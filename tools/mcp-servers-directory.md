# Comprehensive MCP Servers Directory (2025)

**Curated by Dr. Ahmed Halloub**

> This comprehensive directory contains 100+ Model Context Protocol (MCP) servers organized by category. MCP servers extend AI capabilities through secure integrations with external tools and data sources. Last updated: October 2025

---

## Table of Contents

1. [What is MCP?](#what-is-mcp)
2. [Official Reference Servers](#official-reference-servers)
3. [Developer Tools & Platforms](#developer-tools--platforms)
4. [Data & Analytics](#data--analytics)
5. [Cloud Platforms](#cloud-platforms)
6. [Communication & Messaging](#communication--messaging)
7. [Business & Productivity](#business--productivity)
8. [Payment Processing](#payment-processing)
9. [AI & ML Services](#ai--ml-services)
10. [Web & Search](#web--search)
11. [Browser Automation](#browser-automation)
12. [Code Execution](#code-execution)
13. [Coding Agents](#coding-agents)
14. [Command Line](#command-line)
15. [Databases](#databases)
16. [Aggregators & Meta-Servers](#aggregators--meta-servers)
17. [Specialized Categories](#specialized-categories)

---

## What is MCP?

**Model Context Protocol (MCP)** is an open protocol developed by Anthropic that enables AI assistants to securely interact with local and remote resources. MCP servers act as bridges between AI models and external tools, data sources, and services.

### Key Benefits
- **Secure Integration**: Controlled access to external resources
- **Extensibility**: Easy to create custom servers
- **Standardization**: Consistent interface across tools
- **Scalability**: From local files to enterprise systems

### How It Works
1. **MCP Server**: Provides tools and resources via standardized protocol
2. **MCP Client**: AI assistant that connects to servers
3. **Protocol**: Standardized communication layer
4. **Transport**: STDIO, SSE, HTTP, or WebSocket

---

## Official Reference Servers

These servers demonstrate MCP features and are maintained by Anthropic:

| Server | Description | Use Case |
|--------|-------------|----------|
| **Everything** | Reference/test server with prompts, resources, and tools | Testing and development |
| **Fetch** | Web content fetching and conversion for efficient LLM usage | Web scraping, content retrieval |
| **Filesystem** | Secure file operations with configurable access controls | File management, code editing |
| **Git** | Tools to read, search, and manipulate Git repositories | Version control, code review |
| **Memory** | Knowledge graph-based persistent memory system | Long-term context, knowledge storage |
| **Sequential Thinking** | Dynamic and reflective problem-solving through thought sequences | Complex reasoning, planning |
| **Time** | Time and timezone conversion capabilities | Scheduling, time calculations |

**Installation**:
```bash
# Filesystem
npx @modelcontextprotocol/server-filesystem /path/to/directory

# Git
npx @modelcontextprotocol/server-git /path/to/repo

# Fetch
npx @modelcontextprotocol/server-fetch
```

---

## Developer Tools & Platforms

### Version Control

| Server | Description | Features |
|--------|-------------|----------|
| **GitHub** | Official GitHub API integration | Repository management, issues, PRs, actions |
| **GitLab** | GitLab API for project management | CI/CD, merge requests, issues |
| **Gitea** | Self-hosted Git service integration | Private repositories, lightweight |
| **Azure DevOps** | Microsoft DevOps platform | Repos, work items, builds, releases |
| **Git** | Local Git repository manipulation | Commits, branches, history, diffs |

**Example: GitHub MCP**
```bash
npm install @modelcontextprotocol/server-github
```

**Configuration**:
```json
{
  "mcpServers": {
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

### CI/CD & Build Tools

| Server | Description | Key Features |
|--------|-------------|--------------|
| **CircleCI** | Enable AI agents to fix build failures | Pipeline management, build analysis |
| **Jenkins** | Official plugin for build management | Job execution, build status |
| **Buildkite** | CI/CD pipeline control | Pipeline triggers, artifact management |

### Design & Prototyping

| Server | Description | Use Case |
|--------|-------------|----------|
| **Figma Context** | Design data access for implementation | Design handoff, component specs |

---

## Data & Analytics

### Data Warehouses

| Server | Description | Key Features |
|--------|-------------|--------------|
| **Databricks** | Connect to data, AI tools & agents, Databricks platform | SQL queries, data analysis, job management |
| **BigQuery** | Google Cloud data warehouse queries | Large-scale analytics, SQL interface |
| **Snowflake** | Data warehouse access and analysis | Cloud data platform, multi-cloud |

**Example: BigQuery MCP**
```bash
npm install @modelcontextprotocol/server-bigquery
```

### Databases

| Server | Description | Type |
|--------|-------------|------|
| **PostgreSQL** | Database query and management | Relational |
| **MySQL** | Multi-implementation MySQL access | Relational |
| **MongoDB** | Community and Atlas cluster support | Document |
| **SQLite** | Local database operations | Embedded |
| **Neo4j** | Graph database server (schema + read/write-cypher) | Graph |
| **Elasticsearch** | Query data in Elasticsearch | Search/Analytics |
| **Redis** | In-memory data structure store | Cache/KV Store |

**Example: PostgreSQL MCP**
```json
{
  "mcpServers": {
    "postgres": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-postgres"],
      "env": {
        "DATABASE_URL": "postgresql://user:pass@localhost:5432/db"
      }
    }
  }
}
```

### Data Platforms

| Server | Description | Use Case |
|--------|-------------|----------|
| **dbt MCP** | Official integration with dbt Core/Cloud | Data transformation pipelines |
| **Keboola MCP** | Data platform interaction | ETL, data orchestration |
| **Kafka Schema Registry** | Schema management with 48 tools | Stream processing, schema evolution |

---

## Cloud Platforms

### Major Cloud Providers

| Server | Description | Services |
|--------|-------------|----------|
| **AWS** | Specialized MCP servers with AWS best practices | EC2, S3, Lambda, RDS, and more |
| **Azure** | Storage, Cosmos DB, CLI access | Full Azure service suite |
| **Google Cloud Run** | Deploy code to cloud platform | Serverless deployment |
| **Firebase** | Firebase's experimental MCP Server | Firestore, Auth, Storage |

### Infrastructure

| Server | Description | Use Case |
|--------|-------------|----------|
| **Terraform MCP** | Infrastructure-as-code management | IaC, resource provisioning |
| **Kubernetes MCP** | Multiple implementations for cluster management | Container orchestration |
| **Cloudflare MCP** | Workers, KV, R2, D1 integration | Edge computing, CDN |
| **Heroku** | App, add-on, and database management | PaaS deployment |

---

## Communication & Messaging

| Server | Description | Features |
|--------|-------------|----------|
| **Slack** | Most powerful MCP server for Slack Workspaces | Channels, messages, users, search |
| **Teams** | Advanced agent orchestration, multi-agent collaboration | Microsoft Teams messaging |
| **Discord** | Discord bot automation | Server management, message handling |
| **WhatsApp** | Message sending and searching | WhatsApp Business API |
| **Telegram** | User data and message management | Bot API, channels |
| **Twilio** | SMS and communication APIs | SMS, voice, video |
| **Mailgun/Mailjet** | Email delivery services | Transactional emails, campaigns |

**Example: Slack MCP**
```json
{
  "mcpServers": {
    "slack": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-slack"],
      "env": {
        "SLACK_BOT_TOKEN": "xoxb-your-token",
        "SLACK_TEAM_ID": "T01234567"
      }
    }
  }
}
```

---

## Business & Productivity

### Project Management

| Server | Description | Platform |
|--------|-------------|----------|
| **Notion** | Notion API implementation | Pages, databases, tasks |
| **Linear** | Search, create, and update Linear issues, projects, comments | Issue tracking |
| **Jira** | Work item and project management | Atlassian suite |
| **Monday.com** | Board and item interaction | Work OS platform |
| **Asana** | Task and project management | Team collaboration |

### CRM & Sales

| Server | Description | Features |
|--------|-------------|----------|
| **HubSpot** | Connect, manage, and interact with HubSpot CRM data | Contacts, deals, pipelines |
| **Salesforce** | CRM integration | Customer data, automation |

**Example: Notion MCP**
```json
{
  "mcpServers": {
    "notion": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-notion"],
      "env": {
        "NOTION_API_KEY": "your_notion_api_key"
      }
    }
  }
}
```

---

## Payment Processing

| Server | Description | Features |
|--------|-------------|----------|
| **Stripe** | Payment operations and transactions | Charges, customers, subscriptions |
| **PayPal** | Payment management | PayPal API integration |
| **Square** | POS and payment systems | Point of sale, invoicing |

---

## AI & ML Services

| Server | Description | Use Case |
|--------|-------------|----------|
| **OpenAI** | API integration for language models | GPT-4, DALL-E, embeddings |
| **Hugging Face** | Semantic search for spaces and papers, datasets | Model discovery, datasets |
| **Comet/Langfuse** | Prompt management and LLM monitoring | Experiment tracking, observability |
| **Anthropic Claude** | Direct integration support | Claude API access |

---

## Web & Search

| Server | Description | Features |
|--------|-------------|----------|
| **Brave Search** | Web and local search using Brave's Search API | Privacy-focused search |
| **Google Maps** | Location services, directions, and place details | Geocoding, routing |
| **Exa** | Search Engine made for AIs by Exa | Semantic search |
| **Web Search MCP** | Google search without API keys | Free web search |

---

## Browser Automation

| Server | Description | Features |
|--------|-------------|----------|
| **Playwright MCP** | Automate browser interactions in the cloud | Web navigation, data extraction |
| **Puppeteer MCP** | Browser automation for web scraping | Headless Chrome, screenshots |
| **Browserbase** | Cloud browser automation | Managed browser infrastructure |
| **Microsoft Playwright** | Official implementation with accessibility snapshots | Full browser control |
| **YouTube Transcript** | Fetch and analyze video transcripts | Video content analysis |

**Example: Puppeteer MCP**
```json
{
  "mcpServers": {
    "puppeteer": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-puppeteer"]
    }
  }
}
```

---

## Code Execution

Secure sandboxed environments for running code:

| Server | Description | Language |
|--------|-------------|----------|
| **Node Sandbox** | Docker-based sandboxes for executing JavaScript with npm | JavaScript/Node.js |
| **Python Sandbox** | Isolated Python execution environment | Python |
| **Dagger Container** | Containerized coding agent environments | Multi-language |
| **JavaScript Executor** | V8-based isolation for running AI-generated code locally | JavaScript |

**Example: Python Sandbox**
```json
{
  "mcpServers": {
    "python-sandbox": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-python-sandbox"]
    }
  }
}
```

---

## Coding Agents

Full autonomous programming capabilities:

| Server | Description | Features |
|--------|-------------|----------|
| **Codemcp** | Basic read, write, and command-line tools | File operations, shell commands |
| **WCGW** | Rust-based code agent with shell execution | Safe code execution |
| **LeetCode MCP** | Problem access and solution submission | Coding practice, testing |
| **VSCode MCP** | Workspace integration with linter feedback | IDE integration |

---

## Command Line

| Server | Description | Features |
|--------|-------------|----------|
| **MCP Shell** | Secure shell command execution on demand in isolated environments | Bash, zsh, fish |
| **SSH MCP** | Remote server access via SSH | Remote execution |
| **iTerm MCP** | Terminal integration with output capture | macOS terminal |

---

## Aggregators & Meta-Servers

Servers that unify access to multiple MCP servers:

| Server | Description | Key Feature |
|--------|-------------|-------------|
| **1mcp/agent** | Unified MCP server implementation aggregating multiple servers | Single endpoint |
| **MCPJungle** | Self-hosted registry for enterprise AI agents | Enterprise management |
| **Glama Chat** | Multi-modal client with MCP support | Chat interface |
| **MetaMCP** | Unified middleware managing MCP connections with GUI | Visual management |
| **Magg** | Meta-MCP server acting as universal hub, allows LLMs to autonomously discover and install servers | Auto-discovery |

---

## Specialized Categories

### Art & Culture

| Server | Description |
|--------|-------------|
| **TMDB MCP** | Movie and TV show database integration |
| **Open Library** | Book information search |
| **Manim MCP** | Animation generation |
| **Blender MCP** | 3D modeling integration |
| **Metropolitan Museum API** | Artwork search and display |

### Social Media

| Server | Description |
|--------|-------------|
| **Twitter/X Search** | Tweet search functionality |
| **Bluesky Context** | Decentralized social platform |
| **LinkedIn Integration** | Professional network access |

### Web3 & Blockchain

| Server | Description |
|--------|-------------|
| **CoinGecko** | Cryptocurrency data |
| **Bankless Onchain** | Blockchain analytics |

### Specialized

| Server | Description |
|--------|-------------|
| **3D Printing (OctoEverywhere)** | 3D printer control |
| **Gaming (OP.GG)** | Esports data |
| **AltTester** | Game automation |
| **Healthcare (OMOP)** | Clinical terminology mapping |

---

## Installation & Configuration

### General Installation Steps

1. **Install the MCP Server**:
```bash
npm install @modelcontextprotocol/server-<name>
# or
npx -y @modelcontextprotocol/server-<name>
```

2. **Configure in Your Client** (Claude Code example):
```json
{
  "mcpServers": {
    "server-name": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-name"],
      "env": {
        "API_KEY": "your_api_key"
      }
    }
  }
}
```

3. **Restart Your Client**: Reload your AI assistant to load the new server

### Available SDKs

MCP servers can be built using:
- **TypeScript/JavaScript** (most common)
- **Python** (extensive coverage)
- **Go** (infrastructure focus)
- **Rust** (performance-critical)
- **C#** (.NET ecosystem)
- **Java/Kotlin** (enterprise)
- **Ruby** (legacy systems)
- **Swift** (iOS/macOS)
- **PHP** (web applications)

---

## Authentication Methods

Different servers support various authentication approaches:

### OAuth2
- GitHub, GitLab, Google services
- Requires: Client ID, Client Secret, Redirect URI

### API Keys
- Most cloud services (AWS, Azure, OpenAI)
- Requires: API key in environment variable

### SSH Keys
- SSH MCP, remote Git repositories
- Requires: Private key file path

### Service Accounts
- Google Cloud, Firebase, enterprise systems
- Requires: Service account JSON file

### Username/Password
- Databases, legacy systems
- Requires: Credentials in configuration

---

## Transport Protocols

MCP supports multiple transport mechanisms:

| Protocol | Use Case | Example |
|----------|----------|---------|
| **STDIO** | Local processes | Most npm-based servers |
| **SSE** | Server-Sent Events for real-time | Cloud services |
| **HTTP** | REST API integration | Web-based servers |
| **WebSocket** | Bidirectional communication | Real-time applications |

---

## Deployment Modes

### Local Execution 🏠
- Runs on your machine
- Full file system access
- Best for: Development, personal projects

### Cloud-Based Services ☁️
- Hosted servers
- API-based access
- Best for: Production, scalability

### Platform-Specific
- **macOS** 🍎: Native macOS servers
- **Windows** 🪟: Windows-compatible servers
- **Linux** 🐧: Linux support (most common)

---

## Best Practices

### Security
✅ **Do**:
- Use environment variables for secrets
- Implement rate limiting
- Validate all inputs
- Use least-privilege access
- Audit server logs regularly

❌ **Don't**:
- Hardcode credentials
- Grant unnecessary permissions
- Skip input validation
- Ignore security updates
- Expose internal services

### Performance
- Cache frequently accessed data
- Implement connection pooling
- Use async/await patterns
- Monitor resource usage
- Optimize database queries

### Development
- Write comprehensive tests
- Document your server
- Follow MCP specification
- Version your server
- Provide examples

---

## Creating Custom MCP Servers

### Quick Start (TypeScript)

```typescript
import { Server } from "@modelcontextprotocol/sdk/server/index.js";
import { StdioServerTransport } from "@modelcontextprotocol/sdk/server/stdio.js";

const server = new Server({
  name: "my-custom-server",
  version: "1.0.0",
});

// Register tools
server.setRequestHandler("tools/list", async () => ({
  tools: [{
    name: "my_tool",
    description: "Description of what this tool does",
    inputSchema: {
      type: "object",
      properties: {
        param: { type: "string", description: "Parameter description" }
      }
    }
  }]
}));

// Handle tool calls
server.setRequestHandler("tools/call", async (request) => {
  // Implementation
});

const transport = new StdioServerTransport();
await server.connect(transport);
```

---

## Resources & Links

### Official Resources
- **MCP Specification**: https://modelcontextprotocol.io
- **Official Servers**: https://github.com/modelcontextprotocol/servers
- **MCP SDK**: https://github.com/modelcontextprotocol/sdk

### Community
- **Awesome MCP Servers**: https://github.com/punkpeye/awesome-mcp-servers
- **MCP Index**: https://mcpindex.net
- **MCP Server Finder**: https://mcpserverfinder.com

### Documentation
- [Claude MCP Documentation](https://docs.anthropic.com/claude/docs/mcp)
- [Building MCP Servers Guide](https://modelcontextprotocol.io/docs/building-servers)

---

## Contributing

Have an MCP server to add? We welcome contributions!

**Submission Requirements**:
- Server name and description
- Installation instructions
- Configuration example
- Use cases
- GitHub repository link
- License information

---

## Related Resources

- [AI Tools Directory](./ai-tools-directory.md)
- [AI Agents](../agents/autonomous-agents.md)
- [API Integration Examples](../apis/integration-patterns.md)
- [AI Best Practices](../AI-BEST-PRACTICES.md)

---

## License

MIT License - Feel free to use these resources in your projects!

---

**Last Updated**: October 30, 2025

**Maintained by**: Dr. Ahmed Halloub | [ahmedhalloub.com](https://ahmedhalloub.com)

**Note**: MCP is an evolving protocol. Server capabilities and availability may change. Always refer to official documentation for the most current information.
