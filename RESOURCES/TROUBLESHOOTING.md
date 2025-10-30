# AI Troubleshooting Guide

**Curator: Dr. Ahmed Halloub**

Common issues, errors, and solutions when working with AI tools and APIs.

---

## Table of Contents

- [API Errors](#api-errors)
- [Rate Limiting](#rate-limiting)
- [Context Window Issues](#context-window-issues)
- [Performance Problems](#performance-problems)
- [Integration Issues](#integration-issues)
- [Quality Issues](#quality-issues)
- [Cost Overruns](#cost-overruns)
- [Debugging Strategies](#debugging-strategies)

---

## API Errors

### Error: 401 Unauthorized

**Cause:** Invalid or missing API key

**Solutions:**
```python
# Check environment variable is set
import os
api_key = os.getenv('OPENAI_API_KEY')
if not api_key:
    raise ValueError("API key not found in environment")

# Verify key format
if not api_key.startswith('sk-'):
    raise ValueError("Invalid API key format")

# Test key
from openai import OpenAI
client = OpenAI(api_key=api_key)
try:
    client.models.list()
    print("API key is valid")
except Exception as e:
    print(f"API key error: {e}")
```

**Checklist:**
- [ ] API key in .env file
- [ ] .env file loaded (.env.load())
- [ ] Correct key for environment (dev/prod)
- [ ] Key not expired
- [ ] Billing enabled on account

---

### Error: 429 Rate Limit Exceeded

**Cause:** Too many requests in short time

**Solutions:**

**1. Implement exponential backoff:**
```python
import time
from openai import OpenAI

def call_with_retry(func, max_retries=5):
    for attempt in range(max_retries):
        try:
            return func()
        except Exception as e:
            if 'rate_limit' in str(e).lower():
                wait_time = (2 ** attempt) + random.uniform(0, 1)
                print(f"Rate limited. Waiting {wait_time:.2f}s...")
                time.sleep(wait_time)
            else:
                raise e
    raise Exception("Max retries exceeded")
```

**2. Implement rate limiting:**
```python
from ratelimit import limits, sleep_and_retry

@sleep_and_retry
@limits(calls=10, period=60)  # 10 calls per minute
def call_api(prompt):
    return client.chat.completions.create(
        model="gpt-4",
        messages=[{"role": "user", "content": prompt}]
    )
```

**3. Use request queuing:**
```python
import asyncio
from asyncio import Queue

class RateLimitedQueue:
    def __init__(self, rate_limit=10):
        self.queue = Queue()
        self.rate_limit = rate_limit

    async def process(self):
        while True:
            request = await self.queue.get()
            await self.execute(request)
            await asyncio.sleep(60 / self.rate_limit)
```

---

### Error: 400 Bad Request

**Common Causes & Fixes:**

**Invalid JSON:**
```python
# Bad
messages = str([{"role": "user", "content": "Hello"}])

# Good
messages = [{"role": "user", "content": "Hello"}]
```

**Invalid parameters:**
```python
# Check model name
valid_models = ['gpt-4', 'gpt-3.5-turbo', 'gpt-4-turbo']
if model not in valid_models:
    raise ValueError(f"Invalid model: {model}")

# Validate temperature
if not 0 <= temperature <= 2:
    raise ValueError("Temperature must be between 0 and 2")
```

**Empty messages:**
```python
# Validate before sending
if not messages or all(not m.get('content') for m in messages):
    raise ValueError("Messages cannot be empty")
```

---

### Error: 500 Internal Server Error

**Cause:** Server-side issue

**Solutions:**
```python
def handle_server_error(func, max_retries=3):
    for attempt in range(max_retries):
        try:
            return func()
        except Exception as e:
            if '500' in str(e):
                wait_time = 5 * (attempt + 1)
                print(f"Server error. Retry {attempt + 1}/{max_retries} in {wait_time}s")
                time.sleep(wait_time)
            else:
                raise e
    # Report to provider if persistent
    raise Exception("Persistent server error - contact support")
```

---

## Rate Limiting

### Understanding Limits

**OpenAI Limits (Tier 1):**
```
GPT-4:
  - 10,000 TPM (tokens per minute)
  - 500 RPM (requests per minute)

GPT-3.5-turbo:
  - 90,000 TPM
  - 3,500 RPM
```

**Anthropic Limits:**
```
Claude (default):
  - 40,000 TPM
  - 50 RPM
```

### Monitoring Usage

```python
class UsageMonitor:
    def __init__(self):
        self.requests = []
        self.tokens = []

    def log_request(self, tokens_used):
        now = time.time()
        self.requests.append(now)
        self.tokens.append((now, tokens_used))

        # Clean old entries (> 1 minute)
        cutoff = now - 60
        self.requests = [t for t in self.requests if t > cutoff]
        self.tokens = [(t, n) for t, n in self.tokens if t > cutoff]

    def can_make_request(self, estimated_tokens, rpm_limit, tpm_limit):
        current_rpm = len(self.requests)
        current_tpm = sum(n for t, n in self.tokens)

        return (current_rpm < rpm_limit and
                current_tpm + estimated_tokens < tpm_limit)
```

### Batch to Reduce Requests

```python
# Bad: Multiple API calls
for item in items:
    response = process(item)

# Good: Single batch call
batch_prompt = "\n".join([f"{i+1}. {item}" for i, item in enumerate(items)])
response = process(batch_prompt)
results = parse_batch_response(response)
```

---

## Context Window Issues

### Error: Maximum context length exceeded

**Diagnosis:**
```python
import tiktoken

def count_tokens(text, model="gpt-4"):
    encoding = tiktoken.encoding_for_model(model)
    return len(encoding.encode(text))

def check_context_size(messages, model="gpt-4"):
    limits = {
        "gpt-4": 8192,
        "gpt-4-turbo": 128000,
        "gpt-3.5-turbo": 16385
    }

    total_tokens = sum(count_tokens(str(m)) for m in messages)
    limit = limits.get(model, 4096)

    if total_tokens > limit:
        print(f"Warning: {total_tokens} tokens exceeds {limit} limit")
        return False
    return True
```

**Solutions:**

**1. Truncate intelligently:**
```python
def truncate_messages(messages, max_tokens=4000):
    # Keep system message and recent messages
    system = messages[0] if messages[0]['role'] == 'system' else None
    user_messages = [m for m in messages if m['role'] != 'system']

    result = [system] if system else []
    current_tokens = count_tokens(str(system)) if system else 0

    # Add messages from most recent
    for msg in reversed(user_messages):
        msg_tokens = count_tokens(str(msg))
        if current_tokens + msg_tokens <= max_tokens:
            result.insert(1 if system else 0, msg)
            current_tokens += msg_tokens
        else:
            break

    return result
```

**2. Summarize conversation:**
```python
def summarize_conversation(messages):
    if len(messages) > 10:
        # Get summary of old messages
        old_messages = messages[1:-5]  # Skip system and recent
        summary_prompt = f"Summarize this conversation: {old_messages}"
        summary = get_completion(summary_prompt)

        # Rebuild with summary
        return [
            messages[0],  # System
            {"role": "system", "content": f"Previous context: {summary}"},
            *messages[-5:]  # Recent messages
        ]
    return messages
```

**3. Use longer context models:**
```python
# Switch to larger context window
if tokens_needed > 8000:
    model = "gpt-4-turbo"  # 128K context
elif tokens_needed > 100000:
    model = "claude-3.5-sonnet"  # 200K context
```

---

## Performance Problems

### Slow Response Times

**Diagnosis:**
```python
import time

def benchmark_request():
    start = time.time()

    response = client.chat.completions.create(
        model="gpt-4",
        messages=[{"role": "user", "content": "Hello"}]
    )

    duration = time.time() - start
    print(f"Request took {duration:.2f}s")

    return duration
```

**Solutions:**

**1. Use streaming:**
```python
def stream_response(prompt):
    stream = client.chat.completions.create(
        model="gpt-4",
        messages=[{"role": "user", "content": prompt}],
        stream=True
    )

    for chunk in stream:
        if chunk.choices[0].delta.content:
            print(chunk.choices[0].delta.content, end='')
```

**2. Switch to faster models:**
```python
# Slow
model = "gpt-4"  # ~10-30s response time

# Fast
model = "gpt-3.5-turbo"  # ~2-5s response time
model = "claude-3-haiku"  # ~1-3s response time
```

**3. Reduce output length:**
```python
response = client.chat.completions.create(
    model="gpt-4",
    messages=messages,
    max_tokens=500  # Faster completion
)
```

**4. Use caching:**
```python
from functools import lru_cache

@lru_cache(maxsize=1000)
def cached_completion(prompt, model):
    return client.chat.completions.create(
        model=model,
        messages=[{"role": "user", "content": prompt}]
    )
```

---

## Integration Issues

### Vector Database Connection Errors

**Pinecone:**
```python
import pinecone

# Debug connection
try:
    pinecone.init(
        api_key=os.getenv('PINECONE_API_KEY'),
        environment=os.getenv('PINECONE_ENV')
    )
    print("Connected to Pinecone")
except Exception as e:
    print(f"Connection failed: {e}")
    # Check: API key, environment, network
```

**Common fixes:**
- Verify API key and environment
- Check firewall/network settings
- Ensure index exists
- Verify index dimensions match embeddings

### LangChain Issues

**Module not found:**
```bash
# Install correct packages
pip install langchain langchain-openai langchain-community

# Verify installation
python -c "import langchain; print(langchain.__version__)"
```

**Deprecated imports:**
```python
# Old (deprecated)
from langchain.llms import OpenAI

# New
from langchain_openai import OpenAI
```

**Chain errors:**
```python
# Debug chain
from langchain.globals import set_debug
set_debug(True)

# Run chain to see detailed logs
result = chain.run(input)
```

---

## Quality Issues

### Poor Response Quality

**Diagnosis checklist:**
- [ ] Is the prompt clear and specific?
- [ ] Using appropriate model for task?
- [ ] Temperature setting correct?
- [ ] Enough context provided?
- [ ] Examples included (few-shot)?

**Solutions:**

**1. Improve prompt:**
```python
# Vague
prompt = "Tell me about dogs"

# Specific
prompt = """
Provide a 3-paragraph overview of dog breeds, covering:
1. Classification by size
2. Temperament differences
3. Exercise requirements

Use bullet points for key facts.
"""
```

**2. Adjust temperature:**
```python
# For factual tasks
temperature = 0.1  # More deterministic

# For creative tasks
temperature = 0.7  # More creative
```

**3. Use few-shot examples:**
```python
prompt = """
Classify sentiment as positive, negative, or neutral.

Examples:
Text: "I love this product!"
Sentiment: positive

Text: "Terrible experience"
Sentiment: negative

Text: "The item arrived"
Sentiment: neutral

Text: "{user_text}"
Sentiment:
"""
```

### Inconsistent Outputs

**Solutions:**

**1. Set temperature to 0:**
```python
response = client.chat.completions.create(
    model="gpt-4",
    messages=messages,
    temperature=0  # Deterministic
)
```

**2. Use seed (where supported):**
```python
response = client.chat.completions.create(
    model="gpt-4",
    messages=messages,
    seed=12345  # Reproducible results
)
```

**3. Add structured output:**
```python
prompt = """
Respond in this exact JSON format:
{
  "category": "string",
  "confidence": 0.0-1.0,
  "reasoning": "string"
}
"""
```

---

## Cost Overruns

### Unexpected High Costs

**Diagnosis:**
```python
# Track all requests
def track_cost(func):
    def wrapper(*args, **kwargs):
        start_tokens = get_token_count()
        result = func(*args, **kwargs)
        end_tokens = get_token_count()

        cost = calculate_cost(end_tokens - start_tokens)
        log_cost(cost, func.__name__)

        return result
    return wrapper
```

**Common causes:**
- Infinite loops calling API
- Large context windows
- High-volume production traffic
- Expensive models for simple tasks
- No caching

**Solutions:** See [Cost Optimization Guide](./COST-OPTIMIZATION.md)

---

## Debugging Strategies

### Enable Verbose Logging

```python
import logging

logging.basicConfig(level=logging.DEBUG)
logger = logging.getLogger(__name__)

# Log all requests
def debug_request(prompt, model):
    logger.debug(f"Model: {model}")
    logger.debug(f"Prompt: {prompt[:100]}...")

    try:
        response = call_api(prompt, model)
        logger.debug(f"Response: {str(response)[:100]}...")
        return response
    except Exception as e:
        logger.error(f"Error: {e}", exc_info=True)
        raise
```

### Test in Isolation

```python
# Minimal test case
def test_api_connection():
    try:
        response = client.chat.completions.create(
            model="gpt-3.5-turbo",
            messages=[{"role": "user", "content": "Hi"}],
            max_tokens=10
        )
        print("API working:", response.choices[0].message.content)
    except Exception as e:
        print("API error:", e)

test_api_connection()
```

### Use Postman/curl for API Testing

```bash
# Test OpenAI API directly
curl https://api.openai.com/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $OPENAI_API_KEY" \
  -d '{
    "model": "gpt-3.5-turbo",
    "messages": [{"role": "user", "content": "Hello"}]
  }'
```

---

## Quick Reference

### Error Codes

| Code | Meaning | Action |
|------|---------|--------|
| 401 | Unauthorized | Check API key |
| 429 | Rate limit | Implement backoff |
| 400 | Bad request | Validate inputs |
| 500 | Server error | Retry with backoff |
| 503 | Service unavailable | Wait and retry |

### Debug Checklist

- [ ] API key is valid and loaded
- [ ] Request format is correct
- [ ] Model name is valid
- [ ] Input within token limits
- [ ] Network connection working
- [ ] Rate limits not exceeded
- [ ] Error handling implemented
- [ ] Logging enabled

---

**Still stuck?** Check the official documentation or community forums:
- OpenAI Community Forum
- Anthropic Discord
- Stack Overflow (tag: [openai-api], [langchain])

**Related Resources:**
- [API Integration Guide](./API-INTEGRATION-GUIDE.md)
- [Security Guide](./SECURITY-GUIDE.md)
- [Cost Optimization](./COST-OPTIMIZATION.md)
