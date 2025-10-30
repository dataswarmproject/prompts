# Datasets Directory

**Curator: Dr. Ahmed Halloub**

Curated collection of datasets for AI training, fine-tuning, benchmarking, and testing.

---

## Table of Contents

- [General Purpose](#general-purpose)
- [NLP & Text](#nlp--text)
- [Computer Vision](#computer-vision)
- [Code & Programming](#code--programming)
- [Domain-Specific](#domain-specific)
- [Benchmark Datasets](#benchmark-datasets)

---

## General Purpose

### Common Crawl
**Type:** Web corpus
**Size:** 250+ TB
**Use Cases:** Language model training, web mining
**Access:** https://commoncrawl.org/
**License:** Free, various licenses per source

**Description:**
Massive web archive containing billions of web pages. Commonly used for pre-training large language models.

---

### Wikipedia Dumps
**Type:** Encyclopedia articles
**Size:** ~20GB compressed (English)
**Use Cases:** Knowledge base, QA systems, general knowledge
**Access:** https://dumps.wikimedia.org/
**License:** Creative Commons

**Processing:**
```python
from datasets import load_dataset

dataset = load_dataset("wikipedia", "20220301.en")
# Access articles
for article in dataset['train']:
    print(article['title'], article['text'][:100])
```

---

### The Pile
**Type:** Mixed-domain text
**Size:** 825 GB
**Use Cases:** Language model training
**Access:** https://pile.eleuther.ai/
**License:** Various (see documentation)

**Components:**
- Academic papers (ArXiv)
- Books
- GitHub code
- StackExchange
- Wikipedia
- Many others

---

## NLP & Text

### GLUE Benchmark
**Type:** Sentence understanding
**Size:** 9 tasks, varying sizes
**Use Cases:** Model evaluation, classification
**Access:** https://gluebenchmark.com/
**License:** Various

**Tasks:**
- CoLA: Grammatical acceptability
- SST-2: Sentiment analysis
- MRPC: Paraphrase detection
- QQP: Question similarity
- MNLI: Natural language inference
- QNLI: Question answering
- RTE: Textual entailment
- WNLI: Coreference resolution

---

### SQuAD (Stanford Question Answering)
**Type:** Question answering
**Size:** 100K+ questions
**Use Cases:** QA model training, reading comprehension
**Access:** https://rajpurkar.github.io/SQuAD-explorer/
**License:** CC BY-SA 4.0

**Example:**
```json
{
  "context": "The Normans were the people who...",
  "question": "Who were the Normans?",
  "answers": ["the people who in the 10th and 11th centuries gave their name to Normandy"]
}
```

---

### CoNLL-2003 (Named Entity Recognition)
**Type:** NER dataset
**Size:** ~300K tokens
**Use Cases:** Named entity recognition training
**Access:** https://www.clips.uantwerpen.be/conll2003/
**License:** Research use

**Entities:** Person, Location, Organization, Miscellaneous

---

### MultiNLI
**Type:** Natural language inference
**Size:** 433K sentence pairs
**Use Cases:** Textual entailment, NLI
**Access:** https://cims.nyu.edu/~sbowman/multinli/
**License:** CC BY-SA 4.0

---

### Anthropic's HH-RLHF
**Type:** Human feedback
**Size:** 170K+ comparisons
**Use Cases:** RLHF training, preference learning
**Access:** https://huggingface.co/datasets/Anthropic/hh-rlhf
**License:** MIT

**Format:**
```json
{
  "chosen": "Helpful, harmless response",
  "rejected": "Less preferred response"
}
```

---

## Computer Vision

### ImageNet
**Type:** Image classification
**Size:** 14M images, 20K categories
**Use Cases:** Image classification, transfer learning
**Access:** https://www.image-net.org/
**License:** Academic research

**Subsets:**
- ImageNet-1K: 1000 classes
- ImageNet-21K: 21,000 classes

---

### COCO (Common Objects in Context)
**Type:** Object detection, segmentation
**Size:** 330K images, 1.5M object instances
**Use Cases:** Object detection, segmentation, captioning
**Access:** https://cocodataset.org/
**License:** CC BY 4.0

**Annotations:**
- Object detection bounding boxes
- Instance segmentation
- Keypoint detection
- Image captions

---

### CIFAR-10 / CIFAR-100
**Type:** Image classification
**Size:** 60K images (32x32)
**Use Cases:** Model prototyping, benchmarking
**Access:** https://www.cs.toronto.edu/~kriz/cifar.html
**License:** MIT-like

**Classes:**
- CIFAR-10: 10 classes
- CIFAR-100: 100 classes

```python
from torchvision import datasets

cifar10 = datasets.CIFAR10(root='./data', train=True, download=True)
```

---

### Labeled Faces in the Wild (LFW)
**Type:** Face recognition
**Size:** 13K images
**Use Cases:** Face verification, recognition
**Access:** http://vis-www.cs.umass.edu/lfw/
**License:** Non-commercial research

---

## Code & Programming

### The Stack
**Type:** Source code
**Size:** 3TB, 30M files
**Use Cases:** Code generation model training
**Access:** https://huggingface.co/datasets/bigcode/the-stack
**License:** Permissive licenses only

**Languages:** 30+ programming languages

```python
from datasets import load_dataset

ds = load_dataset("bigcode/the-stack", data_dir="data/python")
```

---

### CodeSearchNet
**Type:** Code with documentation
**Size:** 6M functions
**Use Cases:** Code search, documentation generation
**Access:** https://github.com/github/CodeSearchNet
**License:** Various

**Languages:** Python, Java, JavaScript, PHP, Ruby, Go

---

### HumanEval
**Type:** Code evaluation
**Size:** 164 programming problems
**Use Cases:** Code generation benchmark
**Access:** https://github.com/openai/human-eval
**License:** MIT

**Example:**
```python
{
  "task_id": "HumanEval/0",
  "prompt": "def has_close_elements(numbers, threshold):\n    \"\"\" Check if any two numbers are closer than threshold.\n    >>> has_close_elements([1.0, 2.0, 3.0], 0.5)\n    False\n    \"\"\"",
  "canonical_solution": "...",
  "test": "..."
}
```

---

### APPS (Automated Programming Progress Standard)
**Type:** Programming problems
**Size:** 10K problems
**Use Cases:** Code generation, problem-solving
**Access:** https://github.com/hendrycks/apps
**License:** MIT

**Difficulty:** Introductory, Interview, Competition

---

## Domain-Specific

### Medical

#### PubMed Central
**Type:** Biomedical literature
**Size:** 7M+ full-text articles
**Use Cases:** Medical NLP, literature mining
**Access:** https://www.ncbi.nlm.nih.gov/pmc/
**License:** Various (check per article)

#### MIMIC-III
**Type:** Electronic health records
**Size:** 58K admissions
**Use Cases:** Clinical prediction, health analytics
**Access:** https://mimic.mit.edu/
**License:** PhysioNet Credentialed Health Data License (requires training)

---

### Legal

#### CaseOLAP
**Type:** Legal case documents
**Size:** 12M cases
**Use Cases:** Legal analysis, case law research
**Access:** Research datasets
**License:** Academic research

#### MultiLegalPile
**Type:** Legal documents
**Size:** 680GB
**Use Cases:** Legal LLM training
**Access:** https://huggingface.co/datasets/joelniklaus/Multi_Legal_Pile
**License:** Various

---

### Financial

#### Financial PhraseBank
**Type:** Financial sentiment
**Size:** 5K sentences
**Use Cases:** Financial sentiment analysis
**Access:** https://huggingface.co/datasets/financial_phrasebank
**License:** CC BY-NC-SA 3.0

#### SEC Filings
**Type:** Corporate filings
**Size:** Millions of filings
**Use Cases:** Financial analysis, risk assessment
**Access:** https://www.sec.gov/edgar
**License:** Public domain

---

### Scientific

#### ArXiv Dataset
**Type:** Scientific papers
**Size:** 2M+ papers
**Use Cases:** Scientific literature analysis
**Access:** https://www.kaggle.com/Cornell-University/arxiv
**License:** Various (per paper)

#### S2ORC (Semantic Scholar)
**Type:** Academic papers with citations
**Size:** 81M papers
**Use Cases:** Citation analysis, scientific NLP
**Access:** https://github.com/allenai/s2orc
**License:** ODC-BY

---

## Benchmark Datasets

### MMLU (Massive Multitask Language Understanding)
**Type:** Knowledge evaluation
**Size:** 57 subjects, 15K questions
**Use Cases:** LLM capability assessment
**Access:** https://github.com/hendrycks/test
**License:** MIT

**Subjects:** STEM, humanities, social sciences, others

---

### Big-Bench
**Type:** LLM capabilities
**Size:** 200+ tasks
**Use Cases:** Model evaluation across diverse tasks
**Access:** https://github.com/google/BIG-bench
**License:** Apache 2.0

---

### HellaSwag
**Type:** Commonsense reasoning
**Size:** 70K multiple choice questions
**Use Cases:** Evaluating common sense
**Access:** https://rowanzellers.com/hellaswag/
**License:** MIT

---

### TruthfulQA
**Type:** Truthfulness evaluation
**Size:** 817 questions
**Use Cases:** Testing model truthfulness
**Access:** https://github.com/sylinrl/TruthfulQA
**License:** Apache 2.0

---

## Dataset Aggregators

### Hugging Face Datasets
**Access:** https://huggingface.co/datasets
**Count:** 100K+ datasets

```python
from datasets import load_dataset

# Load any dataset
dataset = load_dataset("squad")
dataset = load_dataset("glue", "mrpc")
```

---

### Kaggle Datasets
**Access:** https://www.kaggle.com/datasets
**Count:** 200K+ datasets
**Focus:** Competitions, real-world data

---

### Google Dataset Search
**Access:** https://datasetsearch.research.google.com/
**Function:** Search engine for datasets across the web

---

### Papers With Code
**Access:** https://paperswithcode.com/datasets
**Count:** 10K+ datasets linked with research papers

---

## Data Processing Tools

### Hugging Face Datasets Library
```python
from datasets import load_dataset, Dataset

# Load from Hub
dataset = load_dataset("imdb")

# Create from data
data = {"text": ["hello", "world"], "label": [0, 1]}
dataset = Dataset.from_dict(data)

# Process
dataset = dataset.map(lambda x: {"length": len(x["text"])})
dataset = dataset.filter(lambda x: x["length"] > 5)
```

### Pandas for Tabular Data
```python
import pandas as pd

df = pd.read_csv("dataset.csv")
df = df.dropna()  # Clean
df = df.sample(frac=1)  # Shuffle
train = df[:int(len(df)*0.8)]
test = df[int(len(df)*0.8):]
```

---

## Creating Custom Datasets

### Data Collection

**Web Scraping:**
```python
import requests
from bs4 import BeautifulSoup

def scrape_articles(url):
    response = requests.get(url)
    soup = BeautifulSoup(response.content, 'html.parser')
    articles = soup.find_all('article')
    return [a.get_text() for a in articles]
```

**API Collection:**
```python
import tweepy

# Collect tweets
api = tweepy.Client(bearer_token=BEARER_TOKEN)
tweets = api.search_recent_tweets(query="AI", max_results=100)
```

### Data Annotation

**Tools:**
- Label Studio: https://labelstud.io/
- Prodigy: https://prodi.gy/
- CVAT: https://cvat.org/ (computer vision)

---

## Dataset Best Practices

### Data Quality Checklist

- [ ] Remove duplicates
- [ ] Check for bias
- [ ] Validate labels
- [ ] Balance classes (if needed)
- [ ] Split train/val/test properly
- [ ] Document metadata
- [ ] Include data cards/documentation

### Legal & Ethical

- [ ] Check license compatibility
- [ ] Respect privacy laws (GDPR, CCPA)
- [ ] Remove PII if required
- [ ] Attribute sources
- [ ] Consider bias and fairness
- [ ] Document limitations

---

## Dataset Licenses Quick Reference

| License | Commercial Use | Modifications | Share-Alike |
|---------|---------------|---------------|-------------|
| CC0 | Yes | Yes | No |
| CC BY | Yes | Yes | No |
| CC BY-SA | Yes | Yes | Yes |
| CC BY-NC | No | Yes | No |
| MIT | Yes | Yes | No |
| Apache 2.0 | Yes | Yes | No |

---

**Always verify licenses before using datasets in production or commercial applications.**

**Related Resources:**
- [AI Best Practices](../AI-BEST-PRACTICES.md)
- [Benchmarks](./BENCHMARKS.md)
- [Use Cases Library](./USE-CASES-LIBRARY.md)
