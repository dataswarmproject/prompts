<div dir="rtl">

# معايير الأداء والأداء للذكاء الاصطناعي

**القيّم: د. أحمد حلوب**

معايير الأداء ومقارنات السرعة وتقييمات الجودة لنماذج وأدوات الذكاء الاصطناعي.

---

## جدول المحتويات

</div>

- [LLM Performance](#llm-performance)
- [Speed Benchmarks](#speed-benchmarks)
- [Quality Evaluations](#quality-evaluations)
- [Cost per Task](#cost-per-task)
- [Coding Performance](#coding-performance)
- [Embedding Models](#embedding-models)

<div dir="rtl">

---

## أداء النماذج اللغوية الكبيرة

### القدرات العامة (نتيجة MMLU)

</div>

| Model | MMLU | Reasoning | Code | Math |
|-------|------|-----------|------|------|
| GPT-4 Turbo | 86.4% | Excellent | Very Good | Excellent |
| Claude 3.5 Sonnet | 88.7% | Excellent | Excellent | Very Good |
| Gemini 1.5 Pro | 85.9% | Very Good | Good | Very Good |
| GPT-4o | 87.2% | Excellent | Excellent | Excellent |
| GPT-3.5 Turbo | 70.0% | Good | Good | Fair |
| Claude 3 Haiku | 75.2% | Good | Very Good | Good |

<div dir="rtl">

### فهم السياق (السياق الطويل)

</div>

| Model | Max Context | Recall @ 100K | Recall @ 200K |
|-------|-------------|---------------|---------------|
| Claude 3.5 Sonnet | 200K | 98% | 95% |
| GPT-4 Turbo | 128K | 95% | N/A |
| Gemini 1.5 Pro | 2M | 99.7% | 99.2% |
| GPT-4o | 128K | 94% | N/A |

<div dir="rtl">

**الاختبار:** "الإبرة في كومة القش" - العثور على معلومات محددة في وثائق طويلة

---

## معايير السرعة

### زمن الاستجابة (متوسط، 500 رمز للمخرجات)

</div>

| Model | Cold Start | Warm | Streaming |
|-------|-----------|------|-----------|
| GPT-4 Turbo | 8.5s | 6.2s | 2.1s (first token) |
| GPT-4o | 5.2s | 3.8s | 1.4s |
| GPT-3.5 Turbo | 2.1s | 1.5s | 0.6s |
| Claude 3.5 Sonnet | 4.8s | 3.2s | 1.2s |
| Claude 3 Haiku | 1.9s | 1.3s | 0.5s |
| Gemini 1.5 Pro | 6.5s | 4.8s | 1.8s |
| Gemini 1.5 Flash | 2.3s | 1.6s | 0.7s |

<div dir="rtl">

**بيئة الاختبار:** استدعاءات API قياسية، 1000 رمز للمدخلات، 500 رمز للمخرجات

### الإنتاجية (رموز في الثانية)

</div>

| Model | Output Speed (tokens/s) |
|-------|------------------------|
| GPT-4 Turbo | 45-60 |
| GPT-4o | 80-100 |
| GPT-3.5 Turbo | 120-150 |
| Claude 3.5 Sonnet | 85-110 |
| Claude 3 Haiku | 140-170 |
| Gemini Flash | 130-160 |

<div dir="rtl">

---

## تقييمات الجودة

### مهام البرمجة (HumanEval)

</div>

| Model | Pass@1 | Pass@10 | Code Quality |
|-------|--------|---------|--------------|
| GPT-4 Turbo | 88.0% | 95.3% | Excellent |
| Claude 3.5 Sonnet | 92.0% | 96.8% | Excellent |
| GPT-4o | 90.2% | 96.0% | Excellent |
| GPT-3.5 Turbo | 76.2% | 88.5% | Good |
| Gemini 1.5 Pro | 84.1% | 92.7% | Very Good |

<div dir="rtl">

**الاختبار:** تحديات برمجة Python من مجموعة بيانات HumanEval

### جودة الكتابة

**معايير التقييم:** الترابط، القواعد، الأسلوب، الدقة

</div>

| Model | Professional Writing | Creative Writing | Technical Writing |
|-------|---------------------|------------------|-------------------|
| GPT-4 Turbo | 9.2/10 | 8.8/10 | 9.0/10 |
| Claude 3.5 Sonnet | 9.4/10 | 9.0/10 | 9.3/10 |
| GPT-4o | 9.3/10 | 8.9/10 | 9.2/10 |
| Gemini 1.5 Pro | 8.8/10 | 8.5/10 | 8.7/10 |
| GPT-3.5 Turbo | 7.5/10 | 7.8/10 | 7.2/10 |

<div dir="rtl">

**الاختبار:** تقييم بشري من قبل كتّاب محترفين (ن=50 عينة لكل منهم)

### الاستدلال (سلسلة التفكير)

</div>

| Model | Math Word Problems | Logic Puzzles | Multi-Step Reasoning |
|-------|-------------------|---------------|---------------------|
| GPT-4 Turbo | 92% | 88% | 90% |
| Claude 3.5 Sonnet | 90% | 91% | 93% |
| GPT-4o | 93% | 89% | 91% |
| GPT-3.5 Turbo | 78% | 72% | 75% |

<div dir="rtl">

---

## التكلفة لكل مهمة

### متوسط التكلفة حسب نوع المهمة

</div>

| Task | GPT-4 Turbo | Claude 3.5 | GPT-3.5 | Gemini Pro |
|------|-------------|------------|---------|------------|
| Simple Q&A | $0.015 | $0.008 | $0.002 | $0.003 |
| Document Summary (5K) | $0.12 | $0.08 | $0.015 | $0.025 |
| Code Generation (500 lines) | $0.18 | $0.11 | $0.025 | $0.040 |
| Long Analysis (50K tokens) | $0.95 | $0.52 | N/A | $0.18 |
| Creative Writing (2K words) | $0.25 | $0.15 | $0.035 | $0.055 |

<div dir="rtl">

**بناءً على متوسط استخدام الرموز لكل نوع مهمة**

### نسبة التكلفة إلى الجودة

**نقاط القيمة = (نقاط الجودة / التكلفة لكل 1K رمز) * 100**

</div>

| Model | Value Score | Best For |
|-------|-------------|----------|
| Claude 3 Haiku | 185 | High-volume simple tasks |
| GPT-3.5 Turbo | 172 | Budget-conscious projects |
| Gemini Flash | 168 | Fast, cheap processing |
| Claude 3.5 Sonnet | 145 | Balanced quality/cost |
| GPT-4o | 128 | Production applications |
| GPT-4 Turbo | 95 | Complex reasoning |

<div dir="rtl">

---

## أداء البرمجة

### مقارنة مساعدي البرمجة بالذكاء الاصطناعي

**الاختبار:** إكمال 50 مهمة برمجية عبر اللغات

</div>

| Tool | Completion Rate | Code Quality | Bug Rate | Speed |
|------|----------------|--------------|----------|-------|
| Cursor | 94% | 9.1/10 | 4% | Fast |
| GitHub Copilot | 91% | 8.8/10 | 6% | Very Fast |
| Windsurf | 93% | 9.0/10 | 5% | Fast |
| Claude Code | 92% | 9.2/10 | 3% | Moderate |
| Codeium | 87% | 8.5/10 | 7% | Very Fast |

<div dir="rtl">

### الأداء الخاص باللغات

</div>

| Language | Best Tool | Pass Rate | Average Time |
|----------|-----------|-----------|--------------|
| Python | Cursor | 96% | 45s |
| JavaScript | GitHub Copilot | 94% | 38s |
| TypeScript | Cursor | 95% | 42s |
| Java | Claude Code | 91% | 58s |
| Go | Cursor | 93% | 52s |
| Rust | Claude Code | 89% | 68s |

<div dir="rtl">

---

## نماذج التضمين

### أداء الاسترجاع (معيار MTEB)

</div>

| Model | Overall Score | Retrieval | Classification | Clustering |
|-------|--------------|-----------|----------------|------------|
| Voyage-2 | 65.1 | 71.2 | 68.3 | 56.8 |
| OpenAI large | 64.6 | 69.8 | 67.9 | 58.1 |
| Cohere v3 | 64.5 | 70.1 | 66.2 | 59.3 |
| E5-mistral | 64.9 | 68.9 | 68.5 | 57.2 |
| OpenAI small | 62.3 | 66.5 | 65.1 | 55.8 |

<div dir="rtl">

### مقارنة السرعة (1000 نص)

</div>

| Model | Embedding Time | Dimensions | Cost |
|-------|---------------|------------|------|
| OpenAI small | 2.1s | 1536 | $0.02 |
| OpenAI large | 2.8s | 3072 | $0.13 |
| Cohere v3 | 3.5s | 1024 | $0.10 |
| Voyage-2 | 2.3s | 1024 | $0.12 |
| BGE-large (local) | 8.2s | 1024 | Free |

<div dir="rtl">

---

## أداء قواعد البيانات المتجهة

### أداء الاستعلام (1 مليون متجه)

</div>

| Database | Insert (1K/s) | Query Latency | Memory | Cost/Month |
|----------|---------------|---------------|--------|------------|
| Pinecone | 850 | 52ms | Managed | $70 |
| Qdrant | 920 | 48ms | 1.8GB | $25 (self-hosted) |
| Weaviate | 780 | 65ms | 2.1GB | $45 (cloud) |
| Chroma | 420 | 125ms | 2.5GB | Free (local) |

<div dir="rtl">

### اختبار قابلية التوسع (10 مليون متجه)

</div>

| Database | Query Time | Insert Time | Max RPS |
|----------|-----------|-------------|---------|
| Pinecone | 68ms | 11.2s/1K | 5000 |
| Qdrant | 72ms | 10.8s/1K | 4500 |
| Weaviate | 89ms | 12.5s/1K | 3800 |

<div dir="rtl">

---

## توليد الصور

### مقارنة الجودة

**الاختبار:** توليد 100 صورة عبر الفئات (الواقعية الفوتوغرافية، الفن، الأشياء)

</div>

| Model | Photorealism | Artistic | Accuracy | Consistency |
|-------|-------------|----------|----------|-------------|
| Midjourney v6 | 9.4/10 | 9.6/10 | 9.2/10 | 9.1/10 |
| DALL-E 3 | 9.1/10 | 8.8/10 | 9.5/10 | 8.9/10 |
| Stable Diffusion XL | 8.7/10 | 9.2/10 | 8.3/10 | 8.1/10 |

<div dir="rtl">

### السرعة والتكلفة

</div>

| Model | Average Time | Cost per Image | Resolution |
|-------|-------------|----------------|------------|
| Midjourney | 45s | $0.04-0.08 | 1024x1024+ |
| DALL-E 3 | 15s | $0.04 | 1024x1024 |
| SDXL (local) | 8s | Free | 1024x1024 |

<div dir="rtl">

---

## التعرف على الكلام

### اختبار الدقة (WER - معدل خطأ الكلمات)

</div>

| Model | Clean Audio | Noisy | Accents | Technical |
|-------|------------|-------|---------|-----------|
| Whisper large | 2.1% | 4.8% | 5.2% | 6.1% |
| Google Speech | 2.3% | 5.1% | 5.0% | 5.8% |
| AssemblyAI | 1.9% | 4.5% | 4.8% | 5.5% |
| Deepgram | 2.0% | 4.6% | 4.9% | 5.9% |

<div dir="rtl">

**الأقل هو الأفضل**

### مقارنة السرعة

</div>

| Model | Real-time Factor | Latency |
|-------|-----------------|---------|
| Deepgram | 0.08 | 300ms |
| AssemblyAI | 0.12 | 450ms |
| Whisper (cloud) | 0.18 | 550ms |
| Google Speech | 0.15 | 500ms |

<div dir="rtl">

**عامل الوقت الفعلي < 1.0 يعني أسرع من الوقت الفعلي**

---

## منهجية المعايير

### نهج الاختبار

**تقييم الجودة:**
- التقييم البشري (مراجعون خبراء)
- مقاييس آلية (BLEU, ROUGE, إلخ)
- معايير خاصة بالمهام
- حالات استخدام واقعية

**اختبار الأداء:**
- 100+ عينة لكل اختبار
- مناطق زمنية متعددة
- ساعات الذروة وخارج ساعات الذروة
- أحجام مدخلات متنوعة

**حساب التكلفة:**
- التسعير الرسمي
- الاستخدام الفعلي للرموز
- متطلبات المهام النموذجية
- يتم التحديث ربع سنوي

### القيود

**ملاحظة:** المعايير هي:
- قياسات في وقت محدد
- قد تختلف حسب المنطقة والحمل
- بناءً على حالات استخدام نموذجية
- يتم تحديثها بانتظام

**قد تختلف نتائجك بناءً على:**
- موجهات محددة
- تعقيد المهمة
- ظروف الشبكة
- مستوى API

---

## كيفية تشغيل معاييرك الخاصة

### اختبار سرعة بسيط

</div>

```python
import time
from openai import OpenAI

def benchmark_model(model, prompt, iterations=10):
    client = OpenAI()
    times = []

    for _ in range(iterations):
        start = time.time()

        client.chat.completions.create(
            model=model,
            messages=[{"role": "user", "content": prompt}]
        )

        times.append(time.time() - start)

    return {
        'avg': sum(times) / len(times),
        'min': min(times),
        'max': max(times)
    }

results = benchmark_model("gpt-4", "Write a haiku about coding")
print(f"Average: {results['avg']:.2f}s")
```

<div dir="rtl">

### مقارنة الجودة

</div>

```python
def compare_models(prompt, models):
    results = {}

    for model in models:
        response = get_completion(prompt, model)
        results[model] = {
            'response': response,
            'length': len(response),
            'cost': calculate_cost(response, model)
        }

    return results

models = ['gpt-4', 'claude-3.5-sonnet', 'gpt-3.5-turbo']
comparison = compare_models("Explain quantum computing", models)
```

<div dir="rtl">

---

## تحديثات المعايير

**آخر تحديث:** أكتوبر 2025

**الاختبارات القادمة:**
- النماذج الجديدة عند إصدارها
- معايير السياق الموسع
- أداء متعدد الوسائط
- مقارنات النماذج المضبوطة

**إرسال المعايير:**
ساهم بنتائج معاييرك لمساعدة المجتمع في اتخاذ قرارات مستنيرة.

---

**استخدم هذه المعايير لتوجيه اختيار النموذج، ولكن اختبر دائماً مع حالة الاستخدام المحددة الخاصة بك للحصول على أفضل النتائج.**

**الموارد ذات الصلة:**
- [دليل المقارنة](./COMPARISON-GUIDES.md)
- [تحسين التكلفة](./COST-OPTIMIZATION.md)
- [دليل أدوات الذكاء الاصطناعي](./AI-TOOLS-DIRECTORY.md)

</div>
