# AI Workflows Gallery

**Curator: Dr. Ahmed Halloub**

Pre-built automation workflows and pipelines for common AI tasks. Copy, customize, and deploy these proven patterns.

---

## Table of Contents

- [Research Workflows](#research-workflows)
- [Content Creation](#content-creation)
- [Data Analysis](#data-analysis)
- [Software Development](#software-development)
- [Business Automation](#business-automation)
- [Multi-Agent Workflows](#multi-agent-workflows)

---

## Research Workflows

### 1. Academic Paper Summarization Pipeline

**Purpose:** Analyze multiple research papers and generate comprehensive summary

**Workflow:**
```
PDF Upload → Text Extraction → Chunking → Summarization → Synthesis → Report
```

**Implementation:**
```python
from pypdf import PdfReader
from langchain.text_splitter import RecursiveCharacterTextSplitter

class PaperAnalysisPipeline:
    def __init__(self):
        self.splitter = RecursiveCharacterTextSplitter(
            chunk_size=4000,
            chunk_overlap=200
        )

    def process_paper(self, pdf_path):
        # 1. Extract text
        text = self.extract_text(pdf_path)

        # 2. Chunk for processing
        chunks = self.splitter.split_text(text)

        # 3. Summarize each section
        summaries = [self.summarize_chunk(chunk) for chunk in chunks]

        # 4. Synthesize overall summary
        synthesis = self.synthesize(summaries)

        return {
            'title': self.extract_title(text),
            'authors': self.extract_authors(text),
            'summary': synthesis,
            'key_findings': self.extract_findings(synthesis),
            'methodology': self.extract_methodology(text)
        }

    def extract_text(self, pdf_path):
        reader = PdfReader(pdf_path)
        return "\n".join([page.extract_text() for page in reader.pages])

    def summarize_chunk(self, chunk):
        prompt = f"""
        Summarize the following section of a research paper:

        {chunk}

        Focus on: methodology, findings, and conclusions.
        """
        return get_completion(prompt)

    def synthesize(self, summaries):
        prompt = f"""
        Synthesize these section summaries into a coherent overview:

        {chr(10).join(summaries)}

        Provide: 1) Main contribution, 2) Methods, 3) Results, 4) Limitations
        """
        return get_completion(prompt)
```

**Usage:**
```python
pipeline = PaperAnalysisPipeline()
result = pipeline.process_paper("research_paper.pdf")
print(result['summary'])
```

---

### 2. Literature Review Automation

**Purpose:** Search, analyze, and synthesize findings from multiple papers

**Workflow:**
```
Query → Search Papers → Filter Relevant → Analyze Each → Compare Findings → Generate Review
```

**Implementation:**
```python
class LiteratureReviewWorkflow:
    def __init__(self):
        self.papers = []

    def run_review(self, topic, max_papers=20):
        # 1. Search for papers
        paper_ids = self.search_papers(topic, max_papers)

        # 2. Analyze each paper
        analyses = []
        for paper_id in paper_ids:
            analysis = self.analyze_paper(paper_id)
            if analysis['relevance_score'] > 0.7:
                analyses.append(analysis)

        # 3. Identify themes
        themes = self.identify_themes(analyses)

        # 4. Generate review
        review = self.generate_review(analyses, themes)

        return review

    def analyze_paper(self, paper_id):
        content = self.fetch_paper(paper_id)

        prompt = f"""
        Analyze this paper for a literature review on {self.topic}:

        {content}

        Extract:
        - Main contribution
        - Methods used
        - Key findings
        - Relevance to topic (0-1 score)
        - Limitations
        """

        return parse_analysis(get_completion(prompt))

    def identify_themes(self, analyses):
        findings = [a['findings'] for a in analyses]

        prompt = f"""
        Identify common themes across these research findings:

        {chr(10).join(findings)}

        List 5-7 major themes with supporting evidence.
        """

        return get_completion(prompt)
```

---

## Content Creation

### 3. Blog Post Generation Pipeline

**Purpose:** Create SEO-optimized blog posts from brief

**Workflow:**
```
Brief → Research → Outline → Draft → SEO Optimize → Edit → Format → Publish
```

**Implementation:**
```python
class BlogPostPipeline:
    def __init__(self, topic, keywords):
        self.topic = topic
        self.keywords = keywords

    def generate_post(self):
        # 1. Research topic
        research = self.research_topic()

        # 2. Create outline
        outline = self.create_outline(research)

        # 3. Write sections
        sections = self.write_sections(outline)

        # 4. Optimize for SEO
        optimized = self.seo_optimize(sections)

        # 5. Format for platform
        formatted = self.format_post(optimized)

        return formatted

    def research_topic(self):
        prompt = f"""
        Research the topic: {self.topic}

        Find:
        - Current trends
        - Common questions
        - Expert insights
        - Statistics

        Keywords to include: {', '.join(self.keywords)}
        """
        return get_completion(prompt)

    def create_outline(self, research):
        prompt = f"""
        Create a blog post outline for: {self.topic}

        Based on this research:
        {research}

        Include:
        - Attention-grabbing title
        - Introduction hook
        - 5-7 main sections
        - Conclusion with CTA

        Optimize for keywords: {', '.join(self.keywords)}
        """
        return get_completion(prompt)

    def write_sections(self, outline):
        sections = {}
        for section in parse_outline(outline):
            prompt = f"""
            Write a {section['type']} section for:
            {section['title']}

            Context: {section['context']}
            Length: {section['word_count']} words
            Tone: {self.tone}

            Include keywords naturally: {', '.join(self.keywords)}
            """
            sections[section['title']] = get_completion(prompt)

        return sections

    def seo_optimize(self, sections):
        full_text = "\n\n".join(sections.values())

        prompt = f"""
        Optimize this blog post for SEO:

        {full_text}

        Tasks:
        1. Add meta description (155 chars)
        2. Ensure keyword density 1-2%
        3. Add internal linking suggestions
        4. Suggest image alt texts
        5. Check readability (Flesch score > 60)

        Primary keyword: {self.keywords[0]}
        """

        return get_completion(prompt)
```

---

### 4. Social Media Content Pipeline

**Purpose:** Create multi-platform social content from single source

**Workflow:**
```
Source Content → Platform Adaptation → Image Generation → Scheduling
```

**Implementation:**
```python
class SocialMediaWorkflow:
    def __init__(self, source_content):
        self.source = source_content
        self.platforms = ['twitter', 'linkedin', 'instagram']

    def generate_all(self):
        results = {}

        for platform in self.platforms:
            results[platform] = self.adapt_for_platform(platform)

        return results

    def adapt_for_platform(self, platform):
        specs = {
            'twitter': {'max_length': 280, 'tone': 'casual', 'hashtags': 2},
            'linkedin': {'max_length': 1300, 'tone': 'professional', 'hashtags': 3},
            'instagram': {'max_length': 2200, 'tone': 'engaging', 'hashtags': 15}
        }

        spec = specs[platform]

        prompt = f"""
        Adapt this content for {platform}:

        {self.source}

        Requirements:
        - Max length: {spec['max_length']} characters
        - Tone: {spec['tone']}
        - Include {spec['hashtags']} relevant hashtags
        - Add emoji if appropriate for platform
        - Include call-to-action

        Format: Ready to post
        """

        post = get_completion(prompt)

        # Generate accompanying image
        image_prompt = self.generate_image_prompt(post, platform)

        return {
            'text': post,
            'image_prompt': image_prompt,
            'hashtags': extract_hashtags(post),
            'best_time': self.get_best_posting_time(platform)
        }
```

---

## Data Analysis

### 5. Automated Data Analysis Pipeline

**Purpose:** Upload data, get insights, visualizations, and report

**Workflow:**
```
Upload CSV → Clean Data → Analyze → Visualize → Generate Report
```

**Implementation:**
```python
import pandas as pd
import matplotlib.pyplot as plt

class DataAnalysisPipeline:
    def __init__(self, data_path):
        self.df = pd.read_csv(data_path)

    def run_analysis(self):
        # 1. Clean data
        self.clean_data()

        # 2. Get AI insights
        insights = self.get_insights()

        # 3. Create visualizations
        charts = self.create_visualizations()

        # 4. Generate report
        report = self.generate_report(insights, charts)

        return report

    def get_insights(self):
        # Get data summary
        summary = {
            'shape': self.df.shape,
            'columns': list(self.df.columns),
            'dtypes': self.df.dtypes.to_dict(),
            'missing': self.df.isnull().sum().to_dict(),
            'stats': self.df.describe().to_dict()
        }

        prompt = f"""
        Analyze this dataset:

        {summary}

        Sample data:
        {self.df.head(10).to_string()}

        Provide:
        1. Key patterns and trends
        2. Anomalies or outliers
        3. Correlations
        4. Recommended visualizations
        5. Business insights
        """

        return get_completion(prompt)

    def create_visualizations(self):
        # Let AI suggest charts
        prompt = f"""
        Suggest 3-5 matplotlib visualization scripts for this data:

        Columns: {list(self.df.columns)}
        Data types: {self.df.dtypes.to_dict()}

        Provide complete Python code using matplotlib.
        """

        code = get_completion(prompt)

        # Execute code to generate charts
        exec(code)

        return "charts_generated"

    def generate_report(self, insights, charts):
        prompt = f"""
        Create an executive summary report based on:

        Insights: {insights}

        Include:
        - Executive Summary
        - Key Findings
        - Recommendations
        - Next Steps

        Format: Professional business report
        """

        return get_completion(prompt)
```

---

## Software Development

### 6. Code Review Automation

**Purpose:** Automated PR review with feedback

**Workflow:**
```
PR Created → Fetch Changes → Analyze Code → Security Check → Performance Review → Generate Comments
```

**Implementation:**
```python
class CodeReviewWorkflow:
    def __init__(self, pr_diff):
        self.diff = pr_diff

    def review(self):
        reviews = {
            'code_quality': self.check_quality(),
            'security': self.check_security(),
            'performance': self.check_performance(),
            'tests': self.check_tests(),
            'documentation': self.check_docs()
        }

        summary = self.generate_summary(reviews)

        return {
            'reviews': reviews,
            'summary': summary,
            'approved': self.should_approve(reviews)
        }

    def check_quality(self):
        prompt = f"""
        Review this code for quality issues:

        {self.diff}

        Check for:
        - Code style violations
        - Naming conventions
        - Code complexity
        - Duplication
        - Best practices

        Provide specific line feedback.
        """

        return get_completion(prompt)

    def check_security(self):
        prompt = f"""
        Security review for:

        {self.diff}

        Check for:
        - SQL injection risks
        - XSS vulnerabilities
        - Hardcoded secrets
        - Authentication issues
        - Input validation

        Rate risk level (Low/Medium/High) for each finding.
        """

        return get_completion(prompt)
```

---

### 7. Documentation Generation

**Purpose:** Auto-generate docs from codebase

**Workflow:**
```
Parse Code → Extract Functions/Classes → Generate Docs → Create Examples → Build Site
```

**Implementation:**
```python
import ast

class DocGenerationWorkflow:
    def __init__(self, source_dir):
        self.source_dir = source_dir

    def generate_docs(self):
        # 1. Parse all Python files
        modules = self.parse_directory()

        # 2. Generate docs for each module
        docs = {}
        for module_name, module_ast in modules.items():
            docs[module_name] = self.document_module(module_ast)

        # 3. Create index
        index = self.create_index(docs)

        # 4. Generate examples
        examples = self.generate_examples(docs)

        return {
            'docs': docs,
            'index': index,
            'examples': examples
        }

    def document_module(self, module_ast):
        functions = [node for node in ast.walk(module_ast)
                    if isinstance(node, ast.FunctionDef)]
        classes = [node for node in ast.walk(module_ast)
                  if isinstance(node, ast.ClassDef)]

        docs = []
        for func in functions:
            docs.append(self.document_function(func))

        for cls in classes:
            docs.append(self.document_class(cls))

        return docs

    def document_function(self, func_node):
        source = ast.unparse(func_node)

        prompt = f"""
        Generate documentation for this function:

        {source}

        Include:
        - Description
        - Parameters (with types)
        - Return value
        - Example usage
        - Notes/warnings

        Format: Markdown
        """

        return get_completion(prompt)
```

---

## Business Automation

### 8. Email Response Automation

**Purpose:** Categorize and draft responses to customer emails

**Workflow:**
```
Receive Email → Classify → Extract Intent → Draft Response → Human Review → Send
```

**Implementation:**
```python
class EmailAutomationWorkflow:
    def __init__(self):
        self.categories = [
            'technical_support',
            'billing',
            'feature_request',
            'complaint',
            'general_inquiry'
        ]

    def process_email(self, email_content, sender):
        # 1. Classify
        category = self.classify(email_content)

        # 2. Extract key info
        extracted = self.extract_info(email_content, category)

        # 3. Fetch relevant context
        context = self.get_context(category, extracted)

        # 4. Draft response
        draft = self.draft_response(email_content, category, context)

        # 5. Estimate confidence
        confidence = self.estimate_confidence(draft)

        return {
            'category': category,
            'draft': draft,
            'confidence': confidence,
            'requires_review': confidence < 0.8,
            'suggested_agent': self.route_to_agent(category)
        }

    def classify(self, email):
        prompt = f"""
        Classify this email into one category:
        {', '.join(self.categories)}

        Email:
        {email}

        Output: category name only
        """

        return get_completion(prompt).strip()

    def draft_response(self, email, category, context):
        prompt = f"""
        Draft a professional response to this {category} email:

        Customer Email:
        {email}

        Context/Info:
        {context}

        Requirements:
        - Professional and empathetic tone
        - Address all concerns
        - Provide actionable steps
        - Include relevant links/resources
        - Sign off appropriately
        """

        return get_completion(prompt)
```

---

## Multi-Agent Workflows

### 9. Research & Report Generation Team

**Purpose:** Multiple AI agents collaborate on comprehensive report

**Workflow:**
```
Task Assignment → Parallel Research → Synthesis → Review → Final Report
```

**Implementation:**
```python
from crewai import Agent, Task, Crew

class ReportGenerationCrew:
    def __init__(self, topic):
        self.topic = topic

        # Define agents
        self.researcher = Agent(
            role="Researcher",
            goal=f"Research comprehensive information about {topic}",
            backstory="Expert researcher with access to multiple sources"
        )

        self.analyst = Agent(
            role="Data Analyst",
            goal="Analyze research and extract insights",
            backstory="Experienced analyst skilled at pattern recognition"
        )

        self.writer = Agent(
            role="Technical Writer",
            goal="Create clear, engaging report",
            backstory="Professional writer with technical expertise"
        )

    def generate_report(self):
        # Define tasks
        research_task = Task(
            description=f"Research {self.topic} from multiple angles",
            agent=self.researcher
        )

        analysis_task = Task(
            description="Analyze research and identify key insights",
            agent=self.analyst
        )

        writing_task = Task(
            description="Write comprehensive report with findings",
            agent=self.writer
        )

        # Create crew
        crew = Crew(
            agents=[self.researcher, self.analyst, self.writer],
            tasks=[research_task, analysis_task, writing_task]
        )

        # Execute
        result = crew.kickoff()

        return result
```

---

## Workflow Templates

### Template: Generic Pipeline

```python
class GenericPipeline:
    def __init__(self):
        self.steps = []

    def add_step(self, name, function):
        self.steps.append((name, function))

    def run(self, initial_input):
        result = initial_input

        for name, function in self.steps:
            print(f"Running: {name}")
            result = function(result)

        return result

# Usage
pipeline = GenericPipeline()
pipeline.add_step("extract", extract_text)
pipeline.add_step("analyze", analyze_content)
pipeline.add_step("summarize", create_summary)

output = pipeline.run(input_data)
```

---

**Ready to use these workflows?** Copy the code, customize for your needs, and integrate into your applications.

**Related Resources:**
- [Use Cases Library](./USE-CASES-LIBRARY.md)
- [AI Agents Frameworks](./AI-AGENTS-FRAMEWORKS.md)
- [Code Examples](../AI-BEST-PRACTICES.md)
