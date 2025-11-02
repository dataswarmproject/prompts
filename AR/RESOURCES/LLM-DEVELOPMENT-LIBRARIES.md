<div dir="rtl">

# دليل مكتبات تطوير نماذج اللغة الكبيرة

**أكثر من 120 مكتبة بايثون لهندسة نماذج اللغة الكبيرة**

مجموعة شاملة ومنسقة من مكتبات بايثون لبناء ونشر وتحسين تطبيقات نماذج اللغة الكبيرة. يغطي هذا الدليل دورة التطوير الكاملة لنماذج اللغة الكبيرة من التدريب إلى النشر في الإنتاج.

---

## جدول المحتويات

- [التدريب والضبط الدقيق](#التدريب-والضبط-الدقيق)
- [تطوير التطبيقات](#تطوير-التطبيقات)
- [RAG (التوليد المعزز بالاسترجاع)](#rag-التوليد-المعزز-بالاسترجاع)
- [الاستدلال](#الاستدلال)
- [الخدمة والنشر](#الخدمة-والنشر)
- [استخراج البيانات](#استخراج-البيانات)
- [توليد البيانات](#توليد-البيانات)
- [الوكلاء](#الوكلاء)
- [التقييم](#التقييم)
- [المراقبة](#المراقبة)
- [القوالب](#القوالب)
- [المخرجات المنظمة](#المخرجات-المنظمة)
- [الأمان والسلامة](#الأمان-والسلامة)
- [نماذج التضمين](#نماذج-التضمين)
- [مكتبات أخرى](#مكتبات-أخرى)

---

## التدريب والضبط الدقيق

مكتبات وأطر عمل لتدريب والضبط الدقيق لنماذج اللغة الكبيرة.

| المكتبة | الوصف | الرابط |
|---------|-------|--------|
| unsloth | ضبط دقيق أسرع لنماذج اللغة الكبيرة مع ذاكرة أقل. | [الرابط](https://github.com/unslothai/unsloth) |
| PEFT | مكتبة متقدمة للضبط الدقيق الفعال للمعاملات. | [الرابط](https://github.com/huggingface/peft) |
| TRL | تدريب نماذج اللغة المحولة بالتعلم المعزز. | [الرابط](https://github.com/huggingface/trl) |
| Transformers | توفر آلاف النماذج المدربة مسبقاً لمهام مختلفة على النصوص والصور والصوت. | [الرابط](https://github.com/huggingface/transformers) |
| Axolotl | أداة مصممة لتبسيط التدريب اللاحق لنماذج الذكاء الاصطناعي. | [الرابط](https://github.com/axolotl-ai-cloud/axolotl/) |
| LLMBox | مكتبة شاملة لتنفيذ نماذج اللغة الكبيرة مع خط تدريب موحد وتقييم شامل. | [الرابط](https://github.com/RUCAIBox/LLMBox) |
| LitGPT | تدريب وضبط دقيق سريع لنماذج اللغة الكبيرة. | [الرابط](https://github.com/Lightning-AI/litgpt) |
| Mergoo | مكتبة لدمج خبراء نماذج اللغة الكبيرة المتعددة بسهولة. | [الرابط](https://github.com/Leeroo-AI/mergoo) |
| Llama-Factory | ضبط دقيق سهل وفعال لنماذج اللغة الكبيرة. | [الرابط](https://github.com/hiyouga/LLaMA-Factory) |
| Ludwig | إطار عمل منخفض الكود لبناء نماذج لغة كبيرة وشبكات عصبية مخصصة. | [الرابط](https://github.com/ludwig-ai/ludwig) |
| Txtinstruct | إطار عمل لتدريب النماذج المضبوطة بالتعليمات. | [الرابط](https://github.com/neuml/txtinstruct) |
| Lamini | منصة متكاملة للاستدلال والضبط الدقيق لنماذج اللغة الكبيرة. | [الرابط](https://github.com/lamini-ai/lamini) |
| XTuring | ضبط دقيق سريع وفعال وبسيط لنماذج اللغة الكبيرة مفتوحة المصدر. | [الرابط](https://github.com/stochasticai/xTuring) |
| RL4LMs | مكتبة معيارية للتعلم المعزز لضبط نماذج اللغة حسب التفضيلات البشرية. | [الرابط](https://github.com/allenai/RL4LMs) |
| DeepSpeed | مكتبة تحسين التعلم العميق تجعل التدريب والاستدلال الموزع سهلاً وفعالاً. | [الرابط](https://github.com/deepspeedai/DeepSpeed) |
| torchtune | مكتبة PyTorch مصممة خصيصاً للضبط الدقيق لنماذج اللغة الكبيرة. | [الرابط](https://github.com/pytorch/torchtune) |
| PyTorch Lightning | مكتبة توفر واجهة عالية المستوى للتدريب المسبق والضبط الدقيق. | [الرابط](https://github.com/Lightning-AI/pytorch-lightning) |

---

## تطوير التطبيقات

### أطر العمل

أطر عمل شاملة لبناء التطبيقات المدعومة بنماذج اللغة الكبيرة.

| المكتبة | الوصف | الرابط |
|---------|-------|--------|
| LangChain | إطار عمل لتطوير التطبيقات المدعومة بنماذج اللغة الكبيرة. | [الرابط](https://github.com/langchain-ai/langchain) |
| Llama Index | إطار بيانات لتطبيقات نماذج اللغة الكبيرة. | [الرابط](https://github.com/run-llama/llama_index) |
| HayStack | إطار عمل شامل لبناء التطبيقات المدعومة بنماذج اللغة والبحث الموجه. | [الرابط](https://github.com/deepset-ai/haystack) |
| Prompt flow | مجموعة أدوات تطوير لتبسيط دورة التطوير الكاملة للتطبيقات المعتمدة على نماذج اللغة. | [الرابط](https://github.com/microsoft/promptflow) |
| Griptape | إطار عمل بايثون معياري لبناء التطبيقات المدعومة بالذكاء الاصطناعي. | [الرابط](https://github.com/griptape-ai/griptape) |
| Weave | مجموعة أدوات لتطوير تطبيقات الذكاء الاصطناعي التوليدي. | [الرابط](https://github.com/wandb/weave) |
| Llama Stack | بناء تطبيقات Llama. | [الرابط](https://github.com/meta-llama/llama-stack) |

### إعداد البيانات

| المكتبة | الوصف | الرابط |
|---------|-------|--------|
| Data Prep Kit | تسريع إعداد البيانات غير المنظمة لمطوري تطبيقات نماذج اللغة الكبيرة. | [الرابط](https://github.com/data-prep-kit/data-prep-kit) |

### الوصول المتعدد لواجهات برمجة التطبيقات

| المكتبة | الوصف | الرابط |
|---------|-------|--------|
| LiteLLM | مكتبة لاستدعاء أكثر من 100 واجهة برمجة تطبيقات بتنسيق OpenAI. | [الرابط](https://github.com/BerriAI/litellm) |
| AI Gateway | بوابة ذكاء اصطناعي سريعة مع حمايات متكاملة للتوجيه إلى أكثر من 200 نموذج. | [الرابط](https://github.com/Portkey-AI/gateway) |

### الموجهات

| المكتبة | الوصف | الرابط |
|---------|-------|--------|
| RouteLLM | إطار عمل لخدمة وتقييم موجهات نماذج اللغة لتوفير التكاليف. | [الرابط](https://github.com/lm-sys/RouteLLM) |

### الذاكرة

| المكتبة | الوصف | الرابط |
|---------|-------|--------|
| mem0 | طبقة الذاكرة لتطبيقات الذكاء الاصطناعي. | [الرابط](https://github.com/mem0ai/mem0) |
| Memoripy | طبقة ذاكرة ذكاء اصطناعي مع تخزين قصير وطويل الأمد وتجميع دلالي. | [الرابط](https://github.com/caspianmoon/memoripy) |
| Letta (MemGPT) | إطار عمل مفتوح المصدر لبناء تطبيقات ذات حالة مع ذاكرة طويلة الأمد. | [الرابط](https://github.com/letta-ai/letta) |
| Memobase | نظام ذاكرة قائم على ملف تعريف المستخدم للتطبيقات التوليدية. | [الرابط](https://github.com/memodb-io/memobase) |

### الواجهات

| المكتبة | الوصف | الرابط |
|---------|-------|--------|
| Streamlit | طريقة أسرع لبناء ومشاركة تطبيقات البيانات. | [الرابط](https://github.com/streamlit/streamlit) |
| Gradio | بناء ومشاركة تطبيقات التعلم الآلي بكل بايثون. | [الرابط](https://github.com/gradio-app/gradio) |
| AI SDK UI | بناء واجهات مستخدم للدردشة والتطبيقات التوليدية. | [الرابط](https://sdk.vercel.ai/docs/introduction) |
| AI-Gradio | إنشاء تطبيقات ذكاء اصطناعي مدعومة بمزودين متعددين. | [الرابط](https://github.com/AK391/ai-gradio) |
| Simpleaichat | حزمة بايثون للتفاعل السهل مع تطبيقات الدردشة. | [الرابط](https://github.com/minimaxir/simpleaichat) |
| Chainlit | بناء تطبيقات ذكاء اصطناعي محادثة جاهزة للإنتاج في دقائق. | [الرابط](https://github.com/Chainlit/chainlit) |

### كود منخفض

| المكتبة | الوصف | الرابط |
|---------|-------|--------|
| LangFlow | منشئ تطبيقات منخفض الكود لـ RAG والوكلاء المتعددة. | [الرابط](https://github.com/langflow-ai/langflow) |

### ذاكرة التخزين المؤقت

| المكتبة | الوصف | الرابط |
|---------|-------|--------|
| GPTCache | مكتبة لإنشاء ذاكرة تخزين مؤقت دلالية لاستعلامات نماذج اللغة. | [الرابط](https://github.com/zilliztech/gptcache) |

---

## RAG (التوليد المعزز بالاسترجاع)

مكتبات وأطر عمل مصممة خصيصاً للتوليد المعزز بالاسترجاع.

| المكتبة | الوصف | الرابط |
|---------|-------|--------|
| FastGraph RAG | إطار عمل GraphRAG سريع قابل للتوجيه والتفسير. | [الرابط](https://github.com/circlemind-ai/fast-graphrag) |
| Chonkie | مكتبة تجزئة RAG خفيفة وسريعة وسهلة الاستخدام. | [الرابط](https://github.com/chonkie-ai/chonkie) |
| RAGChecker | إطار عمل دقيق لتشخيص RAG. | [الرابط](https://github.com/amazon-science/RAGChecker) |
| RAG to Riches | بناء ونشر تطبيقات RAG المتقدمة. | [الرابط](https://github.com/SciPhi-AI/R2R) |
| BeyondLLM | مجموعة أدوات شاملة للتجريب والتقييم ونشر أنظمة RAG. | [الرابط](https://github.com/aiplanethub/beyondllm) |
| SQLite-Vec | امتداد بحث موجه لـ SQLite يعمل في أي مكان! | [الرابط](https://github.com/asg017/sqlite-vec) |
| fastRAG | إطار بحثي لخطوط أنابيب توليدية فعالة ومحسنة. | [الرابط](https://github.com/IntelLabs/fastRAG) |
| FlashRAG | مجموعة أدوات بايثون لبحث RAG الفعال. | [الرابط](https://github.com/RUC-NLPIR/FlashRAG) |
| Llmware | إطار عمل موحد لبناء خطوط أنابيب RAG للمؤسسات. | [الرابط](https://github.com/llmware-ai/llmware) |
| Rerankers | واجهة برمجة تطبيقات موحدة خفيفة الوزن لنماذج إعادة الترتيب. | [الرابط](https://github.com/AnswerDotAI/rerankers) |
| Vectara | بناء تطبيقات RAG مع الوكلاء. | [الرابط](https://vectara.github.io/py-vectara-agentic/latest/) |

---

## الاستدلال

مكتبات لتحسين أداء استدلال نماذج اللغة الكبيرة.

| المكتبة | الوصف | الرابط |
|---------|-------|--------|
| LLM Compressor | مكتبة متوافقة مع Transformers لتطبيق خوارزميات الضغط. | [الرابط](https://github.com/vllm-project/llm-compressor) |
| LightLLM | إطار عمل استدلال وخدمة خفيف الوزن وقابل للتوسع. | [الرابط](https://github.com/ModelTC/lightllm) |
| vLLM | محرك استدلال عالي الإنتاجية وفعال للذاكرة لنماذج اللغة الكبيرة. | [الرابط](https://github.com/vllm-project/vllm) |
| torchchat | تشغيل نماذج PyTorch اللغوية محلياً على الخوادم والأجهزة المحمولة. | [الرابط](https://github.com/pytorch/torchchat) |
| TensorRT-LLM | مكتبة لتحسين استدلال نماذج اللغة الكبيرة. | [الرابط](https://github.com/NVIDIA/TensorRT-LLM) |
| WebLLM | محرك استدلال عالي الأداء داخل المتصفح. | [الرابط](https://github.com/mlc-ai/web-llm) |

---

## الخدمة والنشر

مكتبات لنشر وخدمة تطبيقات نماذج اللغة الكبيرة.

| المكتبة | الوصف | الرابط |
|---------|-------|--------|
| Langcorn | خدمة تطبيقات ووكلاء LangChain تلقائياً مع FastAPI. | [الرابط](https://github.com/msoedov/langcorn) |
| LitServe | محرك خدمة سريع لأي نموذج ذكاء اصطناعي بأي حجم. | [الرابط](https://github.com/Lightning-AI/LitServe) |

---

## استخراج البيانات

أدوات لاستخراج وتحليل البيانات لتطبيقات نماذج اللغة الكبيرة.

| المكتبة | الوصف | الرابط |
|---------|-------|--------|
| Crawl4AI | زاحف وكاشط ويب مفتوح المصدر متوافق مع نماذج اللغة الكبيرة. | [الرابط](https://github.com/unclecode/crawl4ai) |
| ScrapeGraphAI | مكتبة كشط ويب تستخدم نماذج اللغة الكبيرة والمنطق البياني. | [الرابط](https://github.com/ScrapeGraphAI/Scrapegraph-ai) |
| Docling | تحليل المستندات وتصديرها بسهولة وسرعة. | [الرابط](https://github.com/DS4SD/docling) |
| Llama Parse | محلل مستندات أصلي للذكاء التوليدي. | [الرابط](https://github.com/run-llama/llama_cloud_services) |
| PyMuPDF4LLM | تسهيل استخراج محتوى PDF بالتنسيق المناسب لنماذج اللغة الكبيرة. | [الرابط](https://pymupdf.readthedocs.io/en/latest/pymupdf4llm/) |
| Crawlee | مكتبة كشط ويب وأتمتة متصفح. | [الرابط](https://github.com/apify/crawlee-python) |
| MegaParse | محلل لكل نوع من المستندات. | [الرابط](https://github.com/quivrhq/megaparse) |
| ExtractThinker | مكتبة ذكاء المستندات لنماذج اللغة الكبيرة. | [الرابط](https://github.com/enoch3712/ExtractThinker) |

---

## توليد البيانات

مكتبات لتوليد البيانات الاصطناعية باستخدام نماذج اللغة الكبيرة.

| المكتبة | الوصف | الرابط |
|---------|-------|--------|
| DataDreamer | مكتبة قوية مفتوحة المصدر للتوجيه وتوليد البيانات الاصطناعية. | [الرابط](https://github.com/datadreamer-dev/DataDreamer) |
| fabricator | إطار عمل مرن مفتوح المصدر لتوليد مجموعات البيانات. | [الرابط](https://github.com/flairNLP/fabricator) |
| Promptwright | مكتبة توليد مجموعات البيانات الاصطناعية. | [الرابط](https://github.com/stacklok/promptwright) |
| EasyInstruct | إطار عمل سهل الاستخدام لمعالجة التعليمات. | [الرابط](https://github.com/zjunlp/EasyInstruct) |

---

## الوكلاء

أطر عمل وأدوات لبناء الوكلاء الذكية باستخدام نماذج اللغة الكبيرة.

| المكتبة | الوصف | الرابط |
|---------|-------|--------|
| CrewAI | إطار عمل لتنسيق الوكلاء المستقلة ذات الأدوار. | [الرابط](https://github.com/crewAIInc/crewAI) |
| LangGraph | بناء وكلاء اللغة المرنة كرسوم بيانية. | [الرابط](https://github.com/langchain-ai/langgraph) |
| Agno | بناء وكلاء ذكاء اصطناعي مع ذاكرة ومعرفة وأدوات. | [الرابط](https://github.com/agno-agi/agno) |
| Agents SDK | بناء تطبيقات الوكلاء باستخدام نماذج اللغة الكبيرة. | [الرابط](https://platform.openai.com/docs/guides/agents-sdk) |
| AutoGen | إطار عمل مفتوح المصدر لبناء أنظمة الوكلاء. | [الرابط](https://github.com/microsoft/autogen) |
| Smolagents | مكتبة لبناء وكلاء قوية في سطور قليلة من الكود. | [الرابط](https://github.com/huggingface/smolagents) |
| Pydantic AI | إطار عمل وكلاء بايثون لبناء تطبيقات إنتاج. | [الرابط](https://ai.pydantic.dev/) |
| CAMEL | إطار عمل متعدد الوكلاء مفتوح المصدر. | [الرابط](https://github.com/camel-ai/camel) |
| BeeAI | بناء أنظمة متعددة الوكلاء جاهزة للإنتاج. | [الرابط](https://github.com/i-am-bee/beeai-framework/tree/main/python) |
| gradio-tools | تحويل تطبيقات Gradio إلى أدوات للوكلاء. | [الرابط](https://github.com/freddyaboulton/gradio-tools) |
| Composio | مجموعة أدوات جاهزة للإنتاج للوكلاء الذكية. | [الرابط](https://github.com/ComposioHQ/composio) |
| Atomic Agents | بناء الوكلاء الذكية بشكل ذري. | [الرابط](https://github.com/BrainBlend-AI/atomic-agents) |
| Memary | طبقة ذاكرة مفتوحة المصدر للوكلاء المستقلة. | [الرابط](https://github.com/kingjulio8238/Memary) |
| Browser Use | جعل مواقع الويب متاحة للوكلاء الذكية. | [الرابط](https://github.com/browser-use/browser-use) |
| OpenWebAgent | مجموعة أدوات مفتوحة لتمكين وكلاء الويب. | [الرابط](https://github.com/THUDM/OpenWebAgent/) |
| Lagent | إطار عمل خفيف الوزن لبناء الوكلاء. | [الرابط](https://github.com/InternLM/lagent) |
| LazyLLM | أداة تطوير منخفضة الكود لتطبيقات الوكلاء المتعددة. | [الرابط](https://github.com/LazyAGI/LazyLLM) |
| Swarms | إطار عمل تنسيق الوكلاء المتعددة على مستوى المؤسسات. | [الرابط](https://github.com/kyegomez/swarms) |
| ChatArena | بيئات ألعاب لغوية متعددة الوكلاء. | [الرابط](https://github.com/Farama-Foundation/chatarena) |
| Swarm | إطار عمل تعليمي لتنسيق الوكلاء المتعددة. | [الرابط](https://github.com/openai/swarm) |
| AgentStack | أسرع طريقة لبناء وكلاء ذكاء اصطناعي قوية. | [الرابط](https://github.com/AgentOps-AI/AgentStack) |
| Archgw | بوابة ذكية للوكلاء. | [الرابط](https://github.com/katanemo/archgw) |
| Flow | محرك مهام خفيف الوزن لبناء الوكلاء الذكية. | [الرابط](https://github.com/lmnr-ai/flow) |
| AgentOps | SDK بايثون لمراقبة الوكلاء الذكية. | [الرابط](https://github.com/AgentOps-AI/agentops) |
| Langroid | إطار عمل متعدد الوكلاء. | [الرابط](https://github.com/langroid/langroid) |
| Agentarium | إطار عمل لإنشاء وإدارة محاكاات الوكلاء الذكية. | [الرابط](https://github.com/Thytu/Agentarium) |
| Upsonic | إطار عمل موثوق للوكلاء يدعم MCP. | [الرابط](https://github.com/upsonic/upsonic) |

---

## التقييم

أدوات وأطر عمل لتقييم أداء نماذج اللغة الكبيرة.

| المكتبة | الوصف | الرابط |
|---------|-------|--------|
| Ragas | مجموعة أدوات شاملة لتقييم وتحسين تطبيقات نماذج اللغة الكبيرة. | [الرابط](https://github.com/explodinggradients/ragas) |
| Giskard | تقييم واختبار مفتوح المصدر لأنظمة التعلم الآلي ونماذج اللغة الكبيرة. | [الرابط](https://github.com/Giskard-AI/giskard) |
| DeepEval | إطار عمل تقييم نماذج اللغة الكبيرة | [الرابط](https://github.com/confident-ai/deepeval) |
| Lighteval | مجموعة أدوات شاملة لتقييم نماذج اللغة الكبيرة. | [الرابط](https://github.com/huggingface/lighteval) |
| Trulens | تقييم وتتبع تجارب نماذج اللغة الكبيرة | [الرابط](https://github.com/truera/trulens) |
| PromptBench | إطار عمل تقييم موحد لنماذج اللغة الكبيرة. | [الرابط](https://github.com/microsoft/promptbench) |
| LangTest | أكثر من 60 نوع اختبار لمقارنة نماذج اللغة الكبيرة والبرمجة اللغوية العصبية. | [الرابط](https://github.com/JohnSnowLabs/langtest) |
| EvalPlus | إطار عمل تقييم صارم لـ LLM4Code. | [الرابط](https://github.com/evalplus/evalplus) |
| FastChat | منصة مفتوحة لتدريب وخدمة وتقييم chatbots. | [الرابط](https://github.com/lm-sys/FastChat) |
| judges | مكتبة صغيرة من قضاة نماذج اللغة الكبيرة. | [الرابط](https://github.com/quotient-ai/judges) |
| Evals | إطار عمل لتقييم نماذج اللغة الكبيرة وسجل مفتوح للمعايير. | [الرابط](https://github.com/openai/evals) |
| AgentEvals | مُقيّمون وأدوات لتقييم أداء الوكلاء. | [الرابط](https://github.com/langchain-ai/agentevals) |
| LLMBox | مكتبة شاملة مع خط تدريب موحد وتقييم شامل. | [الرابط](https://github.com/RUCAIBox/LLMBox) |
| Opik | منصة تطوير شاملة تتضمن تقييم نماذج اللغة الكبيرة. | [الرابط](https://github.com/comet-ml/opik) |
| PydanticAI Evals | إطار عمل تقييم قوي لتطبيقات نماذج اللغة الكبيرة. | [الرابط](https://ai.pydantic.dev/evals/) |
| UQLM | حزمة بايثون لقياس الهلوسة في نماذج اللغة الكبيرة. | [الرابط](https://github.com/cvs-health/uqlm) |

---

## المراقبة

منصات وأدوات لمراقبة تطبيقات نماذج اللغة الكبيرة في الإنتاج.

| المكتبة | الوصف | الرابط |
|---------|-------|--------|
| MLflow | منصة MLOps/LLMOps شاملة لتتبع وتقييم ومراقبة التطبيقات. | [الرابط](https://github.com/mlflow/mlflow) |
| Opik | منصة تطوير شاملة تتضمن مراقبة نماذج اللغة الكبيرة. | [الرابط](https://github.com/comet-ml/opik) |
| LangSmith | أدوات للتسجيل والمراقبة وتحسين التطبيقات. | [الرابط](https://github.com/langchain-ai/langsmith-sdk) |
| Weights & Biases (W&B) | ميزات لتتبع أداء نماذج اللغة الكبيرة. | [الرابط](https://github.com/wandb) |
| Helicone | منصة مراقبة مفتوحة المصدر للمطورين. | [الرابط](https://github.com/Helicone/helicone) |
| Evidently | إطار عمل مراقبة مفتوح المصدر للتعلم الآلي ونماذج اللغة الكبيرة. | [الرابط](https://github.com/evidentlyai/evidently) |
| Phoenix | منصة مراقبة مفتوحة المصدر للتجريب والتقييم. | [الرابط](https://github.com/Arize-ai/phoenix) |
| Observers | مكتبة خفيفة الوزن لمراقبة الذكاء الاصطناعي. | [الرابط](https://github.com/cfahlgren1/observers) |

---

## القوالب

مكتبات لهندسة القوالب والتحسين والضغط.

| المكتبة | الوصف | الرابط |
|---------|-------|--------|
| PCToolkit | مجموعة أدوات موحدة لضغط القوالب. | [الرابط](https://github.com/3DAgentWorld/Toolkit-for-Prompt-Compression) |
| Selective Context | ضغط القوالب والسياق للسماح بمعالجة محتوى أكثر بمرتين. | [الرابط](https://pypi.org/project/selective-context/) |
| LLMLingua | مكتبة لضغط القوالب لتسريع الاستدلال. | [الرابط](https://github.com/microsoft/LLMLingua) |
| betterprompt | مجموعة اختبار للقوالب قبل نشرها للإنتاج. | [الرابط](https://github.com/stjordanis/betterprompt) |
| Promptify | حل مشاكل البرمجة اللغوية العصبية مع نماذج اللغة الكبيرة. | [الرابط](https://github.com/promptslab/Promptify) |
| PromptSource | مجموعة أدوات لإنشاء ومشاركة واستخدام القوالب. | [الرابط](https://pypi.org/project/promptsource/) |
| DSPy | إطار عمل مفتوح المصدر للبرمجة بدلاً من التوجيه. | [الرابط](https://github.com/stanfordnlp/dspy) |
| Py-priompt | مكتبة تصميم القوالب. | [الرابط](https://github.com/zenbase-ai/py-priompt) |
| Promptimizer | مكتبة تحسين القوالب. | [الرابط](https://github.com/hinthornw/promptimizer) |

---

## المخرجات المنظمة

مكتبات لتوليد مخرجات منظمة (JSON، المخططات) من نماذج اللغة الكبيرة.

| المكتبة | الوصف | الرابط |
|---------|-------|--------|
| Instructor | مكتبة بايثون للعمل مع المخرجات المنظمة من نماذج اللغة الكبيرة. | [الرابط](https://github.com/instructor-ai/instructor) |
| XGrammar | مكتبة مفتوحة المصدر للتوليد المنظم الفعال. | [الرابط](https://github.com/mlc-ai/xgrammar) |
| Outlines | توليد نصوص قوية ومنظمة | [الرابط](https://github.com/dottxt-ai/outlines) |
| Guidance | نموذج برمجة فعال لتوجيه نماذج اللغة. | [الرابط](https://github.com/guidance-ai/guidance) |
| LMQL | لغة لبرمجة نماذج اللغة الكبيرة بقيود. | [الرابط](https://github.com/eth-sri/lmql) |
| Jsonformer | طريقة آمنة لتوليد JSON منظم من نماذج اللغة. | [الرابط](https://github.com/1rgs/jsonformer) |

---

## الأمان والسلامة

أدوات لتأمين تطبيقات نماذج اللغة الكبيرة ومنع الهجمات.

| المكتبة | الوصف | الرابط |
|---------|-------|--------|
| JailbreakEval | مجموعة مُقيّمين آليين لتقييم محاولات الاختراق. | [الرابط](https://github.com/ThuCCSLab/JailbreakEval) |
| EasyJailbreak | إطار عمل سهل الاستخدام لتوليد قوالب اختراق معادية. | [الرابط](https://github.com/EasyJailbreak/EasyJailbreak) |
| Guardrails | إضافة حواجز حماية لنماذج اللغة الكبيرة. | [الرابط](https://github.com/guardrails-ai/guardrails) |
| LLM Guard | مجموعة أدوات الأمان لتفاعلات نماذج اللغة الكبيرة. | [الرابط](https://github.com/protectai/llm-guard) |
| AuditNLG | مكتبة مفتوحة المصدر للحد من مخاطر أنظمة الذكاء التوليدي. | [الرابط](https://github.com/salesforce/AuditNLG) |
| NeMo Guardrails | مجموعة أدوات مفتوحة لإضافة حواجز حماية قابلة للبرمجة. | [الرابط](https://github.com/NVIDIA/NeMo-Guardrails) |
| Garak | ماسح الثغرات لنماذج اللغة الكبيرة | [الرابط](https://github.com/NVIDIA/garak) |
| DeepTeam | إطار عمل اختبار الفريق الأحمر لنماذج اللغة الكبيرة | [الرابط](https://github.com/confident-ai/deepteam) |

---

## نماذج التضمين

مكتبات لتوليد والعمل مع تضمينات النصوص.

| المكتبة | الوصف | الرابط |
|---------|-------|--------|
| Sentence-Transformers | تضمينات نصية متطورة | [الرابط](https://github.com/UKPLab/sentence-transformers) |
| Model2Vec | تضمينات ثابتة متطورة وسريعة | [الرابط](https://github.com/MinishLab/model2vec) |
| Text Embedding Inference | حل استدلال سريع لنماذج تضمين النصوص. | [الرابط](https://github.com/huggingface/text-embeddings-inference) |

---

## مكتبات أخرى

مكتبات إضافية مفيدة لتطوير نماذج اللغة الكبيرة.

| المكتبة | الوصف | الرابط |
|---------|-------|--------|
| Text Machina | إطار عمل معياري وقابل للتوسع لإنشاء مجموعات بيانات عالية الجودة. | [الرابط](https://github.com/Genaios/TextMachina) |
| LLM Reasoners | مكتبة للاستدلال المتقدم لنماذج اللغة الكبيرة. | [الرابط](https://github.com/maitrix-org/llm-reasoners) |
| EasyEdit | إطار عمل سهل الاستخدام لتحرير المعرفة. | [الرابط](https://github.com/zjunlp/EasyEdit) |
| CodeTF | مكتبة محول شاملة لنماذج اللغة الكبيرة للكود. | [الرابط](https://github.com/salesforce/CodeTF) |
| spacy-llm | دمج نماذج اللغة الكبيرة في spaCy. | [الرابط](https://github.com/explosion/spacy-llm) |
| pandas-ai | الدردشة مع قواعد البيانات (SQL، CSV، pandas). | [الرابط](https://github.com/Sinaptik-AI/pandas-ai) |
| LLM Transparency Tool | مجموعة أدوات تفاعلية لتحليل نماذج اللغة المحولة. | [الرابط](https://github.com/facebookresearch/llm-transparency-tool) |
| Vanna | الدردشة مع قاعدة بيانات SQL. توليد دقيق من النص إلى SQL. | [الرابط](https://github.com/vanna-ai/vanna) |
| mergekit | أدوات لدمج نماذج اللغة الكبيرة المدربة مسبقاً. | [الرابط](https://github.com/arcee-ai/MergeKit) |
| MarkLLM | مجموعة أدوات مفتوحة المصدر للعلامات المائية. | [الرابط](https://github.com/THU-BPM/MarkLLM) |
| LLMSanitize | مكتبة مفتوحة المصدر لكشف التلوث في مجموعات البيانات. | [الرابط](https://github.com/ntunlp/LLMSanitize) |
| Annotateai | وضع تعليقات توضيحية تلقائية على الأوراق البحثية. | [الرابط](https://github.com/neuml/annotateai) |
| LLM Reasoner | جعل أي نموذج لغة كبير يفكر مثل OpenAI o1 و DeepSeek R1. | [الرابط](https://github.com/harishsg993010/LLM-Reasoner) |

---

## موارد إضافية

للحصول على أدلة شاملة حول بناء تطبيقات RAG، راجع:
- [دليل RAG من الصفر إلى الاحتراف](https://github.com/KalyanKS-NLP/rag-zero-to-hero-guide) - دليل شامل لتعلم RAG من الأساسيات إلى المستوى المتقدم

ابق على اطلاع بأحدث التطورات في تطوير نماذج اللغة الكبيرة:
- [نشرة AIxFunda](https://aixfunda.substack.com/) - تحديثات أسبوعية للذكاء التوليدي ومراجعات أوراق بحثية ودروس جديدة

---

## إسناد المصدر

تم الحصول على هذا الدليل الشامل من مستودع [LLM Engineer Toolkit](https://github.com/KalyanKS-NLP/llm-engineer-toolkit) الممتاز الذي أنشأه **Kalyan KS** (أكثر من 8,000 نجمة و 1,300 شوكة).

**المنسق الأصلي:** Kalyan KS
- لينكد إن: [kalyanksnlp](https://www.linkedin.com/in/kalyanksnlp/)
- تويتر: [@kalyan_kpl](https://x.com/kalyan_kpl)
- يوتيوب: [kalyanksnlp](https://www.youtube.com/@kalyanksnlp)

---

## الترخيص

المحتوى مصدره من [LLM Engineer Toolkit](https://github.com/KalyanKS-NLP/llm-engineer-toolkit) بموجب ترخيص Apache-2.0.

---

**آخر تحديث:** 2 نوفمبر 2025

</div>
