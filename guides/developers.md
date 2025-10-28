# Quick Start Guide for Developers

**Get up and running with AI tools in your development workflow in under 30 minutes.**

## Your First 30 Minutes with AI

### Step 1: Choose Your Primary Tool (5 minutes)

**Recommended**: Claude Code (for comprehensive development)

```bash
# Install
npm install -g @anthropic/claude-code

# Get API key from https://console.anthropic.com
export ANTHROPIC_API_KEY="your_key"

# Start
claude
```

**Alternative**: GitHub Copilot (if you already use VS Code)
```bash
# Install in VS Code
# Extensions → GitHub Copilot

# Or CLI
gh extension install github/gh-copilot
```

---

### Step 2: Your First AI-Powered Task (10 minutes)

Try these common scenarios:

#### Scenario A: Code Review
```
You: Review this function for bugs and improvements

[Paste your code]

Context:
- Language: Python 3.11
- Framework: FastAPI
- This handles user authentication
```

#### Scenario B: Debug an Error
```
You: I'm getting this error:

[Error message and stack trace]

Here's the relevant code:
[Code]

Environment:
- Node.js 18
- Express 4.x
- PostgreSQL 14

What's causing this and how do I fix it?
```

#### Scenario C: Generate New Code
```
You: Create a REST API endpoint for user registration

Requirements:
- POST /api/auth/register
- Email and password validation
- Hash password with bcrypt
- Return JWT token
- Handle duplicate email error

Language: Python with FastAPI
Database: PostgreSQL with SQLAlchemy
```

---

### Step 3: Set Up Your Workflow (15 minutes)

#### Configure Your Environment

**1. Create a workspace directory**
```bash
mkdir ~/ai-dev-workspace
cd ~/ai-dev-workspace
```

**2. Set up MCP servers (optional but powerful)**

Create `~/.claude-code/config.json`:
```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "~/ai-dev-workspace"]
    },
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_TOKEN": "your_github_token"
      }
    }
  }
}
```

**3. Create helpful aliases**

Add to `~/.bashrc` or `~/.zshrc`:
```bash
# AI shortcuts
alias ai="claude"
alias review="claude 'review this code' --file"
alias explain="claude 'explain this code' --file"
alias test="claude 'generate unit tests' --file"

# Quick commit messages
alias aicommit="git diff | claude 'write a commit message'"
```

---

## Essential Workflows

### Workflow 1: Feature Development

```bash
# 1. Plan the feature
claude --plan "Add user authentication with JWT"

# 2. Generate code
claude "Implement the authentication system based on the plan"

# 3. Review generated code
claude "Review the authentication code for security issues"

# 4. Generate tests
claude "Create comprehensive unit tests for auth system"

# 5. Generate docs
claude "Write API documentation for these endpoints" --file src/auth.py
```

### Workflow 2: Bug Fixing

```
Step 1: Describe the bug
---
I have a bug where users can't login after password reset.

Error: "Invalid token"

Relevant files:
- src/auth/reset.py
- src/auth/tokens.py

Stack trace:
[paste trace]
---

Step 2: AI investigates
It will ask for code, suggest checks, identify root cause

Step 3: Implement fix
Ask: "Show me the fix with before/after code"

Step 4: Prevent regression
Ask: "Generate tests to prevent this bug from happening again"
```

### Workflow 3: Code Refactoring

```
Task: Refactor legacy code

Prompt:
---
Refactor this legacy code to modern standards:

[Paste code]

Current issues:
- No error handling
- No type hints
- Deeply nested logic
- Poor naming

Requirements:
- Add type hints (Python 3.11+)
- Improve error handling
- Reduce complexity
- Keep same functionality
- Add docstrings
- Follow PEP 8

Show before/after comparison
---
```

---

## Power User Tips

### Tip 1: Use Context Effectively

**Bad**:
```
"Fix this bug"
[code snippet]
```

**Good**:
```
"Fix the null pointer exception in the payment processing"

Context:
- File: src/payments/processor.py:142
- Error: NoneType object has no attribute 'amount'
- This started after deploying v2.3.0
- Happens when processing refunds

Stack trace:
[full trace]

Related code:
[payment processor class]

Recent changes:
[what changed in v2.3.0]
```

### Tip 2: Iterative Development

```
Iteration 1: "Create a basic user model"
→ Review output

Iteration 2: "Add email validation and password hashing"
→ Review output

Iteration 3: "Add methods for authentication and session management"
→ Review output

Iteration 4: "Add comprehensive docstrings and type hints"
→ Final review
```

### Tip 3: Learn by Asking

```
"Explain this design pattern in the code:
[paste code]

1. What pattern is this?
2. Why is it useful here?
3. What are the trade-offs?
4. When should I use it vs alternatives?"
```

### Tip 4: Code Review Partnership

```
"Act as a senior engineer reviewing this PR.

Changes:
[PR diff]

Check for:
1. Logic errors and edge cases
2. Performance implications
3. Security vulnerabilities
4. Code style and best practices
5. Test coverage gaps
6. Documentation needs

Be thorough but constructive."
```

---

## Tool Recommendations by Task

| Task | Best Tool | Why |
|------|-----------|-----|
| Full feature development | Claude Code | Long context, file ops |
| Quick code completion | GitHub Copilot | Real-time, in-editor |
| Learning new framework | ChatGPT/Claude web | Explanations + examples |
| Code review | Claude Code | Deep analysis |
| API testing | Postman AI | HTTP-specific |
| Database queries | MCP Postgres | Direct DB access |
| Documentation | Claude/GPT-4 | Long-form writing |
| Git operations | GitHub Copilot CLI | Command suggestions |

---

## Language-Specific Tips

### Python
```
Effective prompts:
- "Create type hints using Python 3.11+ syntax"
- "Use dataclasses instead of regular classes"
- "Follow PEP 8 and include docstrings"
- "Use pathlib instead of os.path"
- "Add async/await for I/O operations"
```

### JavaScript/TypeScript
```
Effective prompts:
- "Use TypeScript with strict mode"
- "Follow Airbnb style guide"
- "Use modern ES6+ syntax"
- "Implement proper error handling with try-catch"
- "Add JSDoc comments for better IDE support"
```

### Go
```
Effective prompts:
- "Follow Go idioms and conventions"
- "Use proper error handling (not panic)"
- "Add context for cancellation"
- "Include example usage and tests"
- "Use interfaces where appropriate"
```

### Rust
```
Effective prompts:
- "Use idiomatic Rust with proper ownership"
- "Handle Result and Option types properly"
- "Avoid unnecessary clones"
- "Add comprehensive error types"
- "Include unit tests and documentation tests"
```

---

## Common Pitfalls to Avoid

### ❌ Don't: Blindly Copy-Paste

AI-generated code needs review:
- Check for security issues
- Verify error handling
- Test edge cases
- Ensure it fits your architecture

### ❌ Don't: Ask One Giant Question

Break complex tasks into steps:
- "First, design the data model"
- "Now, implement the API endpoints"
- "Add validation logic"
- "Generate tests"

### ❌ Don't: Ignore Context

Always provide:
- Language and version
- Frameworks and libraries
- Project structure
- Coding standards
- Constraints

### ❌ Don't: Skip Testing

AI code needs verification:
- Run the code
- Test edge cases
- Review for your specific use case
- Check performance

---

## Integration with Existing Tools

### VS Code + Copilot + Claude

```
Workflow:
1. Use Copilot for inline completions while coding
2. Use Claude Code terminal for:
   - Planning features
   - Code review
   - Multi-file refactoring
   - Documentation
3. Use ChatGPT web for:
   - Learning concepts
   - Architecture discussions
```

### Git + AI

```bash
# Better commit messages
git diff | claude "write a conventional commit message"

# PR descriptions
gh pr create --title "Feature X" --body "$(claude 'write PR description' --context .)"

# Code review
gh pr diff 123 | claude "review this PR"
```

### CI/CD Integration

```yaml
# GitHub Actions example
- name: AI Code Review
  run: |
    git diff main...${{ github.sha }} | \
    claude "Review for security and performance issues" > review.md

- name: Comment on PR
  uses: actions/github-script@v6
  with:
    script: |
      const review = require('fs').readFileSync('review.md', 'utf8');
      github.rest.issues.createComment({
        issue_number: context.issue.number,
        body: review
      });
```

---

## Measuring Success

### Week 1 Goals
- [ ] Set up AI development tool
- [ ] Use AI for 3 coding tasks
- [ ] Review and understand all AI-generated code
- [ ] Create 5 helpful prompts for your work

### Month 1 Goals
- [ ] AI assists with 50% of coding tasks
- [ ] Reduced debugging time by 30%
- [ ] Learned 2 new concepts via AI explanation
- [ ] Built personal prompt library

### Long-term Goals
- [ ] Integrate AI into daily workflow
- [ ] Contribute AI-generated code to production
- [ ] Share learnings with team
- [ ] Optimize prompts for your domain

---

## Next Steps

1. **Practice**: Use AI for your next 10 tasks
2. **Learn**: Read [AI Best Practices](../AI-BEST-PRACTICES.md)
3. **Explore**: Try [Software Development Prompts](../prompts/software-development/)
4. **Expand**: Set up [MCP Servers](../tools/mcp-servers.md)
5. **Build**: Create your first [AI Agent](../agents/)

---

## Resources

- [Anthropic Claude Code Docs](https://docs.claude.com/claude-code)
- [GitHub Copilot Best Practices](https://github.blog/category/engineering/copilot/)
- [Software Development Prompts](../prompts/software-development/)
- [CLI Tools Comparison](../tools/cli-tools.md)

---

**Questions?** Check out the main [README](../README.md) or [AI Best Practices](../AI-BEST-PRACTICES.md)

**Last Updated**: 2025-10-28
