<div dir="rtl">

# دليل التكامل الشامل مع واجهات برمجة التطبيقات (2025)

**من إعداد: د. أحمد حلوب**

> يغطي هذا الدليل الشامل أمثلة على التكامل مع واجهات برمجة التطبيقات وأفضل الممارسات لمقدمي الخدمات الرئيسيين للذكاء الاصطناعي بما في ذلك OpenAI و Anthropic Claude و Google Gemini وغيرهم. يتضمن أمثلة برمجية وأنماطاً وتطبيقات جاهزة للإنتاج. آخر تحديث: أكتوبر 2025

---

## جدول المحتويات

</div>

1. [Overview](#overview)
2. [OpenAI API](#openai-api)
3. [Anthropic Claude API](#anthropic-claude-api)
4. [Google Gemini API](#google-gemini-api)
5. [Integration Patterns](#integration-patterns)
6. [Best Practices](#best-practices)
7. [Security](#security)
8. [Performance Optimization](#performance-optimization)
9. [Error Handling](#error-handling)
10. [Cost Management](#cost-management)

<div dir="rtl">

---

## نظرة عامة

### مقدمو خدمات الذكاء الاصطناعي الرئيسيون (2025)

</div>

| Provider | Models | Strengths | Pricing (per 1M tokens) |
|----------|--------|-----------|-------------------------|
| **OpenAI** | GPT-4, GPT-4 Turbo, GPT-3.5 | Creative content, math, general knowledge | $3-$15 input / $10-$60 output |
| **Anthropic** | Claude 4 Opus/Sonnet, Claude 3.5 Haiku | Large documents, ethical alignment, cost-effective | $0.25-$15 input / $1.25-$75 output |
| **Google** | Gemini Ultra/Pro/Flash | Multimodal, Google integration | $0.125-$7 input / $0.375-$21 output |
| **Meta** | Llama 4 | Open source, customizable | Free (self-hosted) |
| **Mistral** | Mistral Large 2, Mixtral | European option, performance | €2-€8 per 1M tokens |

<div dir="rtl">

### متى تختار أي واجهة برمجية

**OpenAI** (GPT-4/GPT-3.5):
- ✅ إنشاء المحتوى الإبداعي
- ✅ الرياضيات المتقدمة
- ✅ توليد الأكواد
- ❌ مكلف للسياقات الكبيرة
- ❌ نوافذ سياق أقصر

**Anthropic Claude**:
- ✅ معالجة الوثائق الكبيرة (200K+ رمز)
- ✅ التوافق الأخلاقي والسلامة
- ✅ فعال من حيث التكلفة للمدخلات الكبيرة
- ✅ أفضل نموذج للبرمجة (Claude Sonnet 4.5)
- ❌ أقل إبداعاً من GPT-4

**Google Gemini**:
- ✅ المهام متعددة الوسائط (نص، صورة، صوت، فيديو)
- ✅ تكامل مع Google Workspace
- ✅ استنتاج سريع
- ❌ نظام بيئي أحدث

---

## OpenAI API

### الإعداد

</div>

```bash
pip install openai
```

```python
import openai

openai.api_key = "your-api-key-here"
```

<div dir="rtl">

### إكمال المحادثات

#### مثال أساسي

</div>

```python
from openai import OpenAI

client = OpenAI(api_key="your-api-key")

response = client.chat.completions.create(
    model="gpt-4",
    messages=[
        {"role": "system", "content": "You are a helpful assistant."},
        {"role": "user", "content": "Explain quantum computing in simple terms."}
    ],
    temperature=0.7,
    max_tokens=500
)

print(response.choices[0].message.content)
```

<div dir="rtl">

#### الاستجابة المتدفقة

</div>

```python
stream = client.chat.completions.create(
    model="gpt-4",
    messages=[{"role": "user", "content": "Write a story"}],
    stream=True
)

for chunk in stream:
    if chunk.choices[0].delta.content is not None:
        print(chunk.choices[0].delta.content, end="")
```

<div dir="rtl">

### استدعاء الوظائف

</div>

```python
tools = [
    {
        "type": "function",
        "function": {
            "name": "get_weather",
            "description": "Get the current weather for a location",
            "parameters": {
                "type": "object",
                "properties": {
                    "location": {
                        "type": "string",
                        "description": "City and state, e.g. San Francisco, CA"
                    },
                    "unit": {
                        "type": "string",
                        "enum": ["celsius", "fahrenheit"]
                    }
                },
                "required": ["location"]
            }
        }
    }
]

response = client.chat.completions.create(
    model="gpt-4",
    messages=[{"role": "user", "content": "What's the weather in Boston?"}],
    tools=tools,
    tool_choice="auto"
)

# Check if the model wants to call a function
if response.choices[0].message.tool_calls:
    tool_call = response.choices[0].message.tool_calls[0]
    function_name = tool_call.function.name
    arguments = json.loads(tool_call.function.arguments)

    # Call your function
    result = get_weather(**arguments)

    # Send result back to model
    second_response = client.chat.completions.create(
        model="gpt-4",
        messages=[
            {"role": "user", "content": "What's the weather in Boston?"},
            response.choices[0].message,
            {
                "role": "tool",
                "tool_call_id": tool_call.id,
                "content": json.dumps(result)
            }
        ]
    )
```

<div dir="rtl">

### التضمينات

</div>

```python
def get_embedding(text, model="text-embedding-ada-002"):
    response = client.embeddings.create(
        input=text,
        model=model
    )
    return response.data[0].embedding

# Example usage
embedding = get_embedding("Hello, world!")
print(f"Embedding dimension: {len(embedding)}")
```

<div dir="rtl">

### الرؤية (GPT-4V)

</div>

```python
response = client.chat.completions.create(
    model="gpt-4-vision-preview",
    messages=[
        {
            "role": "user",
            "content": [
                {"type": "text", "text": "What's in this image?"},
                {
                    "type": "image_url",
                    "image_url": {
                        "url": "https://example.com/image.jpg"
                    }
                }
            ]
        }
    ],
    max_tokens=300
)
```

<div dir="rtl">

### DALL-E 3 (توليد الصور)

</div>

```python
response = client.images.generate(
    model="dall-e-3",
    prompt="A futuristic cityscape at sunset",
    size="1024x1024",
    quality="standard",
    n=1
)

image_url = response.data[0].url
print(f"Generated image: {image_url}")
```

<div dir="rtl">

---

## Anthropic Claude API

### الإعداد

</div>

```bash
pip install anthropic
```

```python
import anthropic

client = anthropic.Anthropic(api_key="your-api-key")
```

<div dir="rtl">

### رسالة أساسية

</div>

```python
message = client.messages.create(
    model="claude-sonnet-4-5",
    max_tokens=1024,
    messages=[
        {"role": "user", "content": "Hello, Claude!"}
    ]
)

print(message.content[0].text)
```

<div dir="rtl">

### موجهات النظام

</div>

```python
message = client.messages.create(
    model="claude-sonnet-4-5",
    max_tokens=1024,
    system="You are a helpful AI assistant specialized in Python programming.",
    messages=[
        {"role": "user", "content": "Write a function to calculate fibonacci numbers"}
    ]
)
```

<div dir="rtl">

### البث المباشر

</div>

```python
with client.messages.stream(
    model="claude-sonnet-4-5",
    max_tokens=1024,
    messages=[{"role": "user", "content": "Write a short story"}]
) as stream:
    for text in stream.text_stream:
        print(text, end="", flush=True)
```

<div dir="rtl">

### استخدام الأدوات

</div>

```python
tools = [
    {
        "name": "get_weather",
        "description": "Get the current weather in a given location",
        "input_schema": {
            "type": "object",
            "properties": {
                "location": {
                    "type": "string",
                    "description": "City and state, e.g. San Francisco, CA"
                }
            },
            "required": ["location"]
        }
    }
]

message = client.messages.create(
    model="claude-sonnet-4-5",
    max_tokens=1024,
    tools=tools,
    messages=[{"role": "user", "content": "What's the weather in Paris?"}]
)

# Check for tool use
if message.stop_reason == "tool_use":
    tool_use = next(block for block in message.content if block.type == "tool_use")
    tool_name = tool_use.name
    tool_input = tool_use.input

    # Execute the tool
    result = get_weather(**tool_input)

    # Continue conversation with tool result
    response = client.messages.create(
        model="claude-sonnet-4-5",
        max_tokens=1024,
        tools=tools,
        messages=[
            {"role": "user", "content": "What's the weather in Paris?"},
            {"role": "assistant", "content": message.content},
            {
                "role": "user",
                "content": [
                    {
                        "type": "tool_result",
                        "tool_use_id": tool_use.id,
                        "content": json.dumps(result)
                    }
                ]
            }
        ]
    )
```

<div dir="rtl">

### الرؤية (تحليل الصور)

</div>

```python
import base64

def encode_image(image_path):
    with open(image_path, "rb") as image_file:
        return base64.b64encode(image_file.read()).decode('utf-8')

message = client.messages.create(
    model="claude-sonnet-4-5",
    max_tokens=1024,
    messages=[
        {
            "role": "user",
            "content": [
                {
                    "type": "image",
                    "source": {
                        "type": "base64",
                        "media_type": "image/jpeg",
                        "data": encode_image("path/to/image.jpg")
                    }
                },
                {
                    "type": "text",
                    "text": "Describe this image in detail."
                }
            ]
        }
    ]
)
```

<div dir="rtl">

### التخزين المؤقت للموجهات (تحسين التكلفة)

</div>

```python
# Use prompt caching for repeated context
message = client.messages.create(
    model="claude-sonnet-4-5",
    max_tokens=1024,
    system=[
        {
            "type": "text",
            "text": "You are an AI assistant with extensive knowledge of...",
            "cache_control": {"type": "ephemeral"}  # Cache this system prompt
        }
    ],
    messages=[{"role": "user", "content": "Question about the context"}]
)
```

<div dir="rtl">

### معالجة ملفات PDF

</div>

```python
import PyPDF2

def extract_text_from_pdf(pdf_path):
    with open(pdf_path, 'rb') as file:
        reader = PyPDF2.PdfReader(file)
        text = ""
        for page in reader.pages:
            text += page.extract_text()
    return text

pdf_text = extract_text_from_pdf("document.pdf")

message = client.messages.create(
    model="claude-opus-4",  # Use Opus for large documents
    max_tokens=4096,
    messages=[
        {
            "role": "user",
            "content": f"Analyze this document and provide key insights:\n\n{pdf_text}"
        }
    ]
)
```

<div dir="rtl">

---

## Google Gemini API

### الإعداد

</div>

```bash
pip install google-generativeai
```

```python
import google.generativeai as genai

genai.configure(api_key="your-api-key")
```

<div dir="rtl">

### توليد النصوص

</div>

```python
model = genai.GenerativeModel('gemini-pro')

response = model.generate_content("Explain how AI works")
print(response.text)
```

<div dir="rtl">

### المحادثة

</div>

```python
model = genai.GenerativeModel('gemini-pro')
chat = model.start_chat(history=[])

response = chat.send_message("Hello!")
print(response.text)

response = chat.send_message("What did I just say?")
print(response.text)
```

<div dir="rtl">

### متعدد الوسائط (Gemini Vision)

</div>

```python
import PIL.Image

model = genai.GenerativeModel('gemini-pro-vision')

image = PIL.Image.open('image.jpg')
response = model.generate_content([
    "What's in this image?",
    image
])
print(response.text)
```

<div dir="rtl">

---

## أنماط التكامل

### 1. إعادة المحاولة مع التراجع الأسي

</div>

```python
import time
from functools import wraps

def retry_with_exponential_backoff(
    func,
    initial_delay: float = 1,
    exponential_base: float = 2,
    max_retries: int = 5
):
    @wraps(func)
    def wrapper(*args, **kwargs):
        delay = initial_delay
        for i in range(max_retries):
            try:
                return func(*args, **kwargs)
            except Exception as e:
                if i == max_retries - 1:
                    raise
                time.sleep(delay)
                delay *= exponential_base
        return None
    return wrapper

@retry_with_exponential_backoff
def call_api():
    return client.chat.completions.create(...)
```

<div dir="rtl">

### 2. تحديد المعدل

</div>

```python
from ratelimit import limits, sleep_and_retry

# 50 calls per minute
@sleep_and_retry
@limits(calls=50, period=60)
def call_api_with_rate_limit():
    return client.chat.completions.create(...)
```

<div dir="rtl">

### 3. المعالجة الدفعية

</div>

```python
async def process_batch(prompts, batch_size=10):
    results = []
    for i in range(0, len(prompts), batch_size):
        batch = prompts[i:i + batch_size]
        batch_results = await asyncio.gather(*[
            call_api_async(prompt) for prompt in batch
        ])
        results.extend(batch_results)
    return results
```

<div dir="rtl">

### 4. التخزين المؤقت للاستجابات

</div>

```python
import hashlib
import json
from functools import lru_cache

def cache_key(messages):
    return hashlib.md5(
        json.dumps(messages, sort_keys=True).encode()
    ).hexdigest()

response_cache = {}

def get_cached_response(messages):
    key = cache_key(messages)
    if key in response_cache:
        return response_cache[key]

    response = client.chat.completions.create(
        model="gpt-4",
        messages=messages
    )
    response_cache[key] = response
    return response
```

<div dir="rtl">

### 5. استراتيجية الاحتياط

</div>

```python
def call_with_fallback(prompt):
    providers = [
        ("openai", "gpt-4", openai_client),
        ("anthropic", "claude-sonnet-4-5", anthropic_client),
        ("google", "gemini-pro", gemini_client)
    ]

    for provider, model, client in providers:
        try:
            response = client.chat.completions.create(
                model=model,
                messages=[{"role": "user", "content": prompt}]
            )
            return response
        except Exception as e:
            print(f"{provider} failed: {e}")
            continue

    raise Exception("All providers failed")
```

<div dir="rtl">

---

## أفضل الممارسات

### 1. هندسة الموجهات

#### استخدام تعليمات واضحة

</div>

```python
# ❌ سيء
"Write about AI"

# ✅ جيد
"Write a 500-word article explaining AI for beginners. Include:
1. Definition of AI
2. Real-world applications
3. Future implications
Use simple language and provide examples."
```

<div dir="rtl">

#### تقديم السياق

</div>

```python
system_prompt = """
You are an expert Python developer with 10 years of experience.
You specialize in writing clean, efficient, and well-documented code.
Always follow PEP 8 style guidelines.
"""
```

<div dir="rtl">

### 2. إدارة الرموز

</div>

```python
def count_tokens(text, model="gpt-4"):
    encoding = tiktoken.encoding_for_model(model)
    return len(encoding.encode(text))

def truncate_to_token_limit(text, max_tokens=4000, model="gpt-4"):
    encoding = tiktoken.encoding_for_model(model)
    tokens = encoding.encode(text)
    if len(tokens) <= max_tokens:
        return text
    return encoding.decode(tokens[:max_tokens])
```

<div dir="rtl">

### 3. المخرجات المنظمة

</div>

```python
from pydantic import BaseModel

class MovieReview(BaseModel):
    title: str
    rating: float
    summary: str
    pros: list[str]
    cons: list[str]

response = client.chat.completions.create(
    model="gpt-4",
    messages=[
        {"role": "system", "content": "Extract movie review information."},
        {"role": "user", "content": review_text}
    ],
    functions=[{
        "name": "extract_review",
        "parameters": MovieReview.schema()
    }],
    function_call={"name": "extract_review"}
)

review = MovieReview.parse_raw(
    response.choices[0].message.function_call.arguments
)
```

<div dir="rtl">

---

## الأمان

### 1. إدارة مفاتيح API

</div>

```python
import os
from dotenv import load_dotenv

load_dotenv()

# ✅ جيد: استخدام متغيرات البيئة
api_key = os.getenv("OPENAI_API_KEY")

# ❌ سيء: تضمين مفاتيح API مباشرة
api_key = "sk-..."  # Never do this!
```

<div dir="rtl">

### 2. التحقق من المدخلات

</div>

```python
def validate_input(user_input):
    # Check length
    if len(user_input) > 10000:
        raise ValueError("Input too long")

    # Check for sensitive data
    sensitive_patterns = [r'\b\d{3}-\d{2}-\d{4}\b']  # SSN pattern
    for pattern in sensitive_patterns:
        if re.search(pattern, user_input):
            raise ValueError("Sensitive data detected")

    return user_input
```

<div dir="rtl">

### 3. تصفية المحتوى

</div>

```python
from openai import OpenAI

def check_content_safety(text):
    response = client.moderations.create(input=text)
    if response.results[0].flagged:
        return False, response.results[0].categories
    return True, None

# Before processing
is_safe, violations = check_content_safety(user_input)
if not is_safe:
    print(f"Content violates policies: {violations}")
```

<div dir="rtl">

---

## تحسين الأداء

### 1. استخدام البث للاستجابات الطويلة

</div>

```python
def stream_response(prompt):
    stream = client.chat.completions.create(
        model="gpt-4",
        messages=[{"role": "user", "content": prompt}],
        stream=True
    )

    for chunk in stream:
        if chunk.choices[0].delta.content:
            yield chunk.choices[0].delta.content
```

<div dir="rtl">

### 2. الطلبات المتوازية

</div>

```python
import asyncio
from anthropic import AsyncAnthropic

client = AsyncAnthropic(api_key="your-key")

async def process_multiple_prompts(prompts):
    tasks = [
        client.messages.create(
            model="claude-sonnet-4-5",
            max_tokens=1024,
            messages=[{"role": "user", "content": prompt}]
        )
        for prompt in prompts
    ]
    return await asyncio.gather(*tasks)

# Usage
prompts = ["Prompt 1", "Prompt 2", "Prompt 3"]
results = asyncio.run(process_multiple_prompts(prompts))
```

<div dir="rtl">

### 3. اختيار النموذج

</div>

```python
def choose_model(task_complexity, budget="medium"):
    if task_complexity == "simple" and budget == "low":
        return "gpt-3.5-turbo"  # Fast, cheap
    elif task_complexity == "medium":
        return "claude-sonnet-4-5"  # Balanced
    else:
        return "gpt-4"  # Best quality
```

<div dir="rtl">

---

## معالجة الأخطاء

</div>

```python
from openai import OpenAI, APIError, RateLimitError, APIConnectionError

client = OpenAI(api_key="your-key")

def robust_api_call(prompt, max_retries=3):
    for attempt in range(max_retries):
        try:
            response = client.chat.completions.create(
                model="gpt-4",
                messages=[{"role": "user", "content": prompt}]
            )
            return response.choices[0].message.content

        except RateLimitError:
            wait_time = 2 ** attempt
            print(f"Rate limit hit. Waiting {wait_time}s...")
            time.sleep(wait_time)

        except APIConnectionError:
            print("Connection error. Retrying...")
            time.sleep(1)

        except APIError as e:
            print(f"API error: {e}")
            if attempt == max_retries - 1:
                raise

        except Exception as e:
            print(f"Unexpected error: {e}")
            raise

    raise Exception("Max retries exceeded")
```

<div dir="rtl">

---

## إدارة التكلفة

### تتبع الاستخدام

</div>

```python
class UsageTracker:
    def __init__(self):
        self.total_tokens = 0
        self.total_cost = 0
        self.requests = []

    def log_request(self, response, model="gpt-4"):
        usage = response.usage
        input_tokens = usage.prompt_tokens
        output_tokens = usage.completion_tokens

        # Pricing (example for GPT-4)
        cost = (input_tokens * 0.03 / 1000) + (output_tokens * 0.06 / 1000)

        self.total_tokens += input_tokens + output_tokens
        self.total_cost += cost
        self.requests.append({
            "timestamp": time.time(),
            "model": model,
            "tokens": input_tokens + output_tokens,
            "cost": cost
        })

    def get_stats(self):
        return {
            "total_requests": len(self.requests),
            "total_tokens": self.total_tokens,
            "total_cost": f"${self.total_cost:.4f}"
        }

tracker = UsageTracker()
response = client.chat.completions.create(...)
tracker.log_request(response)
```

<div dir="rtl">

---

## الموارد

### الوثائق الرسمية
- **OpenAI Cookbook**: https://cookbook.openai.com
- **Anthropic Claude Cookbook**: https://github.com/anthropics/anthropic-cookbook
- **Google Gemini Docs**: https://ai.google.dev/docs

### المجتمع
- **OpenAI Community**: https://community.openai.com
- **Anthropic Discord**: https://anthropic.com/discord
- **Reddit r/MachineLearning**: مناقشات تعلم الآلة

---

## الموارد ذات الصلة

- [دليل أدوات الذكاء الاصطناعي](../tools/ai-tools-directory.md)
- [مكتبة الموجهات](../prompts/MASTER-PROMPTS-LIBRARY.md)
- [خوادم MCP](../tools/mcp-servers-directory.md)
- [وكلاء الذكاء الاصطناعي](../agents/ai-agents-frameworks.md)

---

**آخر تحديث**: 30 أكتوبر 2025

**صيانة بواسطة**: د. أحمد حلوب | [ahmedhalloub.com](https://ahmedhalloub.com)

</div>
