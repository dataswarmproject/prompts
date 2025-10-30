# AI Cost Optimization Guide

**Curator: Dr. Ahmed Halloub**

Strategies and techniques to optimize AI implementation costs while maintaining quality and performance.

---

## Table of Contents

- [Cost Overview](#cost-overview)
- [Token Optimization](#token-optimization)
- [Model Selection](#model-selection)
- [Caching Strategies](#caching-strategies)
- [Batch Processing](#batch-processing)
- [Infrastructure Optimization](#infrastructure-optimization)
- [Monitoring & Analytics](#monitoring--analytics)
- [ROI Calculation](#roi-calculation)

---

## Cost Overview

### AI Cost Breakdown

| Cost Category | Typical % of Budget | Optimization Potential |
|--------------|-------------------|----------------------|
| API Calls (LLM) | 60-70% | High |
| Vector Database | 10-15% | Medium |
| Infrastructure | 10-15% | Medium |
| Embeddings | 5-10% | High |
| Development Tools | 5-10% | Low |

### Pricing Comparison (Per 1M Tokens)

#### Input Costs

| Model | Input Cost | Use Case |
|-------|-----------|----------|
| GPT-4 Turbo | $10 | Complex reasoning |
| GPT-4o | $2.50 | Balanced performance |
| GPT-3.5 Turbo | $0.50 | Simple tasks |
| Claude 3.5 Sonnet | $3 | Code, analysis |
| Claude 3 Haiku | $0.25 | Fast, simple tasks |
| Gemini 1.5 Pro | $1.25 | Long context |
| Gemini 1.5 Flash | $0.075 | Budget tasks |

#### Output Costs

| Model | Output Cost | Output Quality |
|-------|------------|----------------|
| GPT-4 Turbo | $30 | Excellent |
| GPT-4o | $10 | Excellent |
| GPT-3.5 Turbo | $1.50 | Good |
| Claude 3.5 Sonnet | $15 | Excellent |
| Claude 3 Haiku | $1.25 | Good |
| Gemini 1.5 Pro | $5 | Very good |
| Gemini 1.5 Flash | $0.30 | Good |

---

## Token Optimization

### Understanding Token Usage

**Token Calculation:**
- 1 token ≈ 4 characters
- 1 token ≈ 0.75 words
- Average sentence ≈ 15-20 tokens

**Cost Impact:**
```python
# Example: GPT-4 Turbo
input_tokens = 1000
output_tokens = 500

input_cost = (input_tokens / 1_000_000) * 10  # $0.01
output_cost = (output_tokens / 1_000_000) * 30  # $0.015
total_cost = input_cost + output_cost  # $0.025
```

### Optimization Techniques

#### 1. Prompt Engineering

**Inefficient:**
```python
prompt = """
I would like you to please analyze the following document for me.
The document is about customer feedback and I need you to tell me
what the main themes are. Please be thorough and comprehensive in
your analysis. Here is the document: {document}
"""
# ~40 tokens of unnecessary fluff
```

**Optimized:**
```python
prompt = """
Analyze customer feedback. Identify main themes.

Document: {document}
"""
# ~10 tokens - saves 75%
```

**Savings:** 75% reduction in prompt tokens

#### 2. Context Management

**Track conversation tokens:**
```python
def manage_context(messages: list, max_tokens: int = 4000):
    """Keep only relevant conversation history"""
    token_count = sum(count_tokens(msg) for msg in messages)

    if token_count > max_tokens:
        # Keep system message and recent messages
        system_msg = messages[0]
        recent = messages[-5:]  # Last 5 messages

        # Summarize middle section
        middle = messages[1:-5]
        summary = summarize_conversation(middle)

        messages = [system_msg, summary] + recent

    return messages
```

**Savings:** Up to 60% on long conversations

#### 3. Response Length Control

**Limit output tokens:**
```python
response = openai.chat.completions.create(
    model="gpt-4",
    messages=messages,
    max_tokens=500  # Prevent runaway responses
)
```

**Use concise instructions:**
```python
prompt = """
Summarize in 3 bullet points (max 50 words total).
"""
```

**Savings:** 40-60% on output costs

#### 4. Template Reuse

**Bad:**
```python
for user in users:
    prompt = f"Analyze {user.name}'s behavior: {user.full_profile}"
    # Sends full profile every time
```

**Good:**
```python
# Create embedding once
user_embedding = create_embedding(user.full_profile)

# Use lightweight query
prompt = f"Analyze behavior for user type: {user.segment}"
```

**Savings:** 80% token reduction

---

## Model Selection

### Task-Based Model Selection

| Task Type | Best Model | Cost/Quality Ratio |
|-----------|-----------|-------------------|
| Simple Q&A | GPT-3.5/Haiku | Excellent |
| Code generation | Claude Sonnet | Very good |
| Complex reasoning | GPT-4 | Good |
| Long documents | Gemini Pro | Excellent |
| Classification | GPT-3.5/Flash | Excellent |
| Creative writing | GPT-4/Claude | Good |

### Cascading Model Strategy

**Use cheaper models first:**
```python
def smart_completion(task: str, complexity: str):
    # Try cheap model first
    if complexity == 'simple':
        response = gpt_35_turbo(task)
        if quality_check(response):
            return response

    # Fall back to expensive model
    return gpt_4(task)
```

**Savings:** 50-70% for mixed workloads

### Routing Logic

```python
class ModelRouter:
    def route(self, task: dict):
        # Simple classification
        if self.is_simple_task(task):
            return "gpt-3.5-turbo"

        # Code-related
        if self.is_code_task(task):
            return "claude-3.5-sonnet"

        # Long context
        if task['token_count'] > 100_000:
            return "gemini-1.5-pro"

        # Default
        return "gpt-4-turbo"
```

---

## Caching Strategies

### Prompt Caching

**Claude Prompt Caching:**
```python
response = anthropic.messages.create(
    model="claude-3-5-sonnet-20241022",
    max_tokens=1024,
    system=[
        {
            "type": "text",
            "text": "You are an AI assistant...",
            "cache_control": {"type": "ephemeral"}
        }
    ],
    messages=[{"role": "user", "content": "Hello"}]
)
```

**Savings:** 90% on cached portions

### Response Caching

**Implementation:**
```python
from functools import lru_cache
import hashlib

class ResponseCache:
    def __init__(self):
        self.cache = {}

    def get_cache_key(self, prompt: str, model: str) -> str:
        return hashlib.md5(f"{model}:{prompt}".encode()).hexdigest()

    def get_or_generate(self, prompt: str, model: str):
        key = self.get_cache_key(prompt, model)

        if key in self.cache:
            return self.cache[key], True  # Cache hit

        response = call_api(prompt, model)
        self.cache[key] = response
        return response, False  # Cache miss

cache = ResponseCache()
response, from_cache = cache.get_or_generate(prompt, "gpt-4")
```

**When to cache:**
- Repeated identical queries
- Static content analysis
- Common FAQ responses
- Reference data lookups

**Savings:** Up to 100% on cache hits

### Semantic Caching

**Cache similar queries:**
```python
def semantic_cache_lookup(query: str, threshold: float = 0.95):
    query_embedding = get_embedding(query)

    # Search for similar cached queries
    similar = vector_db.search(query_embedding, top_k=1)

    if similar and similar[0]['score'] > threshold:
        return cached_responses[similar[0]['id']]

    return None
```

**Savings:** 60-80% on similar queries

---

## Batch Processing

### Batch API Usage

**OpenAI Batch API:**
```python
# Instead of real-time processing
batch_input = [
    {"custom_id": "req-1", "method": "POST", "url": "/v1/chat/completions",
     "body": {"model": "gpt-4", "messages": [...]}},
    # ... more requests
]

# Submit batch (50% cost reduction)
batch = client.batches.create(
    input_file_id=file_id,
    endpoint="/v1/chat/completions",
    completion_window="24h"
)
```

**Savings:** 50% discount on batch requests

### Batch Processing Strategy

**Aggregate requests:**
```python
class BatchProcessor:
    def __init__(self, batch_size=100, wait_time=60):
        self.batch = []
        self.batch_size = batch_size

    def add(self, request):
        self.batch.append(request)

        if len(self.batch) >= self.batch_size:
            self.process_batch()

    def process_batch(self):
        # Process all at once
        results = api.batch_process(self.batch)
        self.batch = []
        return results
```

**Savings:** 50% + reduced overhead

---

## Infrastructure Optimization

### Vector Database Costs

**Cost Comparison:**
```
Pinecone (1M vectors): ~$70/month
Qdrant (self-hosted): ~$20/month (VPS)
Chroma (local): $0
```

**Optimization:**
```python
# Reduce dimensionality
from sklearn.decomposition import PCA

pca = PCA(n_components=512)  # From 1536 to 512
reduced_embeddings = pca.fit_transform(embeddings)
```

**Savings:** 67% storage reduction

### Embedding Optimization

**Choose appropriate model:**
```python
# Expensive
embeddings = openai.embeddings.create(
    model="text-embedding-3-large",  # $0.13/1M tokens
    input=texts
)

# Budget
embeddings = openai.embeddings.create(
    model="text-embedding-3-small",  # $0.02/1M tokens
    input=texts
)
```

**Savings:** 85% cost reduction

**Batch embeddings:**
```python
# Bad: One at a time
for text in texts:
    embedding = get_embedding(text)  # 100 API calls

# Good: Batch
embeddings = get_embeddings(texts)  # 1 API call
```

**Savings:** Reduced API overhead

### Self-Hosting Considerations

**When to self-host:**
- High volume (>1M requests/month)
- Sensitive data
- Consistent load
- Technical expertise available

**Cost Analysis:**
```
Cloud API: $5,000/month (1M GPT-4 calls)
Self-hosted (Llama 3 70B):
  - GPU server: $2,000/month
  - Maintenance: $1,000/month
  - Total: $3,000/month
Savings: $2,000/month (40%)
```

---

## Monitoring & Analytics

### Cost Tracking

**Implementation:**
```python
class CostTracker:
    def __init__(self):
        self.costs = {
            'gpt-4': {'input': 10, 'output': 30},
            'gpt-3.5-turbo': {'input': 0.5, 'output': 1.5}
        }

    def track_request(self, model: str, input_tokens: int,
                      output_tokens: int):
        input_cost = (input_tokens / 1_000_000) * self.costs[model]['input']
        output_cost = (output_tokens / 1_000_000) * self.costs[model]['output']

        self.log({
            'model': model,
            'input_tokens': input_tokens,
            'output_tokens': output_tokens,
            'cost': input_cost + output_cost,
            'timestamp': datetime.now()
        })
```

### Cost Alerts

**Set budgets:**
```python
def check_budget():
    daily_cost = get_daily_cost()

    if daily_cost > DAILY_BUDGET * 0.8:
        send_alert("Approaching daily budget")

    if daily_cost > DAILY_BUDGET:
        send_alert("Budget exceeded!")
        # Optionally: switch to cheaper models
        enable_budget_mode()
```

### Usage Analytics

**Track metrics:**
```python
metrics = {
    'cost_per_user': total_cost / active_users,
    'cost_per_request': total_cost / request_count,
    'average_tokens_per_request': total_tokens / request_count,
    'model_distribution': model_usage_percentages,
    'cache_hit_rate': cache_hits / total_requests
}
```

---

## ROI Calculation

### Cost-Benefit Analysis

**Calculate time savings:**
```python
def calculate_roi(ai_cost: float, hours_saved: float,
                  hourly_rate: float):
    time_value = hours_saved * hourly_rate
    roi = ((time_value - ai_cost) / ai_cost) * 100
    return roi

# Example
monthly_ai_cost = 500
hours_saved = 80  # Per month
hourly_rate = 50

roi = calculate_roi(monthly_ai_cost, hours_saved, hourly_rate)
# ROI: 700% (save $4,000, spend $500)
```

### Optimization Checklist

**Quick Wins:**
- [ ] Switch simple tasks to GPT-3.5/Haiku
- [ ] Implement response caching
- [ ] Optimize prompts (remove fluff)
- [ ] Set max_tokens limits
- [ ] Use batch API where possible

**Medium Effort:**
- [ ] Implement model routing
- [ ] Add semantic caching
- [ ] Optimize embeddings
- [ ] Context window management
- [ ] Monitor and alert on costs

**Long Term:**
- [ ] Consider self-hosting
- [ ] Fine-tune smaller models
- [ ] Build evaluation pipeline
- [ ] Implement A/B testing
- [ ] Continuous optimization

---

## Cost Optimization Strategies by Scale

### Startup (<$500/month)

**Priorities:**
1. Use free tiers (Gemini Flash, GPT-3.5)
2. Aggressive caching
3. Minimal infrastructure (Chroma local)
4. Manual optimization

**Expected Savings:** 60-70%

### Small Business ($500-$5K/month)

**Priorities:**
1. Model routing (cheap → expensive)
2. Prompt caching
3. Managed vector DB (Pinecone starter)
4. Automated monitoring

**Expected Savings:** 40-50%

### Enterprise (>$5K/month)

**Priorities:**
1. Fine-tuned models
2. Self-hosted solutions
3. Advanced caching strategies
4. Dedicated optimization team

**Expected Savings:** 30-40%

---

## Real-World Examples

### Example 1: Customer Support Bot

**Before Optimization:**
```
Model: GPT-4
Average conversation: 20 messages
Tokens per conversation: 4,000
Cost per conversation: $0.20
Monthly conversations: 10,000
Monthly cost: $2,000
```

**After Optimization:**
```
Model routing: GPT-3.5 (80%) + GPT-4 (20%)
Prompt optimization: -40% tokens
Response caching: 30% cache hit rate
Cost per conversation: $0.06
Monthly cost: $600
Savings: $1,400/month (70%)
```

### Example 2: Document Analysis

**Before:**
```
Model: GPT-4
Documents per day: 500
Tokens per document: 8,000
Cost per document: $0.32
Monthly cost: $4,800
```

**After:**
```
Model: Gemini 1.5 Pro (long context)
Batch processing: 50% discount
Prompt optimization: -30% tokens
Cost per document: $0.08
Monthly cost: $1,200
Savings: $3,600/month (75%)
```

---

## Tools & Resources

### Cost Calculation Tools
- OpenAI Tokenizer
- Anthropic Token Counter
- AI Cost Calculator (custom tools)

### Monitoring Platforms
- OpenAI Usage Dashboard
- LangSmith (LangChain)
- Helicone
- Custom analytics

---

**Key Takeaway:** With proper optimization, you can reduce AI costs by 50-70% without sacrificing quality. Start with quick wins and gradually implement advanced strategies.

**Related Resources:**
- [Comparison Guide](./COMPARISON-GUIDES.md)
- [API Integration Guide](./API-INTEGRATION-GUIDE.md)
- [Benchmarks](./BENCHMARKS.md)
