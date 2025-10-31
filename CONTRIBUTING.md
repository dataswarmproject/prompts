# Contributing Guide

**Curator: Dr. Ahmed Halloub**

Thank you for your interest in contributing to the AI Resources Hub! This guide will help you contribute effectively.

---

## Table of Contents

- [Ways to Contribute](#ways-to-contribute)
- [Contribution Guidelines](#contribution-guidelines)
- [How to Submit](#how-to-submit)
- [Code of Conduct](#code-of-conduct)
- [Review Process](#review-process)

---

## Ways to Contribute

### 1. Suggest New Tools

**What we're looking for:**
- Production-ready AI tools
- Free or freemium options
- Well-documented tools
- Active maintenance
- Unique value proposition

**How to suggest:**
1. Check if tool already exists
2. Verify it's actively maintained
3. Test the tool yourself
4. Submit via GitHub Issue with template

**Template:**
```markdown
**Tool Name:**
**Category:** (e.g., Image Generation, Code Assistant)
**Description:** (2-3 sentences)
**Link:**
**Pricing:**
**Key Features:**
- Feature 1
- Feature 2
**Why it's valuable:**
```

---

### 2. Report Outdated Information

**Help us keep content current:**
- Pricing changes
- Deprecated features
- Broken links
- Outdated benchmarks
- New model versions

**How to report:**
- Create GitHub Issue
- Specify exact location (file, section)
- Provide correct information
- Include source/reference

---

### 3. Submit Use Cases

**Share your implementations:**
- Real-world applications
- Industry-specific solutions
- Workflow automations
- Cost optimization strategies
- Performance improvements

**Requirements:**
- Practical and tested
- Clear description
- Measurable results
- Code examples (if applicable)
- No proprietary/confidential info

---

### 4. Improve Documentation

**Ways to help:**
- Fix typos and grammar
- Clarify confusing sections
- Add missing explanations
- Improve code examples
- Enhance tables/charts

**Guidelines:**
- Maintain professional tone
- No emojis
- Use proper markdown
- Follow existing style
- Test code examples

---

### 5. Add Translations

**Current languages:** English, Arabic

**Want to add a language?**
1. Open discussion in Issues
2. Translate core files first
3. Maintain structure
4. Ensure cultural appropriateness
5. Commit to maintenance

---

### 6. Submit Benchmarks

**We accept:**
- Performance comparisons
- Cost analyses
- Quality evaluations
- Speed tests

**Requirements:**
- Methodology description
- Sample size >50
- Reproducible tests
- Raw data available
- Date of testing
- Environment details

---

## Contribution Guidelines

### Quality Standards

**All contributions must:**
- Be accurate and verified
- Provide value to professionals
- Follow existing format
- Include proper attribution
- Respect licenses

**Content should:**
- Be clear and concise
- Use professional language
- Include examples where helpful
- Reference sources
- Avoid marketing language

---

### Style Guide

**Formatting:**
- Use markdown properly
- No emojis (professional style)
- Consistent header levels
- Tables for comparisons
- Code blocks with language tags

**Writing:**
- Active voice
- Clear and direct
- Professional tone
- No jargon without explanation
- Spell out acronyms first use

**Code:**
```python
# Use descriptive variable names
# Include comments
# Follow PEP 8 (Python) or language standards
# Provide complete, runnable examples
# Handle errors appropriately
```

---

### File Structure

**Where to add content:**

```
/RESOURCES/
├── AI-TOOLS-DIRECTORY.md          # Tool listings
├── PROMPTS-LIBRARY.md              # Prompt examples
├── USE-CASES-LIBRARY.md            # Implementation examples
├── COMPARISON-GUIDES.md            # Tool comparisons
├── LEARNING-PATHS.md               # Educational content
├── WORKFLOWS-GALLERY.md            # Code workflows
└── [other guides]

/AR/RESOURCES/                      # Arabic translations
```

**Creating new files:**
- Discuss in Issues first
- Follow naming convention (UPPERCASE-WITH-DASHES.md)
- Add to README navigation
- Include Arabic translation path
- Update CHANGELOG.md

---

## How to Submit

### Via GitHub Issues (Easiest)

1. Go to Issues tab
2. Click "New Issue"
3. Choose appropriate template
4. Fill in all required fields
5. Submit

**Best for:**
- Tool suggestions
- Error reports
- Feature requests
- Questions

---

### Via Pull Request (Advanced)

**Prerequisites:**
- GitHub account
- Git knowledge
- Markdown proficiency

**Steps:**

1. **Fork Repository**
   ```bash
   # Fork on GitHub, then clone
   git clone https://github.com/YOUR_USERNAME/prompts.git
   cd prompts
   ```

2. **Create Branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```

3. **Make Changes**
   - Edit files
   - Test formatting
   - Verify links
   - Check spelling

4. **Commit**
   ```bash
   git add .
   git commit -m "Add: Brief description of changes"
   ```

5. **Push**
   ```bash
   git push origin feature/your-feature-name
   ```

6. **Create Pull Request**
   - Go to your fork on GitHub
   - Click "Pull Request"
   - Fill in template
   - Submit

---

### Commit Message Format

**Structure:**
```
Type: Brief description (50 chars max)

Detailed explanation if needed.
Include motivation and context.

Fixes #issue_number
```

**Types:**
- `Add:` New content
- `Update:` Modified existing content
- `Fix:` Corrections
- `Remove:` Deleted content
- `Refactor:` Structural changes

**Examples:**
```
Add: Gemini 1.5 Pro to comparison guide

Update: OpenAI pricing in cost optimization

Fix: Broken link in MCP servers directory

Remove: Deprecated tool from AI tools list
```

---

## Code of Conduct

### Our Standards

**Positive behavior:**
- Respectful communication
- Constructive feedback
- Collaborative spirit
- Professional conduct
- Inclusive language

**Unacceptable:**
- Harassment or insults
- Political/religious debates
- Spam or self-promotion
- Sharing private information
- Unethical AI usage discussion

---

### Enforcement

**Violations will result in:**
1. Warning
2. Temporary ban
3. Permanent ban

**Report issues to:** GitHub Issues (private)

---

## Review Process

### What Happens After Submission

1. **Initial Review** (1-3 days)
   - Check completeness
   - Verify accuracy
   - Test links/code

2. **Feedback** (if needed)
   - Requested changes
   - Clarification questions
   - Improvement suggestions

3. **Approval** (1-5 days)
   - Merge into repository
   - Update changelog
   - Close related issues

4. **Recognition**
   - Contributor credit
   - GitHub contributor badge

---

### Response Times

**We aim for:**
- Issues: Response within 48 hours
- Pull Requests: Initial review within 72 hours
- Approval: Within 1 week (if no issues)

**Delays may occur during:**
- Holidays
- Major updates
- High volume periods

---

## Recognition

### Contributors

All contributors are recognized:
- GitHub contributors list
- Special thanks in releases
- Contributor badge
- Optional profile link

**Top contributors** may be invited as maintainers.

---

## Questions?

**Before asking:**
- Check [FAQ](./FAQ.md)
- Search existing Issues
- Read relevant documentation

**Still need help?**
- Open GitHub Issue
- Tag as "question"
- Provide context

---

## Quick Start Checklist

- [ ] Read this guide
- [ ] Check existing Issues/PRs
- [ ] Verify information accuracy
- [ ] Follow style guide
- [ ] Test all code examples
- [ ] Update relevant files only
- [ ] Write clear commit messages
- [ ] Submit PR with description

---

## Thank You!

Your contributions help thousands of AI professionals. We appreciate your time and effort!

**Happy Contributing!**

---

**Related Resources:**
- [Code of Conduct](https://github.com/github/docs/blob/main/CODE_OF_CONDUCT.md)
- [GitHub Flow](https://guides.github.com/introduction/flow/)
- [Markdown Guide](https://www.markdownguide.org/)
