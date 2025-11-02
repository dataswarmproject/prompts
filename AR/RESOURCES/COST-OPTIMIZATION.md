<div dir="rtl">

# دليل تحسين تكلفة الذكاء الاصطناعي

**القيّم: د. أحمد حلوب**

استراتيجيات وتقنيات لتحسين تكاليف تطبيق الذكاء الاصطناعي مع الحفاظ على الجودة والأداء.

---

## جدول المحتويات

</div>

- [Cost Overview](#cost-overview)
- [Token Optimization](#token-optimization)
- [Model Selection](#model-selection)
- [Caching Strategies](#caching-strategies)
- [Batch Processing](#batch-processing)
- [Infrastructure Optimization](#infrastructure-optimization)
- [Monitoring & Analytics](#monitoring--analytics)
- [ROI Calculation](#roi-calculation)

<div dir="rtl">

---

## نظرة عامة على التكاليف

### تفصيل تكاليف الذكاء الاصطناعي

</div>

| Cost Category | Typical % of Budget | Optimization Potential |
|--------------|-------------------|----------------------|
| API Calls (LLM) | 60-70% | High |
| Vector Database | 10-15% | Medium |
| Infrastructure | 10-15% | Medium |
| Embeddings | 5-10% | High |
| Development Tools | 5-10% | Low |

<div dir="rtl">

### مقارنة الأسعار (لكل مليون رمز)

#### تكاليف المدخلات

</div>

| Model | Input Cost | Use Case |
|-------|-----------|----------|
| GPT-4 Turbo | $10 | Complex reasoning |
| GPT-4o | $2.50 | Balanced performance |
| GPT-3.5 Turbo | $0.50 | Simple tasks |
| Claude 3.5 Sonnet | $3 | Code, analysis |
| Claude 3 Haiku | $0.25 | Fast, simple tasks |
| Gemini 1.5 Pro | $1.25 | Long context |
| Gemini 1.5 Flash | $0.075 | Budget tasks |

<div dir="rtl">

#### تكاليف المخرجات

</div>

| Model | Output Cost | Output Quality |
|-------|------------|----------------|
| GPT-4 Turbo | $30 | Excellent |
| GPT-4o | $10 | Excellent |
| GPT-3.5 Turbo | $1.50 | Good |
| Claude 3.5 Sonnet | $15 | Excellent |
| Claude 3 Haiku | $1.25 | Good |
| Gemini 1.5 Pro | $5 | Very good |
| Gemini 1.5 Flash | $0.30 | Good |

<div dir="rtl">

---

## تحسين الرموز

### فهم استخدام الرموز

**حساب الرموز:**
- رمز واحد ≈ 4 أحرف
- رمز واحد ≈ 0.75 كلمة
- جملة متوسطة ≈ 15-20 رمز

**تأثير التكلفة:**

</div>

```python
# مثال: GPT-4 Turbo
input_tokens = 1000
output_tokens = 500

input_cost = (input_tokens / 1_000_000) * 10  # $0.01
output_cost = (output_tokens / 1_000_000) * 30  # $0.015
total_cost = input_cost + output_cost  # $0.025
```

<div dir="rtl">

### تقنيات التحسين

#### 1. هندسة الموجهات

**غير فعال:**

</div>

```python
prompt = """
I would like you to please analyze the following document for me.
The document is about customer feedback and I need you to tell me
what the main themes are. Please be thorough and comprehensive in
your analysis. Here is the document: {document}
"""
# ~40 رمز من الحشو غير الضروري
```

<div dir="rtl">

**محسّن:**

</div>

```python
prompt = """
Analyze customer feedback. Identify main themes.

Document: {document}
"""
# ~10 رموز - توفير 75%
```

<div dir="rtl">

**التوفير:** تقليل 75% في رموز الموجهات

#### 2. إدارة السياق

**تتبع رموز المحادثة:**

</div>

```python
def manage_context(messages: list, max_tokens: int = 4000):
    """الاحتفاظ فقط بسجل المحادثة ذي الصلة"""
    token_count = sum(count_tokens(msg) for msg in messages)

    if token_count > max_tokens:
        # الاحتفاظ برسالة النظام والرسائل الأخيرة
        system_msg = messages[0]
        recent = messages[-5:]  # آخر 5 رسائل

        # تلخيص القسم الأوسط
        middle = messages[1:-5]
        summary = summarize_conversation(middle)

        messages = [system_msg, summary] + recent

    return messages
```

<div dir="rtl">

**التوفير:** حتى 60% على المحادثات الطويلة

#### 3. التحكم في طول الاستجابة

**تحديد رموز المخرجات:**

</div>

```python
response = openai.chat.completions.create(
    model="gpt-4",
    messages=messages,
    max_tokens=500  # منع الاستجابات المفرطة
)
```

<div dir="rtl">

**استخدام تعليمات موجزة:**

</div>

```python
prompt = """
لخص في 3 نقاط (بحد أقصى 50 كلمة إجمالاً).
"""
```

<div dir="rtl">

**التوفير:** 40-60% على تكاليف المخرجات

#### 4. إعادة استخدام القوالب

**سيء:**

</div>

```python
for user in users:
    prompt = f"Analyze {user.name}'s behavior: {user.full_profile}"
    # إرسال الملف الشخصي الكامل في كل مرة
```

<div dir="rtl">

**جيد:**

</div>

```python
# إنشاء التضمين مرة واحدة
user_embedding = create_embedding(user.full_profile)

# استخدام استعلام خفيف
prompt = f"Analyze behavior for user type: {user.segment}"
```

<div dir="rtl">

**التوفير:** تقليل الرموز بنسبة 80%

---

## اختيار النموذج

### اختيار النموذج بناءً على المهمة

</div>

| Task Type | Best Model | Cost/Quality Ratio |
|-----------|-----------|-------------------|
| Simple Q&A | GPT-3.5/Haiku | Excellent |
| Code generation | Claude Sonnet | Very good |
| Complex reasoning | GPT-4 | Good |
| Long documents | Gemini Pro | Excellent |
| Classification | GPT-3.5/Flash | Excellent |
| Creative writing | GPT-4/Claude | Good |

<div dir="rtl">

### استراتيجية النماذج المتتالية

**استخدام نماذج أرخص أولاً:**

</div>

```python
def smart_completion(task: str, complexity: str):
    # جرب النموذج الرخيص أولاً
    if complexity == 'simple':
        response = gpt_35_turbo(task)
        if quality_check(response):
            return response

    # الرجوع إلى النموذج الأغلى
    return gpt_4(task)
```

<div dir="rtl">

**التوفير:** 50-70% لأعباء العمل المختلطة

### منطق التوجيه

</div>

```python
class ModelRouter:
    def route(self, task: dict):
        # تصنيف بسيط
        if self.is_simple_task(task):
            return "gpt-3.5-turbo"

        # متعلق بالكود
        if self.is_code_task(task):
            return "claude-3.5-sonnet"

        # سياق طويل
        if task['token_count'] > 100_000:
            return "gemini-1.5-pro"

        # افتراضي
        return "gpt-4-turbo"
```

<div dir="rtl">

---

## استراتيجيات التخزين المؤقت

### التخزين المؤقت للموجهات

**التخزين المؤقت لموجهات Claude:**

</div>

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

<div dir="rtl">

**التوفير:** 90% على الأجزاء المخزنة مؤقتاً

### التخزين المؤقت للاستجابات

**التنفيذ:**

</div>

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
            return self.cache[key], True  # إصابة التخزين المؤقت

        response = call_api(prompt, model)
        self.cache[key] = response
        return response, False  # إخفاق التخزين المؤقت

cache = ResponseCache()
response, from_cache = cache.get_or_generate(prompt, "gpt-4")
```

<div dir="rtl">

**متى يتم التخزين المؤقت:**
- الاستعلامات المتطابقة المتكررة
- تحليل المحتوى الثابت
- استجابات الأسئلة الشائعة
- البحث عن البيانات المرجعية

**التوفير:** حتى 100% عند إصابات التخزين المؤقت

### التخزين المؤقت الدلالي

**التخزين المؤقت للاستعلامات المشابهة:**

</div>

```python
def semantic_cache_lookup(query: str, threshold: float = 0.95):
    query_embedding = get_embedding(query)

    # البحث عن استعلامات مشابهة مخزنة مؤقتاً
    similar = vector_db.search(query_embedding, top_k=1)

    if similar and similar[0]['score'] > threshold:
        return cached_responses[similar[0]['id']]

    return None
```

<div dir="rtl">

**التوفير:** 60-80% على الاستعلامات المشابهة

---

## المعالجة الدفعية

### استخدام Batch API

**OpenAI Batch API:**

</div>

```python
# بدلاً من المعالجة في الوقت الفعلي
batch_input = [
    {"custom_id": "req-1", "method": "POST", "url": "/v1/chat/completions",
     "body": {"model": "gpt-4", "messages": [...]}},
    # ... المزيد من الطلبات
]

# إرسال دفعة (تخفيض 50% في التكلفة)
batch = client.batches.create(
    input_file_id=file_id,
    endpoint="/v1/chat/completions",
    completion_window="24h"
)
```

<div dir="rtl">

**التوفير:** خصم 50% على الطلبات الدفعية

### استراتيجية المعالجة الدفعية

**تجميع الطلبات:**

</div>

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
        # معالجة الكل دفعة واحدة
        results = api.batch_process(self.batch)
        self.batch = []
        return results
```

<div dir="rtl">

**التوفير:** 50% + تقليل النفقات العامة

---

## تحسين البنية التحتية

### تكاليف قاعدة البيانات المتجهة

**مقارنة التكلفة:**

</div>

```
Pinecone (1M vectors): ~$70/شهر
Qdrant (مستضاف ذاتياً): ~$20/شهر (VPS)
Chroma (محلي): $0
```

<div dir="rtl">

**التحسين:**

</div>

```python
# تقليل الأبعاد
from sklearn.decomposition import PCA

pca = PCA(n_components=512)  # من 1536 إلى 512
reduced_embeddings = pca.fit_transform(embeddings)
```

<div dir="rtl">

**التوفير:** تقليل التخزين بنسبة 67%

### تحسين التضمين

**اختر النموذج المناسب:**

</div>

```python
# غالي
embeddings = openai.embeddings.create(
    model="text-embedding-3-large",  # $0.13/1M رمز
    input=texts
)

# اقتصادي
embeddings = openai.embeddings.create(
    model="text-embedding-3-small",  # $0.02/1M رمز
    input=texts
)
```

<div dir="rtl">

**التوفير:** تقليل التكلفة بنسبة 85%

**التضمين الدفعي:**

</div>

```python
# سيء: واحداً تلو الآخر
for text in texts:
    embedding = get_embedding(text)  # 100 استدعاء API

# جيد: دفعي
embeddings = get_embeddings(texts)  # استدعاء API واحد
```

<div dir="rtl">

**التوفير:** تقليل النفقات العامة لـ API

### اعتبارات الاستضافة الذاتية

**متى تستضيف ذاتياً:**
- حجم كبير (>1M طلب/شهر)
- بيانات حساسة
- حمل ثابت
- خبرة تقنية متاحة

**تحليل التكلفة:**

</div>

```
Cloud API: $5,000/شهر (1M استدعاء GPT-4)
الاستضافة الذاتية (Llama 3 70B):
  - خادم GPU: $2,000/شهر
  - الصيانة: $1,000/شهر
  - الإجمالي: $3,000/شهر
التوفير: $2,000/شهر (40%)
```

<div dir="rtl">

---

## المراقبة والتحليلات

### تتبع التكاليف

**التنفيذ:**

</div>

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

<div dir="rtl">

### تنبيهات التكلفة

**تعيين الميزانيات:**

</div>

```python
def check_budget():
    daily_cost = get_daily_cost()

    if daily_cost > DAILY_BUDGET * 0.8:
        send_alert("Approaching daily budget")

    if daily_cost > DAILY_BUDGET:
        send_alert("Budget exceeded!")
        # اختيارياً: التبديل إلى نماذج أرخص
        enable_budget_mode()
```

<div dir="rtl">

### تحليلات الاستخدام

**تتبع المقاييس:**

</div>

```python
metrics = {
    'cost_per_user': total_cost / active_users,
    'cost_per_request': total_cost / request_count,
    'average_tokens_per_request': total_tokens / request_count,
    'model_distribution': model_usage_percentages,
    'cache_hit_rate': cache_hits / total_requests
}
```

<div dir="rtl">

---

## حساب عائد الاستثمار

### تحليل التكلفة والفائدة

**حساب توفير الوقت:**

</div>

```python
def calculate_roi(ai_cost: float, hours_saved: float,
                  hourly_rate: float):
    time_value = hours_saved * hourly_rate
    roi = ((time_value - ai_cost) / ai_cost) * 100
    return roi

# مثال
monthly_ai_cost = 500
hours_saved = 80  # في الشهر
hourly_rate = 50

roi = calculate_roi(monthly_ai_cost, hours_saved, hourly_rate)
# ROI: 700% (توفير $4,000، إنفاق $500)
```

<div dir="rtl">

### قائمة التحقق من التحسين

**مكاسب سريعة:**
- [ ] التبديل للمهام البسيطة إلى GPT-3.5/Haiku
- [ ] تنفيذ التخزين المؤقت للاستجابات
- [ ] تحسين الموجهات (إزالة الحشو)
- [ ] تعيين حدود max_tokens
- [ ] استخدام batch API حيثما أمكن

**جهد متوسط:**
- [ ] تنفيذ توجيه النموذج
- [ ] إضافة التخزين المؤقت الدلالي
- [ ] تحسين التضمينات
- [ ] إدارة نافذة السياق
- [ ] المراقبة والتنبيه بشأن التكاليف

**طويل الأجل:**
- [ ] النظر في الاستضافة الذاتية
- [ ] ضبط دقيق لنماذج أصغر
- [ ] بناء خط تقييم
- [ ] تنفيذ اختبار A/B
- [ ] التحسين المستمر

---

## استراتيجيات تحسين التكلفة حسب الحجم

### شركة ناشئة (<$500/شهر)

**الأولويات:**
1. استخدام المستويات المجانية (Gemini Flash، GPT-3.5)
2. التخزين المؤقت العدواني
3. بنية تحتية بسيطة (Chroma محلي)
4. التحسين اليدوي

**التوفير المتوقع:** 60-70%

### شركة صغيرة ($500-$5K/شهر)

**الأولويات:**
1. توجيه النموذج (رخيص → غالي)
2. التخزين المؤقت للموجهات
3. قاعدة بيانات متجهة مُدارة (Pinecone starter)
4. المراقبة الآلية

**التوفير المتوقع:** 40-50%

### المؤسسة (>$5K/شهر)

**الأولويات:**
1. نماذج مضبوطة دقيقاً
2. حلول مستضافة ذاتياً
3. استراتيجيات تخزين مؤقت متقدمة
4. فريق تحسين مخصص

**التوفير المتوقع:** 30-40%

---

## أمثلة واقعية

### مثال 1: روبوت دعم العملاء

**قبل التحسين:**

</div>

```
Model: GPT-4
متوسط المحادثة: 20 رسالة
الرموز لكل محادثة: 4,000
التكلفة لكل محادثة: $0.20
المحادثات الشهرية: 10,000
التكلفة الشهرية: $2,000
```

<div dir="rtl">

**بعد التحسين:**

</div>

```
توجيه النموذج: GPT-3.5 (80%) + GPT-4 (20%)
تحسين الموجهات: -40% رموز
التخزين المؤقت للاستجابات: معدل إصابة 30%
التكلفة لكل محادثة: $0.06
التكلفة الشهرية: $600
التوفير: $1,400/شهر (70%)
```

<div dir="rtl">

### مثال 2: تحليل الوثائق

**قبل:**

</div>

```
Model: GPT-4
الوثائق في اليوم: 500
الرموز لكل وثيقة: 8,000
التكلفة لكل وثيقة: $0.32
التكلفة الشهرية: $4,800
```

<div dir="rtl">

**بعد:**

</div>

```
Model: Gemini 1.5 Pro (سياق طويل)
المعالجة الدفعية: خصم 50%
تحسين الموجهات: -30% رموز
التكلفة لكل وثيقة: $0.08
التكلفة الشهرية: $1,200
التوفير: $3,600/شهر (75%)
```

<div dir="rtl">

---

## الأدوات والموارد

### أدوات حساب التكلفة
- OpenAI Tokenizer
- Anthropic Token Counter
- AI Cost Calculator (أدوات مخصصة)

### منصات المراقبة
- OpenAI Usage Dashboard
- LangSmith (LangChain)
- Helicone
- تحليلات مخصصة

---

**الخلاصة الرئيسية:** مع التحسين الصحيح، يمكنك تقليل تكاليف الذكاء الاصطناعي بنسبة 50-70% دون التضحية بالجودة. ابدأ بالمكاسب السريعة ونفذ تدريجياً استراتيجيات متقدمة.

**الموارد ذات الصلة:**
- [دليل المقارنة](./COMPARISON-GUIDES.md)
- [دليل التكامل مع API](./API-INTEGRATION-GUIDE.md)
- [المعايير](./BENCHMARKS.md)

</div>
