# AI APIs and Integrations

**Programmatic access to AI models for building intelligent applications.**

## Major AI API Providers

### 1. Anthropic Claude API

**Models**: Claude 3.5 Sonnet, Claude 3 Opus, Claude 3 Haiku

**Key Features**:
- 200K context window
- Function calling (tool use)
- Vision capabilities
- Streaming responses
- JSON mode
- Safety built-in

**Pricing** (per million tokens):
- Claude 3.5 Sonnet: $3 input / $15 output
- Claude 3 Opus: $15 input / $75 output
- Claude 3 Haiku: $0.25 input / $1.25 output

**Quick Start**:
```python
from anthropic import Anthropic

client = Anthropic(api_key="your_api_key")

message = client.messages.create(
    model="claude-3-5-sonnet-20241022",
    max_tokens=1024,
    messages=[
        {"role": "user", "content": "Hello, Claude!"}
    ]
)

print(message.content[0].text)
```

**Use Cases**:
- Code generation and analysis
- Long document processing
- Complex reasoning tasks
- Content creation

**Documentation**: https://docs.anthropic.com

---

### 2. OpenAI API

**Models**: GPT-4 Turbo, GPT-4, GPT-3.5 Turbo, DALL-E, Whisper, TTS

**Key Features**:
- Function calling
- JSON mode
- Vision (GPT-4V)
- Image generation (DALL-E)
- Speech-to-text (Whisper)
- Text-to-speech
- Embeddings
- Fine-tuning

**Pricing** (per million tokens):
- GPT-4 Turbo: $10 input / $30 output
- GPT-4: $30 input / $60 output
- GPT-3.5 Turbo: $0.50 input / $1.50 output

**Quick Start**:
```python
from openai import OpenAI

client = OpenAI(api_key="your_api_key")

response = client.chat.completions.create(
    model="gpt-4-turbo",
    messages=[
        {"role": "user", "content": "Hello, GPT!"}
    ]
)

print(response.choices[0].message.content)
```

**Use Cases**:
- General chatbots
- Content generation
- Image creation
- Voice applications

**Documentation**: https://platform.openai.com/docs

---

### 3. Google Gemini API

**Models**: Gemini Pro, Gemini Pro Vision, Gemini Ultra

**Key Features**:
- Multimodal (text, image, video, audio)
- Long context (up to 2M tokens)
- Function calling
- Streaming
- Embeddings
- Free tier available

**Pricing**:
- Gemini Pro: Free (rate limited) or pay-as-you-go
- Gemini Pro Vision: $0.002 per image
- Gemini Ultra: Coming soon

**Quick Start**:
```python
import google.generativeai as genai

genai.configure(api_key="your_api_key")

model = genai.GenerativeModel('gemini-pro')
response = model.generate_content("Hello, Gemini!")

print(response.text)
```

**Use Cases**:
- Multimodal analysis
- Long document processing
- Free tier projects
- Google Cloud integration

**Documentation**: https://ai.google.dev

---

### 4. Cohere API

**Models**: Command, Command R, Command R+, Embed, Rerank

**Key Features**:
- Enterprise-focused
- Retrieval-augmented generation (RAG)
- Embeddings optimized for search
- Reranking
- Classification
- Multilingual support

**Pricing**:
- Command: $1 per million tokens
- Embed: $0.10 per million tokens
- Free tier: 100 requests/month

**Quick Start**:
```python
import cohere

co = cohere.Client('your_api_key')

response = co.generate(
    model='command',
    prompt="Write a product description",
    max_tokens=300
)

print(response.generations[0].text)
```

**Use Cases**:
- Enterprise search
- RAG applications
- Document classification
- Semantic search

**Documentation**: https://docs.cohere.com

---

## Specialized APIs

### 5. Stability AI (Stable Diffusion)

**Purpose**: Image generation and editing

**Models**: SDXL, SD 1.5, SD 2.1

**Features**:
- Text-to-image
- Image-to-image
- Inpainting
- Upscaling
- Control over style

**Pricing**: Credit-based, ~$0.002-0.08 per image

**Quick Start**:
```python
import stability_sdk.interfaces.gooseai.generation.generation_pb2 as generation

# Initialize client
stability_api = client.StabilityInference(
    key=os.environ['STABILITY_KEY'],
    engine="stable-diffusion-xl-1024-v1-0",
)

# Generate image
answers = stability_api.generate(
    prompt="A serene landscape with mountains",
    steps=30,
)
```

**Use Cases**:
- Marketing visuals
- Product mockups
- Concept art
- Design assets

---

### 6. ElevenLabs API

**Purpose**: Text-to-speech and voice cloning

**Features**:
- Natural-sounding voices
- Voice cloning
- Multiple languages
- Emotion control
- Streaming audio

**Pricing**: Character-based, starts at $5/mo

**Quick Start**:
```python
from elevenlabs import generate, play

audio = generate(
    text="Hello, this is a generated voice",
    voice="Bella",
    model="eleven_monolingual_v1"
)

play(audio)
```

**Use Cases**:
- Voiceovers
- Accessibility
- Audiobooks
- Voice assistants

---

### 7. Replicate

**Purpose**: Run AI models via API

**Features**:
- 1000s of open-source models
- No infrastructure management
- Pay per use
- Custom model deployment

**Pricing**: Varies by model, ~$0.0001-0.05 per run

**Quick Start**:
```python
import replicate

output = replicate.run(
    "stability-ai/sdxl:latest",
    input={"prompt": "A futuristic cityscape"}
)

print(output)
```

**Use Cases**:
- Experimenting with models
- Prototyping
- Comparing models
- Open-source models

---

### 8. Hugging Face Inference API

**Purpose**: Access to 150K+ models

**Features**:
- Transformers, Diffusers, etc.
- Free tier
- Serverless inference
- Custom model deployment
- AutoTrain

**Pricing**:
- Free: Rate-limited
- Pro ($9/mo): Higher limits
- Enterprise: Custom

**Quick Start**:
```python
from huggingface_hub import InferenceClient

client = InferenceClient(token="your_token")

response = client.text_generation(
    "Write a story about AI",
    model="meta-llama/Llama-2-7b-chat-hf"
)

print(response)
```

**Use Cases**:
- Open-source models
- Fine-tuned models
- Research
- Prototyping

---

## Integration Patterns

### Basic Chat Completion

```python
# Universal pattern for most APIs
def chat_completion(messages, model="gpt-4-turbo"):
    response = client.chat.completions.create(
        model=model,
        messages=messages,
        temperature=0.7,
        max_tokens=1000
    )
    return response.choices[0].message.content
```

### Streaming Responses

```python
# For real-time output
def stream_chat(prompt):
    for chunk in client.chat.completions.create(
        model="gpt-4-turbo",
        messages=[{"role": "user", "content": prompt}],
        stream=True
    ):
        if chunk.choices[0].delta.content:
            yield chunk.choices[0].delta.content
```

### Function Calling / Tool Use

```python
# Anthropic Claude example
tools = [{
    "name": "get_weather",
    "description": "Get weather for a location",
    "input_schema": {
        "type": "object",
        "properties": {
            "location": {"type": "string"}
        },
        "required": ["location"]
    }
}]

response = client.messages.create(
    model="claude-3-5-sonnet-20241022",
    max_tokens=1024,
    tools=tools,
    messages=[{"role": "user", "content": "What's the weather in SF?"}]
)

# Check if tool was called
if response.stop_reason == "tool_use":
    tool_use = next(block for block in response.content if block.type == "tool_use")
    # Execute function and send result back
```

### Embeddings for Semantic Search

```python
# Generate embeddings
from openai import OpenAI
client = OpenAI()

def get_embedding(text):
    response = client.embeddings.create(
        input=text,
        model="text-embedding-3-small"
    )
    return response.data[0].embedding

# Use for similarity search
import numpy as np

def cosine_similarity(a, b):
    return np.dot(a, b) / (np.linalg.norm(a) * np.linalg.norm(b))

query_embedding = get_embedding("search query")
doc_embedding = get_embedding("document text")
similarity = cosine_similarity(query_embedding, doc_embedding)
```

### RAG (Retrieval-Augmented Generation)

```python
# Simple RAG pattern
def rag_query(question, documents):
    # 1. Embed documents and question
    doc_embeddings = [get_embedding(doc) for doc in documents]
    question_embedding = get_embedding(question)

    # 2. Find most relevant documents
    similarities = [
        cosine_similarity(question_embedding, doc_emb)
        for doc_emb in doc_embeddings
    ]
    top_k = np.argsort(similarities)[-3:]  # Top 3

    # 3. Create context from relevant docs
    context = "\n\n".join([documents[i] for i in top_k])

    # 4. Generate answer with context
    prompt = f"Context:\n{context}\n\nQuestion: {question}\nAnswer:"
    return chat_completion([{"role": "user", "content": prompt}])
```

---

## Framework Integrations

### LangChain

```python
from langchain.chat_models import ChatOpenAI
from langchain.prompts import ChatPromptTemplate
from langchain.chains import LLMChain

llm = ChatOpenAI(model="gpt-4-turbo")

prompt = ChatPromptTemplate.from_template(
    "Translate {text} to {language}"
)

chain = LLMChain(llm=llm, prompt=prompt)

result = chain.run(text="Hello", language="Spanish")
```

### LlamaIndex

```python
from llama_index import VectorStoreIndex, SimpleDirectoryReader

# Load documents
documents = SimpleDirectoryReader('data').load_data()

# Create index
index = VectorStoreIndex.from_documents(documents)

# Query
query_engine = index.as_query_engine()
response = query_engine.query("What is the main topic?")
```

### Semantic Kernel

```python
import semantic_kernel as sk

kernel = sk.Kernel()

# Add AI service
kernel.add_text_completion_service(
    "gpt-4",
    OpenAIChatCompletion("gpt-4-turbo", api_key)
)

# Create semantic function
summarize = kernel.create_semantic_function(
    "Summarize: {{$input}}",
    max_tokens=100
)

result = summarize("Long text to summarize...")
```

---

## Best Practices

### Error Handling

```python
from anthropic import Anthropic, APIError, RateLimitError
import time

def safe_api_call(prompt, max_retries=3):
    for attempt in range(max_retries):
        try:
            return client.messages.create(
                model="claude-3-5-sonnet-20241022",
                max_tokens=1024,
                messages=[{"role": "user", "content": prompt}]
            )
        except RateLimitError:
            wait_time = 2 ** attempt  # Exponential backoff
            time.sleep(wait_time)
        except APIError as e:
            print(f"API error: {e}")
            raise

    raise Exception("Max retries exceeded")
```

### Cost Optimization

```python
# 1. Use cheaper models for simple tasks
def choose_model(complexity):
    if complexity == "simple":
        return "gpt-3.5-turbo"  # Cheaper
    elif complexity == "moderate":
        return "gpt-4-turbo"
    else:
        return "gpt-4"  # Most expensive but best

# 2. Limit max tokens
response = client.chat.completions.create(
    model="gpt-4-turbo",
    messages=[...],
    max_tokens=500  # Prevent excessive output
)

# 3. Cache responses
from functools import lru_cache

@lru_cache(maxsize=100)
def cached_completion(prompt):
    return client.chat.completions.create(...)
```

### Token Counting

```python
import tiktoken

def count_tokens(text, model="gpt-4"):
    encoding = tiktoken.encoding_for_model(model)
    return len(encoding.encode(text))

# Estimate cost before calling
def estimate_cost(prompt, max_tokens=1000):
    input_tokens = count_tokens(prompt)
    total_tokens = input_tokens + max_tokens

    # GPT-4 Turbo pricing
    input_cost = input_tokens * 0.01 / 1000
    output_cost = max_tokens * 0.03 / 1000

    return input_cost + output_cost
```

### Rate Limiting

```python
from ratelimit import limits, sleep_and_retry

# 60 requests per minute
@sleep_and_retry
@limits(calls=60, period=60)
def rate_limited_call(prompt):
    return client.chat.completions.create(...)
```

---

## Security Best Practices

### Environment Variables

```python
import os
from dotenv import load_dotenv

load_dotenv()

api_key = os.getenv("ANTHROPIC_API_KEY")
client = Anthropic(api_key=api_key)
```

### Input Sanitization

```python
def sanitize_input(user_input):
    # Remove potential injection attempts
    # Limit length
    # Validate format
    if len(user_input) > 10000:
        raise ValueError("Input too long")

    # Remove special characters if needed
    import re
    clean_input = re.sub(r'[<>]', '', user_input)

    return clean_input
```

### Output Validation

```python
def validate_output(output):
    # Check for sensitive data
    # Verify format
    # Content filtering

    sensitive_patterns = [
        r'\b\d{3}-\d{2}-\d{4}\b',  # SSN
        r'\b\d{16}\b',  # Credit card
    ]

    for pattern in sensitive_patterns:
        if re.search(pattern, output):
            return "Output contains sensitive data"

    return output
```

---

## Monitoring and Logging

```python
import logging
from datetime import datetime

logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

def tracked_api_call(prompt, model):
    start_time = datetime.now()

    try:
        response = client.chat.completions.create(
            model=model,
            messages=[{"role": "user", "content": prompt}]
        )

        duration = (datetime.now() - start_time).total_seconds()

        logger.info({
            "model": model,
            "prompt_length": len(prompt),
            "response_length": len(response.choices[0].message.content),
            "duration": duration,
            "tokens_used": response.usage.total_tokens,
            "timestamp": datetime.now().isoformat()
        })

        return response

    except Exception as e:
        logger.error(f"API call failed: {e}")
        raise
```

---

## Resources

- **Anthropic Docs**: https://docs.anthropic.com
- **OpenAI Docs**: https://platform.openai.com/docs
- **Google AI**: https://ai.google.dev
- **Cohere Docs**: https://docs.cohere.com
- **LangChain**: https://python.langchain.com
- **LlamaIndex**: https://docs.llamaindex.ai

---

**Last Updated**: 2025-10-28

**See Also**:
- [AI Agents](../agents/)
- [CLI Tools](../tools/cli-tools.md)
- [Best Practices](../AI-BEST-PRACTICES.md)
