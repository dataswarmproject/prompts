# AI Best Practices - Advanced Guide

**Master the art of working with AI to maximize productivity, accuracy, and value.**

## Table of Contents

1. [Prompt Engineering Mastery](#prompt-engineering-mastery)
2. [Context Management](#context-management)
3. [Token Optimization](#token-optimization)
4. [Chain of Thought Techniques](#chain-of-thought-techniques)
5. [Multi-Turn Conversations](#multi-turn-conversations)
6. [Security & Privacy](#security-and-privacy)
7. [Cost Management](#cost-management)
8. [Model Selection](#model-selection)
9. [Testing & Validation](#testing-and-validation)
10. [Advanced Techniques](#advanced-techniques)

---

## Prompt Engineering Mastery

### The SCRIBE Framework

Use this framework for consistently excellent results:

- **S**pecific: Be precise about what you want
- **C**ontext: Provide relevant background information
- **R**ole: Assign the AI an expert role
- **I**nstructions: Give clear, step-by-step directions
- **B**oundaries: Set constraints and limitations
- **E**xamples: Show desired output format

#### Example:

```
You are a senior Python developer specializing in API design.

Context: I'm building a REST API for a e-commerce platform that handles 10K requests/second.

Task: Review this endpoint code and suggest optimizations for performance and security.

Requirements:
- Focus on database query optimization
- Ensure proper authentication handling
- Include caching strategies
- Keep response time under 100ms

Please provide:
1. Specific issues found
2. Code suggestions with explanations
3. Performance impact estimates

[Your code here]
```

### Advanced Prompting Techniques

#### 1. Few-Shot Learning

Provide examples to guide the AI's output:

```
Convert these natural language queries to SQL:

Example 1:
Input: "Show me all customers who bought in the last month"
Output: SELECT * FROM customers WHERE last_purchase_date >= DATE_SUB(NOW(), INTERVAL 1 MONTH);

Example 2:
Input: "Find products under $50 sorted by rating"
Output: SELECT * FROM products WHERE price < 50 ORDER BY rating DESC;

Now convert: "Get top 10 sellers with revenue over 100k"
```

#### 2. Chain of Thought (CoT)

Ask the AI to think step-by-step:

```
Let's solve this problem step by step:

Problem: [Your complex problem]

Please:
1. Break down the problem into components
2. Analyze each component
3. Show your reasoning at each step
4. Provide the final solution with explanation
```

#### 3. Self-Consistency

Get multiple solutions and choose the best:

```
Please provide 3 different approaches to solve [problem]:

Approach 1: [Most efficient]
Approach 2: [Most maintainable]
Approach 3: [Most scalable]

For each approach, explain:
- Implementation steps
- Pros and cons
- Best use cases
```

#### 4. Tree of Thoughts

Explore multiple reasoning paths:

```
Let's explore different solutions:

Path A: [Conservative approach]
- Pros:
- Cons:
- Next steps:

Path B: [Innovative approach]
- Pros:
- Cons:
- Next steps:

Path C: [Hybrid approach]
- Pros:
- Cons:
- Next steps:

Recommendation: Based on [criteria], choose Path X because...
```

---

## Context Management

### Providing Effective Context

**DO:**
- Include relevant code, documentation, or background
- Specify your tech stack, environment, constraints
- Mention previous attempts and why they failed
- Share error messages in full
- Describe your expertise level

**DON'T:**
- Dump entire codebases without focus
- Omit critical environment details
- Assume the AI knows your project
- Include sensitive data or credentials

### Context Optimization

```
# Good Context Structure

## Background
[Brief project overview]

## Current Situation
[What's working, what's not]

## Technical Environment
- Language: Python 3.11
- Framework: FastAPI
- Database: PostgreSQL 14
- Hosting: AWS Lambda

## Specific Issue
[Detailed problem description]

## What I've Tried
1. [Attempt 1 - Result]
2. [Attempt 2 - Result]

## Goal
[Specific desired outcome]
```

---

## Token Optimization

### Reducing Token Usage

1. **Be Concise**: Remove unnecessary words
   - ❌ "I would really appreciate it if you could help me understand..."
   - ✅ "Explain how..."

2. **Use Markdown Efficiently**: Structure saves tokens
   ```
   # Main Task
   ## Subtask 1
   - Requirement A
   - Requirement B
   ```

3. **Reference Previous Context**:
   - ❌ Re-pasting entire code blocks
   - ✅ "Referring to the function we discussed earlier..."

4. **Strategic Code Sharing**:
   - Share only relevant sections
   - Use line numbers for large files
   - Summarize unchanged parts

### Token Budgeting

For 200K token contexts:
- **Context**: 50-100K tokens (code, docs, background)
- **Conversation**: 50-100K tokens (back-and-forth)
- **Responses**: Reserve 20-40K for detailed outputs
- **Buffer**: Keep 10-20K for safety

---

## Chain of Thought Techniques

### Zero-Shot CoT

```
Question: [Complex problem]

Let's think through this step by step:

Step 1: [First consideration]
Step 2: [Build on previous step]
Step 3: [Continue reasoning]

Conclusion: [Final answer with justification]
```

### Structured Reasoning

```
Problem: [Issue description]

Analysis:
1. Root Cause: [Identify core issue]
2. Dependencies: [What else is affected]
3. Constraints: [Limitations to consider]
4. Options: [Possible solutions]
5. Recommendation: [Best solution with reasoning]
```

---

## Multi-Turn Conversations

### Effective Dialogue Patterns

#### 1. Progressive Refinement

```
Turn 1: "Create a user authentication system"
Turn 2: "Add OAuth2 support"
Turn 3: "Include rate limiting"
Turn 4: "Add comprehensive error handling"
```

#### 2. Building on Context

```
Turn 1: "Show me the bug in this function"
Turn 2: "Fix it while maintaining backward compatibility"
Turn 3: "Add unit tests for the fix"
Turn 4: "Document the changes"
```

#### 3. Iterative Improvement

```
Turn 1: "Draft a proposal for X"
Turn 2: "Make it more technical and data-driven"
Turn 3: "Add cost-benefit analysis"
Turn 4: "Format for executive presentation"
```

### Maintaining Context

- Reference previous turns: "As you mentioned earlier..."
- Use consistent terminology
- Build incrementally rather than starting over
- Summarize when context gets large

---

## Security and Privacy

### Never Share

- ❌ API keys, tokens, passwords
- ❌ Private keys or certificates
- ❌ Customer data or PII
- ❌ Proprietary algorithms
- ❌ Internal system architecture details
- ❌ Database connection strings

### Safe Practices

✅ Use placeholders: `API_KEY="your_key_here"`
✅ Anonymize data: Replace real names with "User A", "User B"
✅ Remove sensitive URLs: Use "example.com"
✅ Generalize: Share patterns, not actual credentials
✅ Use example data: Synthetic datasets for testing

### Code Review for Sensitive Data

Before sharing code:
1. Search for "password", "key", "token", "secret"
2. Check environment variables
3. Review configuration files
4. Scan for email addresses
5. Look for internal URLs

---

## Cost Management

### API Usage Optimization

1. **Batch Requests**: Combine multiple questions
2. **Shorter Prompts**: Be concise but clear
3. **Efficient Context**: Share only what's needed
4. **Right Model for Job**: Use smaller models for simple tasks

### Cost-Effective Patterns

| Task | Recommended Model | Why |
|------|------------------|-----|
| Code generation | Claude 3.5 Sonnet | Best code quality |
| Simple Q&A | GPT-3.5 / Haiku | Lower cost, fast |
| Complex reasoning | GPT-4 / Opus | Worth the quality |
| Bulk processing | Haiku | High volume |
| Image analysis | Claude 3.5 Sonnet | Multimodal capability |

### Monitoring Costs

```python
# Track token usage
from anthropic import Anthropic

client = Anthropic(api_key="your_key")

response = client.messages.create(
    model="claude-3-5-sonnet-20241022",
    max_tokens=1024,
    messages=[{"role": "user", "content": "Hello"}]
)

print(f"Input tokens: {response.usage.input_tokens}")
print(f"Output tokens: {response.usage.output_tokens}")
```

---

## Model Selection

### Model Comparison

| Model | Best For | Strengths | Weaknesses |
|-------|----------|-----------|------------|
| Claude 3.5 Sonnet | Code, analysis, long context | Superior coding, 200K context | Higher cost |
| Claude 3 Opus | Complex reasoning | Best overall quality | Most expensive |
| Claude 3 Haiku | Speed, volume | Very fast, low cost | Less nuanced |
| GPT-4 Turbo | General purpose | Great quality | Shorter context |
| GPT-3.5 Turbo | Simple tasks | Very cheap, fast | Limited reasoning |

### When to Use Which Model

**Claude 3.5 Sonnet**:
- Software development
- Code reviews and refactoring
- Technical documentation
- Complex analysis with large codebases

**Claude 3 Opus**:
- Strategic planning
- Research synthesis
- Creative writing
- Complex problem-solving

**Claude 3 Haiku**:
- Data processing
- Simple Q&A
- Content moderation
- High-volume operations

**GPT-4**:
- General knowledge questions
- Creative tasks
- Balanced performance/cost

**GPT-3.5**:
- Simple translations
- Basic text processing
- High-volume cheap operations

---

## Testing and Validation

### Prompt Testing Framework

1. **Define Success Criteria**
   ```
   Test: Code Generation
   Success:
   - Compiles without errors
   - Passes all test cases
   - Follows style guide
   - Includes error handling
   ```

2. **Create Test Cases**
   ```
   Test Case 1: Simple input
   Test Case 2: Edge case
   Test Case 3: Invalid input
   Test Case 4: Complex scenario
   ```

3. **Validate Outputs**
   - Check factual accuracy
   - Verify code functionality
   - Test edge cases
   - Confirm security practices

### A/B Testing Prompts

```python
prompt_a = "Write a function to sort a list"
prompt_b = "Create a Python function that takes a list and returns it sorted in ascending order. Include type hints and docstring."

# Test both and compare:
# - Accuracy
# - Completeness
# - Code quality
# - Performance
```

---

## Advanced Techniques

### 1. Meta-Prompting

Ask the AI to help craft better prompts:

```
I need to ask an AI to help me with [task].
Can you help me craft an effective prompt that includes:
- Proper context
- Clear instructions
- Expected output format
- Any constraints

Here's what I'm trying to accomplish: [goal]
```

### 2. Role-Based Prompting

```
You are a [specific expert role] with [specific expertise].

Your task is to [specific action] considering:
- [Domain-specific constraint 1]
- [Domain-specific constraint 2]
- [Domain-specific constraint 3]

Approach this from the perspective of someone who [expert mindset].
```

### 3. Constrained Generation

```
Generate [output] with these strict constraints:
- Max length: 100 words
- Must include: [required elements]
- Must avoid: [forbidden elements]
- Format: [specific structure]
- Tone: [professional/casual/technical]
```

### 4. Comparative Analysis

```
Compare these 3 approaches to [problem]:

Approach A: [Option 1]
Approach B: [Option 2]
Approach C: [Option 3]

For each, analyze:
- Performance implications
- Scalability
- Maintenance burden
- Cost
- Security

Provide a recommendation matrix based on different priorities.
```

### 5. Iterative Refinement Pattern

```
Version 1: [Initial attempt]
Issues with V1: [Problems identified]

Version 2: [Improved attempt]
Issues with V2: [Remaining problems]

Version 3: [Final attempt]
Why this works: [Explanation]
```

---

## Common Pitfalls to Avoid

### ❌ Vague Requests
"Make this better" → "Optimize for O(n log n) performance and add error handling"

### ❌ Assuming Context
"Fix the bug" → "Fix the null pointer exception in line 42 of user_service.py"

### ❌ Multiple Unrelated Tasks
"Do A, B, C, D, E" → Break into separate focused requests

### ❌ Ignoring Output
Not reviewing or testing AI-generated code or content

### ❌ Over-Reliance
Using AI without understanding the solutions provided

---

## Checklists

### Before Asking

- [ ] Is my question specific and clear?
- [ ] Have I provided necessary context?
- [ ] Have I removed sensitive information?
- [ ] Have I specified the desired output format?
- [ ] Have I mentioned relevant constraints?

### After Receiving Response

- [ ] Does it answer my actual question?
- [ ] Is the solution appropriate for my use case?
- [ ] Have I tested the code/solution?
- [ ] Do I understand how it works?
- [ ] Is it production-ready or does it need refinement?

---

## Resources

### Further Reading

- [Anthropic Prompt Engineering Guide](https://docs.anthropic.com/claude/docs/prompt-engineering)
- [OpenAI Best Practices](https://platform.openai.com/docs/guides/prompt-engineering)
- [Prompt Engineering Guide](https://www.promptingguide.ai/)

### Tools

- Claude Code (CLI)
- ChatGPT Web Interface
- API Playgrounds
- Prompt testing frameworks

---

**Last Updated**: 2025-10-28

**Remember**: AI is a tool to augment your expertise, not replace it. Always review, understand, and test AI-generated content before using it in production.
