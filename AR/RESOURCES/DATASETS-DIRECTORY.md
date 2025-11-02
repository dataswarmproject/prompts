<div dir="rtl">

# دليل مجموعات البيانات

**القيّم: د. أحمد حلوب**

مجموعة منسقة من مجموعات البيانات للتدريب، الضبط الدقيق، المعايير، والاختبار في مجال الذكاء الاصطناعي.

---

## جدول المحتويات

</div>

- [General Purpose](#general-purpose)
- [NLP & Text](#nlp--text)
- [Computer Vision](#computer-vision)
- [Code & Programming](#code--programming)
- [Domain-Specific](#domain-specific)
- [Benchmark Datasets](#benchmark-datasets)

<div dir="rtl">

---

## الأغراض العامة

### Common Crawl
**النوع:** مجموعة ويب
**الحجم:** 250+ تيرابايت
**حالات الاستخدام:** تدريب النماذج اللغوية، استخراج الويب
**الوصول:** https://commoncrawl.org/
**الترخيص:** مجاني، تراخيص متنوعة حسب المصدر

**الوصف:**
أرشيف ويب ضخم يحتوي على مليارات صفحات الويب. يُستخدم بشكل شائع للتدريب المسبق للنماذج اللغوية الكبيرة.

---

### Wikipedia Dumps
**النوع:** مقالات موسوعية
**الحجم:** ~20 جيجابايت مضغوط (الإنجليزية)
**حالات الاستخدام:** قاعدة معرفة، أنظمة الأسئلة والأجوبة، المعرفة العامة
**الوصول:** https://dumps.wikimedia.org/
**الترخيص:** Creative Commons

**المعالجة:**

</div>

```python
from datasets import load_dataset

dataset = load_dataset("wikipedia", "20220301.en")
# الوصول إلى المقالات
for article in dataset['train']:
    print(article['title'], article['text'][:100])
```

<div dir="rtl">

---

### The Pile
**النوع:** نص متعدد المجالات
**الحجم:** 825 جيجابايت
**حالات الاستخدام:** تدريب النماذج اللغوية
**الوصول:** https://pile.eleuther.ai/
**الترخيص:** متنوع (راجع الوثائق)

**المكونات:**
- أوراق أكاديمية (ArXiv)
- كتب
- أكواد GitHub
- StackExchange
- Wikipedia
- العديد من المصادر الأخرى

---

## معالجة اللغة الطبيعية والنصوص

### GLUE Benchmark
**النوع:** فهم الجملة
**الحجم:** 9 مهام، أحجام متنوعة
**حالات الاستخدام:** تقييم النموذج، التصنيف
**الوصول:** https://gluebenchmark.com/
**الترخيص:** متنوع

**المهام:**
- CoLA: القبول النحوي
- SST-2: تحليل المشاعر
- MRPC: الكشف عن إعادة الصياغة
- QQP: تشابه الأسئلة
- MNLI: الاستنتاج اللغوي الطبيعي
- QNLI: الإجابة على الأسئلة
- RTE: الاستلزام النصي
- WNLI: حل الإشارة المرجعية

---

### SQuAD (Stanford Question Answering)
**النوع:** الإجابة على الأسئلة
**الحجم:** 100K+ سؤال
**حالات الاستخدام:** تدريب نماذج الأسئلة والأجوبة، الفهم القرائي
**الوصول:** https://rajpurkar.github.io/SQuAD-explorer/
**الترخيص:** CC BY-SA 4.0

**مثال:**

</div>

```json
{
  "context": "The Normans were the people who...",
  "question": "Who were the Normans?",
  "answers": ["the people who in the 10th and 11th centuries gave their name to Normandy"]
}
```

<div dir="rtl">

---

### CoNLL-2003 (Named Entity Recognition)
**النوع:** مجموعة بيانات NER
**الحجم:** ~300K رمز
**حالات الاستخدام:** تدريب التعرف على الكيانات المسماة
**الوصول:** https://www.clips.uantwerpen.be/conll2003/
**الترخيص:** للاستخدام البحثي

**الكيانات:** شخص، موقع، منظمة، متنوع

---

### MultiNLI
**النوع:** الاستنتاج اللغوي الطبيعي
**الحجم:** 433K زوج جملة
**حالات الاستخدام:** الاستلزام النصي، NLI
**الوصول:** https://cims.nyu.edu/~sbowman/multinli/
**الترخيص:** CC BY-SA 4.0

---

### Anthropic's HH-RLHF
**النوع:** ملاحظات بشرية
**الحجم:** 170K+ مقارنة
**حالات الاستخدام:** تدريب RLHF، تعلم التفضيلات
**الوصول:** https://huggingface.co/datasets/Anthropic/hh-rlhf
**الترخيص:** MIT

**التنسيق:**

</div>

```json
{
  "chosen": "Helpful, harmless response",
  "rejected": "Less preferred response"
}
```

<div dir="rtl">

---

## رؤية الكمبيوتر

### ImageNet
**النوع:** تصنيف الصور
**الحجم:** 14 مليون صورة، 20K فئة
**حالات الاستخدام:** تصنيف الصور، التعلم بالنقل
**الوصول:** https://www.image-net.org/
**الترخيص:** للبحث الأكاديمي

**المجموعات الفرعية:**
- ImageNet-1K: 1000 فئة
- ImageNet-21K: 21,000 فئة

---

### COCO (Common Objects in Context)
**النوع:** الكشف عن الأشياء، التقسيم
**الحجم:** 330K صورة، 1.5 مليون كائن
**حالات الاستخدام:** كشف الأشياء، التقسيم، التعليق
**الوصول:** https://cocodataset.org/
**الترخيص:** CC BY 4.0

**التعليقات التوضيحية:**
- مربعات حدود الكشف عن الأشياء
- تقسيم الحالات
- الكشف عن النقاط الرئيسية
- تعليقات الصور

---

### CIFAR-10 / CIFAR-100
**النوع:** تصنيف الصور
**الحجم:** 60K صورة (32x32)
**حالات الاستخدام:** نماذج أولية، معايير
**الوصول:** https://www.cs.toronto.edu/~kriz/cifar.html
**الترخيص:** شبيه بـ MIT

**الفئات:**
- CIFAR-10: 10 فئات
- CIFAR-100: 100 فئة

</div>

```python
from torchvision import datasets

cifar10 = datasets.CIFAR10(root='./data', train=True, download=True)
```

<div dir="rtl">

---

### Labeled Faces in the Wild (LFW)
**النوع:** التعرف على الوجوه
**الحجم:** 13K صورة
**حالات الاستخدام:** التحقق من الوجه، التعرف
**الوصول:** http://vis-www.cs.umass.edu/lfw/
**الترخيص:** للبحث غير التجاري

---

## البرمجة والكود

### The Stack
**النوع:** كود مصدري
**الحجم:** 3 تيرابايت، 30 مليون ملف
**حالات الاستخدام:** تدريب نماذج توليد الأكواد
**الوصول:** https://huggingface.co/datasets/bigcode/the-stack
**الترخيص:** تراخيص مسموحة فقط

**اللغات:** 30+ لغة برمجة

</div>

```python
from datasets import load_dataset

ds = load_dataset("bigcode/the-stack", data_dir="data/python")
```

<div dir="rtl">

---

### CodeSearchNet
**النوع:** كود مع توثيق
**الحجم:** 6 مليون دالة
**حالات الاستخدام:** البحث عن الأكواد، توليد التوثيق
**الوصول:** https://github.com/github/CodeSearchNet
**الترخيص:** متنوع

**اللغات:** Python، Java، JavaScript، PHP، Ruby، Go

---

### HumanEval
**النوع:** تقييم الأكواد
**الحجم:** 164 مشكلة برمجية
**حالات الاستخدام:** معيار توليد الأكواد
**الوصول:** https://github.com/openai/human-eval
**الترخيص:** MIT

**مثال:**

</div>

```python
{
  "task_id": "HumanEval/0",
  "prompt": "def has_close_elements(numbers, threshold):\n    \"\"\" Check if any two numbers are closer than threshold.\n    >>> has_close_elements([1.0, 2.0, 3.0], 0.5)\n    False\n    \"\"\"",
  "canonical_solution": "...",
  "test": "..."
}
```

<div dir="rtl">

---

### APPS (Automated Programming Progress Standard)
**النوع:** مشاكل برمجية
**الحجم:** 10K مشكلة
**حالات الاستخدام:** توليد الأكواد، حل المشكلات
**الوصول:** https://github.com/hendrycks/apps
**الترخيص:** MIT

**الصعوبة:** تمهيدي، مقابلة، منافسة

---

## خاص بالمجال

### الطبي

#### PubMed Central
**النوع:** أدبيات طبية حيوية
**الحجم:** 7 مليون+ مقال كامل النص
**حالات الاستخدام:** NLP طبي، استخراج الأدبيات
**الوصول:** https://www.ncbi.nlm.nih.gov/pmc/
**الترخيص:** متنوع (تحقق لكل مقال)

#### MIMIC-III
**النوع:** سجلات صحية إلكترونية
**الحجم:** 58K حالة دخول
**حالات الاستخدام:** التنبؤ السريري، تحليلات صحية
**الوصول:** https://mimic.mit.edu/
**الترخيص:** ترخيص بيانات PhysioNet الصحية المعتمدة (يتطلب تدريب)

---

### القانوني

#### CaseOLAP
**النوع:** وثائق قضايا قانونية
**الحجم:** 12 مليون قضية
**حالات الاستخدام:** التحليل القانوني، أبحاث السوابق القضائية
**الوصول:** مجموعات بيانات بحثية
**الترخيص:** للبحث الأكاديمي

#### MultiLegalPile
**النوع:** وثائق قانونية
**الحجم:** 680 جيجابايت
**حالات الاستخدام:** تدريب LLM القانوني
**الوصول:** https://huggingface.co/datasets/joelniklaus/Multi_Legal_Pile
**الترخيص:** متنوع

---

### المالي

#### Financial PhraseBank
**النوع:** المشاعر المالية
**الحجم:** 5K جملة
**حالات الاستخدام:** تحليل المشاعر المالية
**الوصول:** https://huggingface.co/datasets/financial_phrasebank
**الترخيص:** CC BY-NC-SA 3.0

#### SEC Filings
**النوع:** ملفات الشركات
**الحجم:** ملايين الملفات
**حالات الاستخدام:** التحليل المالي، تقييم المخاطر
**الوصول:** https://www.sec.gov/edgar
**الترخيص:** الملك العام

---

### العلمي

#### ArXiv Dataset
**النوع:** أوراق علمية
**الحجم:** 2 مليون+ ورقة
**حالات الاستخدام:** تحليل الأدبيات العلمية
**الوصول:** https://www.kaggle.com/Cornell-University/arxiv
**الترخيص:** متنوع (لكل ورقة)

#### S2ORC (Semantic Scholar)
**النوع:** أوراق أكاديمية مع اقتباسات
**الحجم:** 81 مليون ورقة
**حالات الاستخدام:** تحليل الاقتباسات، NLP علمي
**الوصول:** https://github.com/allenai/s2orc
**الترخيص:** ODC-BY

---

## مجموعات بيانات المعايير

### MMLU (Massive Multitask Language Understanding)
**النوع:** تقييم المعرفة
**الحجم:** 57 موضوع، 15K سؤال
**حالات الاستخدام:** تقييم قدرات LLM
**الوصول:** https://github.com/hendrycks/test
**الترخيص:** MIT

**المواضيع:** العلوم، العلوم الإنسانية، العلوم الاجتماعية، أخرى

---

### Big-Bench
**النوع:** قدرات LLM
**الحجم:** 200+ مهمة
**حالات الاستخدام:** تقييم النماذج عبر مهام متنوعة
**الوصول:** https://github.com/google/BIG-bench
**الترخيص:** Apache 2.0

---

### HellaSwag
**النوع:** الاستدلال الفطري السليم
**الحجم:** 70K سؤال اختيار من متعدد
**حالات الاستخدام:** تقييم الحس السليم
**الوصول:** https://rowanzellers.com/hellaswag/
**الترخيص:** MIT

---

### TruthfulQA
**النوع:** تقييم الصدق
**الحجم:** 817 سؤال
**حالات الاستخدام:** اختبار صدق النموذج
**الوصول:** https://github.com/sylinrl/TruthfulQA
**الترخيص:** Apache 2.0

---

## مجمعات مجموعات البيانات

### Hugging Face Datasets
**الوصول:** https://huggingface.co/datasets
**العدد:** 100K+ مجموعة بيانات

</div>

```python
from datasets import load_dataset

# تحميل أي مجموعة بيانات
dataset = load_dataset("squad")
dataset = load_dataset("glue", "mrpc")
```

<div dir="rtl">

---

### Kaggle Datasets
**الوصول:** https://www.kaggle.com/datasets
**العدد:** 200K+ مجموعة بيانات
**التركيز:** المسابقات، بيانات العالم الحقيقي

---

### Google Dataset Search
**الوصول:** https://datasetsearch.research.google.com/
**الوظيفة:** محرك بحث لمجموعات البيانات عبر الويب

---

### Papers With Code
**الوصول:** https://paperswithcode.com/datasets
**العدد:** 10K+ مجموعة بيانات مرتبطة بأوراق بحثية

---

## أدوات معالجة البيانات

### Hugging Face Datasets Library

</div>

```python
from datasets import load_dataset, Dataset

# التحميل من Hub
dataset = load_dataset("imdb")

# الإنشاء من البيانات
data = {"text": ["hello", "world"], "label": [0, 1]}
dataset = Dataset.from_dict(data)

# المعالجة
dataset = dataset.map(lambda x: {"length": len(x["text"])})
dataset = dataset.filter(lambda x: x["length"] > 5)
```

<div dir="rtl">

### Pandas للبيانات الجدولية

</div>

```python
import pandas as pd

df = pd.read_csv("dataset.csv")
df = df.dropna()  # التنظيف
df = df.sample(frac=1)  # الخلط
train = df[:int(len(df)*0.8)]
test = df[int(len(df)*0.8):]
```

<div dir="rtl">

---

## إنشاء مجموعات بيانات مخصصة

### جمع البيانات

**استخراج الويب:**

</div>

```python
import requests
from bs4 import BeautifulSoup

def scrape_articles(url):
    response = requests.get(url)
    soup = BeautifulSoup(response.content, 'html.parser')
    articles = soup.find_all('article')
    return [a.get_text() for a in articles]
```

<div dir="rtl">

**جمع API:**

</div>

```python
import tweepy

# جمع التغريدات
api = tweepy.Client(bearer_token=BEARER_TOKEN)
tweets = api.search_recent_tweets(query="AI", max_results=100)
```

<div dir="rtl">

### تعليق البيانات

**الأدوات:**
- Label Studio: https://labelstud.io/
- Prodigy: https://prodi.gy/
- CVAT: https://cvat.org/ (رؤية الكمبيوتر)

---

## أفضل ممارسات مجموعات البيانات

### قائمة التحقق من جودة البيانات

- [ ] إزالة التكرارات
- [ ] التحقق من التحيز
- [ ] التحقق من صحة التسميات
- [ ] موازنة الفئات (إذا لزم الأمر)
- [ ] تقسيم train/val/test بشكل صحيح
- [ ] توثيق البيانات الوصفية
- [ ] تضمين بطاقات/وثائق البيانات

### القانونية والأخلاقية

- [ ] التحقق من توافق الترخيص
- [ ] احترام قوانين الخصوصية (GDPR، CCPA)
- [ ] إزالة PII إذا لزم الأمر
- [ ] نسب المصادر
- [ ] النظر في التحيز والإنصاف
- [ ] توثيق القيود

---

## مرجع سريع لتراخيص مجموعات البيانات

</div>

| License | Commercial Use | Modifications | Share-Alike |
|---------|---------------|---------------|-------------|
| CC0 | Yes | Yes | No |
| CC BY | Yes | Yes | No |
| CC BY-SA | Yes | Yes | Yes |
| CC BY-NC | No | Yes | No |
| MIT | Yes | Yes | No |
| Apache 2.0 | Yes | Yes | No |

<div dir="rtl">

---

**تحقق دائماً من التراخيص قبل استخدام مجموعات البيانات في الإنتاج أو التطبيقات التجارية.**

**الموارد ذات الصلة:**
- [أفضل ممارسات الذكاء الاصطناعي](../AI-BEST-PRACTICES.md)
- [المعايير](./BENCHMARKS.md)
- [مكتبة حالات الاستخدام](./USE-CASES-LIBRARY.md)

</div>
