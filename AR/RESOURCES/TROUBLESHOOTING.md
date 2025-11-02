<div dir="rtl">

# دليل استكشاف أخطاء الذكاء الاصطناعي

**القيّم: د. أحمد حلوب**

المشاكل الشائعة، الأخطاء، والحلول عند العمل مع أدوات وواجهات برمجة تطبيقات الذكاء الاصطناعي.

---

## جدول المحتويات

</div>

- [API Errors](#api-errors)
- [Rate Limiting](#rate-limiting)
- [Context Window Issues](#context-window-issues)
- [Performance Problems](#performance-problems)
- [Integration Issues](#integration-issues)
- [Quality Issues](#quality-issues)
- [Cost Overruns](#cost-overruns)
- [Debugging Strategies](#debugging-strategies)

<div dir="rtl">

---

## أخطاء API

### خطأ: 401 Unauthorized

**السبب:** مفتاح API غير صالح أو مفقود

**الحلول:**

</div>

```python
# التحقق من تعيين متغير البيئة
import os
api_key = os.getenv('OPENAI_API_KEY')
if not api_key:
    raise ValueError("مفتاح API غير موجود في البيئة")

# التحقق من تنسيق المفتاح
if not api_key.startswith('sk-'):
    raise ValueError("تنسيق مفتاح API غير صالح")

# اختبار المفتاح
from openai import OpenAI
client = OpenAI(api_key=api_key)
try:
    client.models.list()
    print("مفتاح API صالح")
except Exception as e:
    print(f"خطأ في مفتاح API: {e}")
```

<div dir="rtl">

**قائمة التحقق:**
- [ ] مفتاح API في ملف .env
- [ ] تم تحميل ملف .env (.env.load())
- [ ] المفتاح الصحيح للبيئة (dev/prod)
- [ ] المفتاح لم ينته صلاحيته
- [ ] تم تمكين الفوترة على الحساب

---

### خطأ: 429 Rate Limit Exceeded

**السبب:** عدد كبير جداً من الطلبات في وقت قصير

**الحلول:**

**1. تنفيذ التراجع الأسي:**

</div>

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
                print(f"تم تجاوز الحد. الانتظار {wait_time:.2f}ث...")
                time.sleep(wait_time)
            else:
                raise e
    raise Exception("تم تجاوز الحد الأقصى للمحاولات")
```

<div dir="rtl">

**2. تنفيذ تحديد المعدل:**

</div>

```python
from ratelimit import limits, sleep_and_retry

@sleep_and_retry
@limits(calls=10, period=60)  # 10 استدعاءات في الدقيقة
def call_api(prompt):
    return client.chat.completions.create(
        model="gpt-4",
        messages=[{"role": "user", "content": prompt}]
    )
```

<div dir="rtl">

**3. استخدام قوائم انتظار الطلبات:**

</div>

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

<div dir="rtl">

---

### خطأ: 400 Bad Request

**الأسباب الشائعة والإصلاحات:**

**JSON غير صالح:**

</div>

```python
# سيء
messages = str([{"role": "user", "content": "Hello"}])

# جيد
messages = [{"role": "user", "content": "Hello"}]
```

<div dir="rtl">

**معاملات غير صالحة:**

</div>

```python
# التحقق من اسم النموذج
valid_models = ['gpt-4', 'gpt-3.5-turbo', 'gpt-4-turbo']
if model not in valid_models:
    raise ValueError(f"نموذج غير صالح: {model}")

# التحقق من درجة الحرارة
if not 0 <= temperature <= 2:
    raise ValueError("يجب أن تكون درجة الحرارة بين 0 و 2")
```

<div dir="rtl">

**رسائل فارغة:**

</div>

```python
# التحقق قبل الإرسال
if not messages or all(not m.get('content') for m in messages):
    raise ValueError("لا يمكن أن تكون الرسائل فارغة")
```

<div dir="rtl">

---

### خطأ: 500 Internal Server Error

**السبب:** مشكلة من جانب الخادم

**الحلول:**

</div>

```python
def handle_server_error(func, max_retries=3):
    for attempt in range(max_retries):
        try:
            return func()
        except Exception as e:
            if '500' in str(e):
                wait_time = 5 * (attempt + 1)
                print(f"خطأ في الخادم. محاولة {attempt + 1}/{max_retries} في {wait_time}ث")
                time.sleep(wait_time)
            else:
                raise e
    # الإبلاغ إلى المزود إذا استمر
    raise Exception("خطأ خادم مستمر - اتصل بالدعم")
```

<div dir="rtl">

---

## تحديد المعدل

### فهم الحدود

**حدود OpenAI (المستوى 1):**

</div>

```
GPT-4:
  - 10,000 TPM (رموز في الدقيقة)
  - 500 RPM (طلبات في الدقيقة)

GPT-3.5-turbo:
  - 90,000 TPM
  - 3,500 RPM
```

<div dir="rtl">

**حدود Anthropic:**

</div>

```
Claude (افتراضي):
  - 40,000 TPM
  - 50 RPM
```

<div dir="rtl">

### مراقبة الاستخدام

</div>

```python
class UsageMonitor:
    def __init__(self):
        self.requests = []
        self.tokens = []

    def log_request(self, tokens_used):
        now = time.time()
        self.requests.append(now)
        self.tokens.append((now, tokens_used))

        # تنظيف الإدخالات القديمة (> 1 دقيقة)
        cutoff = now - 60
        self.requests = [t for t in self.requests if t > cutoff]
        self.tokens = [(t, n) for t, n in self.tokens if t > cutoff]

    def can_make_request(self, estimated_tokens, rpm_limit, tpm_limit):
        current_rpm = len(self.requests)
        current_tpm = sum(n for t, n in self.tokens)

        return (current_rpm < rpm_limit and
                current_tpm + estimated_tokens < tpm_limit)
```

<div dir="rtl">

### الدفعات لتقليل الطلبات

</div>

```python
# سيء: استدعاءات API متعددة
for item in items:
    response = process(item)

# جيد: استدعاء دفعي واحد
batch_prompt = "\n".join([f"{i+1}. {item}" for i, item in enumerate(items)])
response = process(batch_prompt)
results = parse_batch_response(response)
```

<div dir="rtl">

---

## مشاكل نافذة السياق

### خطأ: تم تجاوز الحد الأقصى لطول السياق

**التشخيص:**

</div>

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
        print(f"تحذير: {total_tokens} رمز يتجاوز حد {limit}")
        return False
    return True
```

<div dir="rtl">

**الحلول:**

**1. القطع الذكي:**

</div>

```python
def truncate_messages(messages, max_tokens=4000):
    # الاحتفاظ برسالة النظام والرسائل الأخيرة
    system = messages[0] if messages[0]['role'] == 'system' else None
    user_messages = [m for m in messages if m['role'] != 'system']

    result = [system] if system else []
    current_tokens = count_tokens(str(system)) if system else 0

    # إضافة الرسائل من الأحدث
    for msg in reversed(user_messages):
        msg_tokens = count_tokens(str(msg))
        if current_tokens + msg_tokens <= max_tokens:
            result.insert(1 if system else 0, msg)
            current_tokens += msg_tokens
        else:
            break

    return result
```

<div dir="rtl">

**2. تلخيص المحادثة:**

</div>

```python
def summarize_conversation(messages):
    if len(messages) > 10:
        # الحصول على ملخص الرسائل القديمة
        old_messages = messages[1:-5]  # تخطي النظام والأخيرة
        summary_prompt = f"لخص هذه المحادثة: {old_messages}"
        summary = get_completion(summary_prompt)

        # إعادة البناء مع الملخص
        return [
            messages[0],  # النظام
            {"role": "system", "content": f"السياق السابق: {summary}"},
            *messages[-5:]  # الرسائل الأخيرة
        ]
    return messages
```

<div dir="rtl">

**3. استخدام نماذج بسياق أطول:**

</div>

```python
# التبديل إلى نافذة سياق أكبر
if tokens_needed > 8000:
    model = "gpt-4-turbo"  # 128K سياق
elif tokens_needed > 100000:
    model = "claude-3.5-sonnet"  # 200K سياق
```

<div dir="rtl">

---

## مشاكل الأداء

### أوقات استجابة بطيئة

**التشخيص:**

</div>

```python
import time

def benchmark_request():
    start = time.time()

    response = client.chat.completions.create(
        model="gpt-4",
        messages=[{"role": "user", "content": "Hello"}]
    )

    duration = time.time() - start
    print(f"استغرق الطلب {duration:.2f}ث")

    return duration
```

<div dir="rtl">

**الحلول:**

**1. استخدام البث:**

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
            print(chunk.choices[0].delta.content, end='')
```

<div dir="rtl">

**2. التبديل إلى نماذج أسرع:**

</div>

```python
# بطيء
model = "gpt-4"  # ~10-30ث وقت استجابة

# سريع
model = "gpt-3.5-turbo"  # ~2-5ث وقت استجابة
model = "claude-3-haiku"  # ~1-3ث وقت استجابة
```

<div dir="rtl">

**3. تقليل طول المخرجات:**

</div>

```python
response = client.chat.completions.create(
    model="gpt-4",
    messages=messages,
    max_tokens=500  # إكمال أسرع
)
```

<div dir="rtl">

**4. استخدام التخزين المؤقت:**

</div>

```python
from functools import lru_cache

@lru_cache(maxsize=1000)
def cached_completion(prompt, model):
    return client.chat.completions.create(
        model=model,
        messages=[{"role": "user", "content": prompt}]
    )
```

<div dir="rtl">

---

## مشاكل التكامل

### أخطاء اتصال قاعدة البيانات المتجهة

**Pinecone:**

</div>

```python
import pinecone

# تصحيح الاتصال
try:
    pinecone.init(
        api_key=os.getenv('PINECONE_API_KEY'),
        environment=os.getenv('PINECONE_ENV')
    )
    print("متصل بـ Pinecone")
except Exception as e:
    print(f"فشل الاتصال: {e}")
    # تحقق: مفتاح API، البيئة، الشبكة
```

<div dir="rtl">

**الإصلاحات الشائعة:**
- التحقق من مفتاح API والبيئة
- فحص إعدادات الجدار الناري/الشبكة
- التأكد من وجود الفهرس
- التحقق من تطابق أبعاد الفهرس مع التضمينات

### مشاكل LangChain

**الوحدة غير موجودة:**

</div>

```bash
# تثبيت الحزم الصحيحة
pip install langchain langchain-openai langchain-community

# التحقق من التثبيت
python -c "import langchain; print(langchain.__version__)"
```

<div dir="rtl">

**الاستيرادات المهملة:**

</div>

```python
# قديم (مهمل)
from langchain.llms import OpenAI

# جديد
from langchain_openai import OpenAI
```

<div dir="rtl">

**أخطاء السلسلة:**

</div>

```python
# تصحيح السلسلة
from langchain.globals import set_debug
set_debug(True)

# تشغيل السلسلة لرؤية السجلات التفصيلية
result = chain.run(input)
```

<div dir="rtl">

---

## مشاكل الجودة

### جودة استجابة ضعيفة

**قائمة التحقق من التشخيص:**
- [ ] هل الموجه واضح ومحدد؟
- [ ] استخدام النموذج المناسب للمهمة؟
- [ ] إعداد درجة الحرارة صحيح؟
- [ ] تقديم سياق كاف؟
- [ ] تضمين أمثلة (few-shot)؟

**الحلول:**

**1. تحسين الموجه:**

</div>

```python
# غامض
prompt = "أخبرني عن الكلاب"

# محدد
prompt = """
قدم نظرة عامة من 3 فقرات عن سلالات الكلاب، تغطي:
1. التصنيف حسب الحجم
2. الاختلافات في الطباع
3. متطلبات التمرين

استخدم نقاط لأهم الحقائق.
"""
```

<div dir="rtl">

**2. ضبط درجة الحرارة:**

</div>

```python
# للمهام الواقعية
temperature = 0.1  # أكثر حتمية

# للمهام الإبداعية
temperature = 0.7  # أكثر إبداعاً
```

<div dir="rtl">

**3. استخدام أمثلة few-shot:**

</div>

```python
prompt = """
صنف المشاعر كإيجابية أو سلبية أو محايدة.

أمثلة:
النص: "أحب هذا المنتج!"
المشاعر: إيجابية

النص: "تجربة رهيبة"
المشاعر: سلبية

النص: "وصل الطرد"
المشاعر: محايدة

النص: "{user_text}"
المشاعر:
"""
```

<div dir="rtl">

### مخرجات غير متسقة

**الحلول:**

**1. تعيين درجة الحرارة إلى 0:**

</div>

```python
response = client.chat.completions.create(
    model="gpt-4",
    messages=messages,
    temperature=0  # حتمي
)
```

<div dir="rtl">

**2. استخدام seed (حيثما كان مدعوماً):**

</div>

```python
response = client.chat.completions.create(
    model="gpt-4",
    messages=messages,
    seed=12345  # نتائج قابلة للتكرار
)
```

<div dir="rtl">

**3. إضافة مخرجات منظمة:**

</div>

```python
prompt = """
الرد بهذا التنسيق JSON بالضبط:
{
  "category": "string",
  "confidence": 0.0-1.0,
  "reasoning": "string"
}
"""
```

<div dir="rtl">

---

## تجاوزات التكلفة

### تكاليف مرتفعة غير متوقعة

**التشخيص:**

</div>

```python
# تتبع جميع الطلبات
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

<div dir="rtl">

**الأسباب الشائعة:**
- حلقات لا نهائية تستدعي API
- نوافذ سياق كبيرة
- حركة مرور إنتاجية كبيرة
- نماذج باهظة الثمن للمهام البسيطة
- عدم وجود تخزين مؤقت

**الحلول:** راجع [دليل تحسين التكلفة](./COST-OPTIMIZATION.md)

---

## استراتيجيات التصحيح

### تمكين التسجيل التفصيلي

</div>

```python
import logging

logging.basicConfig(level=logging.DEBUG)
logger = logging.getLogger(__name__)

# تسجيل جميع الطلبات
def debug_request(prompt, model):
    logger.debug(f"النموذج: {model}")
    logger.debug(f"الموجه: {prompt[:100]}...")

    try:
        response = call_api(prompt, model)
        logger.debug(f"الاستجابة: {str(response)[:100]}...")
        return response
    except Exception as e:
        logger.error(f"خطأ: {e}", exc_info=True)
        raise
```

<div dir="rtl">

### الاختبار في عزلة

</div>

```python
# حالة اختبار بسيطة
def test_api_connection():
    try:
        response = client.chat.completions.create(
            model="gpt-3.5-turbo",
            messages=[{"role": "user", "content": "Hi"}],
            max_tokens=10
        )
        print("API يعمل:", response.choices[0].message.content)
    except Exception as e:
        print("خطأ API:", e)

test_api_connection()
```

<div dir="rtl">

### استخدام Postman/curl لاختبار API

</div>

```bash
# اختبار OpenAI API مباشرة
curl https://api.openai.com/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $OPENAI_API_KEY" \
  -d '{
    "model": "gpt-3.5-turbo",
    "messages": [{"role": "user", "content": "Hello"}]
  }'
```

<div dir="rtl">

---

## مرجع سريع

### رموز الأخطاء

</div>

| Code | Meaning | Action |
|------|---------|--------|
| 401 | Unauthorized | تحقق من مفتاح API |
| 429 | Rate limit | نفذ التراجع |
| 400 | Bad request | تحقق من المدخلات |
| 500 | Server error | أعد المحاولة مع التراجع |
| 503 | Service unavailable | انتظر وأعد المحاولة |

<div dir="rtl">

### قائمة التحقق من التصحيح

- [ ] مفتاح API صالح ومحمّل
- [ ] تنسيق الطلب صحيح
- [ ] اسم النموذج صالح
- [ ] المدخلات ضمن حدود الرموز
- [ ] اتصال الشبكة يعمل
- [ ] لم يتم تجاوز حدود المعدل
- [ ] تم تنفيذ معالجة الأخطاء
- [ ] تم تمكين التسجيل

---

**ما زلت عالقاً؟** تحقق من الوثائق الرسمية أو منتديات المجتمع:
- منتدى مجتمع OpenAI
- Anthropic Discord
- Stack Overflow (الوسوم: [openai-api], [langchain])

**الموارد ذات الصلة:**
- [دليل التكامل مع API](./API-INTEGRATION-GUIDE.md)
- [دليل الأمان](./SECURITY-GUIDE.md)
- [تحسين التكلفة](./COST-OPTIMIZATION.md)

</div>
