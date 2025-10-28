# AI CLI Tools

**Command-line tools for integrating AI into your development workflow.**

## AI-Powered Development Tools

### 1. Claude Code

**What it is**: Official Anthropic CLI for Claude AI with advanced coding capabilities

**Key Features**:
- Interactive AI assistant in terminal
- File operations (read, write, edit)
- Git integration
- Bash command execution
- 200K token context window
- MCP server support
- Task management

**Installation**:
```bash
npm install -g @anthropic/claude-code
```

**Usage**:
```bash
# Start interactive session
claude

# Direct command
claude "refactor this function" --file mycode.py

# With context
claude "fix the bug" --context src/

# Plan mode
claude --plan "add authentication"
```

**Best For**:
- Full-stack development
- Code reviews and refactoring
- Complex multi-file operations
- Long-form development tasks

**Pricing**: Requires Anthropic API key (pay-as-you-go)

---

### 2. GitHub Copilot CLI

**What it is**: AI-powered command suggestions in your terminal

**Key Features**:
- Natural language to shell commands
- Command explanations
- Git command assistance
- Cross-platform support

**Installation**:
```bash
gh extension install github/gh-copilot
```

**Usage**:
```bash
# Get command suggestions
gh copilot suggest "find all javascript files modified today"

# Explain a command
gh copilot explain "tar -xzf archive.tar.gz"

# Git-specific help
gh copilot git "undo last commit but keep changes"
```

**Best For**:
- Learning new commands
- Shell script writing
- Git operations
- System administration

**Pricing**: Included with GitHub Copilot subscription ($10-19/month)

---

### 3. ChatGPT CLI (unofficial)

**What it is**: Unofficial CLI client for ChatGPT

**Key Features**:
- Direct ChatGPT access from terminal
- Conversation history
- Multiple model support
- Markdown rendering

**Installation**:
```bash
npm install -g @j178/chatgpt
# or
pip install chatgpt-cli
```

**Usage**:
```bash
# Interactive mode
chatgpt

# Single query
chatgpt "explain docker compose"

# With system message
chatgpt -s "You are a Python expert" "debug this code"

# Use GPT-4
chatgpt -m gpt-4-turbo "complex task"
```

**Best For**:
- Quick queries
- General assistance
- Code explanations
- Scripting with AI

**Pricing**: Requires OpenAI API key

---

### 4. aichat

**What it is**: Powerful CLI for multiple AI providers

**Key Features**:
- Supports OpenAI, Claude, Gemini, local models
- Role system
- Session management
- File attachments
- Code execution

**Installation**:
```bash
# macOS
brew install aichat

# Cargo
cargo install aichat

# From source
git clone https://github.com/sigoden/aichat
cd aichat && cargo build --release
```

**Configuration**:
```bash
# Set API keys
export OPENAI_API_KEY="your-key"
export ANTHROPIC_API_KEY="your-key"

# Or use config file
aichat --config
```

**Usage**:
```bash
# Start chat
aichat

# With role
aichat --role programmer "write a quicksort"

# With file
aichat --file code.py "review this"

# Execute code
aichat --execute "python script that prints fibonacci"

# Change model
aichat --model claude-3-5-sonnet "complex task"
```

**Best For**:
- Multi-model workflows
- Power users
- Scripting and automation
- File-based interactions

**Pricing**: Varies by provider (API keys required)

---

### 5. LLM (by Simon Willison)

**What it is**: CLI for working with Large Language Models

**Key Features**:
- Plugin system
- Multiple model support
- Template system
- Conversation logging
- Embeddings support

**Installation**:
```bash
pip install llm

# Install plugins
llm install llm-gpt4all  # Local models
llm install llm-claude   # Claude support
```

**Usage**:
```bash
# Basic query
llm "explain quantum computing"

# With system prompt
llm -s "You are a code reviewer" "review this function" < code.py

# Save conversation
llm "start of conversation" --save conv1
llm --continue conv1 "follow up question"

# Use template
llm -t code-review "review this" --file app.py

# List models
llm models list

# Use specific model
llm -m claude-3-5-sonnet "complex query"
```

**Best For**:
- Data pipelines
- Experimentation
- Research workflows
- Plugin ecosystem

**Pricing**: Free tool, varies by model provider

---

## Code Generation Tools

### 6. Cursor (Terminal Mode)

**What it is**: AI-first code editor with terminal integration

**Key Features**:
- Inline code generation
- Multi-file editing
- Codebase understanding
- Terminal commands

**Installation**:
Download from https://cursor.sh

**Usage**:
```bash
# Open in terminal mode
cursor .

# Generate file from description
cursor generate "REST API for users"

# Edit existing code
cursor edit "add error handling" main.py
```

**Best For**:
- Full project generation
- Complex refactoring
- New project setup

**Pricing**: Free tier + Pro ($20/month)

---

### 7. GPT Engineer

**What it is**: Generate entire codebases from prompts

**Key Features**:
- Full project scaffolding
- Interactive clarifications
- Multiple iterations
- Dependency management

**Installation**:
```bash
pip install gpt-engineer
```

**Usage**:
```bash
# Create new project
gpt-engineer

# Specify prompt file
gpt-engineer --prompt "Build a todo app with React and FastAPI"

# Continue existing project
gpt-engineer --improve
```

**Best For**:
- MVP creation
- Prototyping
- Learning new frameworks

**Pricing**: Requires OpenAI API key

---

## Productivity Tools

### 8. mods

**What it is**: AI for your command line pipelines

**Key Features**:
- STDIN/STDOUT support
- Perfect for pipes
- Multiple AI providers
- Markdown formatting

**Installation**:
```bash
# macOS
brew install mods

# Go
go install github.com/charmbracelet/mods@latest
```

**Usage**:
```bash
# Process piped input
cat file.py | mods "explain this code"

# Generate commit message
git diff | mods "write a commit message"

# Summarize logs
tail -100 app.log | mods "summarize errors"

# With web search
mods --web "latest python best practices"

# Save output
echo "write a haiku about coding" | mods > haiku.txt
```

**Best For**:
- Shell scripting
- Log analysis
- Git workflows
- Data processing

**Pricing**: Free, requires API key for providers

---

### 9. sgpt (Shell-GPT)

**What it is**: ChatGPT for shell commands and code

**Key Features**:
- Command generation
- Code generation
- REPL mode
- Chat history

**Installation**:
```bash
pip install shell-gpt
```

**Usage**:
```bash
# Generate shell command
sgpt --shell "find all python files and count lines"

# Execute directly (with confirmation)
sgpt --shell --execute "compress all logs"

# Generate code
sgpt --code "python function to validate email"

# Chat mode
sgpt --repl "You are a DevOps expert"

# Use chat history
sgpt --chat devops "how to set up CI/CD"
sgpt --chat devops "continue with GitHub Actions"
```

**Best For**:
- Learning commands
- Quick scripts
- DevOps automation

**Pricing**: Requires OpenAI API key

---

### 10. ai (GitHub CLI extension)

**What it is**: AI-powered GitHub CLI enhancements

**Key Features**:
- PR summaries
- Issue triage
- Code review assistance
- Commit message generation

**Installation**:
```bash
gh extension install github/gh-copilot
```

**Usage**:
```bash
# Generate PR description
gh ai pr create

# Summarize PR
gh ai pr summary 123

# Triage issues
gh ai issue triage

# Review code
gh ai pr review 456
```

**Best For**:
- GitHub workflows
- Team collaboration
- PR management

**Pricing**: Requires GitHub Copilot

---

## Specialized Tools

### 11. Continue.dev (CLI Mode)

**What it is**: Open-source AI code assistant

**Key Features**:
- Multiple LLM support
- Codebase indexing
- Custom models
- Local model support

**Installation**:
```bash
npm install -g continue
```

**Best For**:
- Privacy-conscious development
- Custom model integration
- Enterprise use

**Pricing**: Free and open-source

---

### 12. Aider

**What it is**: AI pair programming in terminal

**Key Features**:
- Git integration
- Multi-file edits
- Automatic commits
- Model comparison

**Installation**:
```bash
pip install aider-chat
```

**Usage**:
```bash
# Start in repo
aider

# Add files to context
aider src/main.py tests/test_main.py

# Use specific model
aider --model gpt-4-turbo

# Auto-commit changes
aider --auto-commits

# Comparison mode
aider --compare
```

**Best For**:
- Pair programming
- Test-driven development
- Refactoring sessions

**Pricing**: Requires API key

---

## Setup Best Practices

### Environment Variables

```bash
# Add to ~/.bashrc or ~/.zshrc

# OpenAI
export OPENAI_API_KEY="sk-..."

# Anthropic
export ANTHROPIC_API_KEY="sk-ant-..."

# Google
export GOOGLE_API_KEY="..."

# Default model preferences
export AI_MODEL="claude-3-5-sonnet-20241022"
export OPENAI_MODEL="gpt-4-turbo"
```

### Aliases for Productivity

```bash
# Quick AI access
alias ai="claude"
alias ask="mods"
alias cmd="gh copilot suggest"

# Specific tasks
alias codereview="claude --role code-reviewer"
alias explain="mods 'explain this simply'"
alias commit="git diff | mods 'commit message' | git commit -F -"

# Model-specific
alias gpt4="aichat --model gpt-4-turbo"
alias sonnet="aichat --model claude-3-5-sonnet"
```

### Cost Management

```bash
# Track API usage
llm log | tail -100  # Recent queries

# Set spending limits in provider dashboards
# Monitor usage regularly

# Use cheaper models for simple tasks
alias quickai="aichat --model gpt-3.5-turbo"
```

---

## Comparison Matrix

| Tool | Best For | Multi-Model | Piping | Price |
|------|----------|-------------|--------|-------|
| Claude Code | Full dev workflow | No | Yes | API |
| GitHub Copilot CLI | Commands | No | Limited | $10-19/mo |
| aichat | Power users | Yes | Yes | API |
| LLM | Data pipelines | Yes | Yes | Free+API |
| mods | Shell scripts | Yes | Yes | API |
| sgpt | Quick commands | No | Yes | API |
| GPT Engineer | Projects | No | No | API |
| Aider | Pair programming | Yes | No | API |

---

## Resources

- **Claude Code Docs**: https://docs.claude.com/claude-code
- **GitHub Copilot**: https://github.com/features/copilot
- **aichat**: https://github.com/sigoden/aichat
- **LLM**: https://llm.datasette.io
- **mods**: https://github.com/charmbracelet/mods
- **Aider**: https://aider.chat

---

**Last Updated**: 2025-10-28

**See Also**:
- [MCP Servers](./mcp-servers.md)
- [Web Apps](./web-apps.md)
- [APIs](../apis/)
