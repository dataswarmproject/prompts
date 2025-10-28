# MCP (Model Context Protocol) Servers

**Powerful integrations to extend AI capabilities with external tools and data sources.**

## What is MCP?

Model Context Protocol (MCP) is an open protocol that allows AI assistants to securely connect with external data sources and tools. MCP servers provide seamless integrations that enhance AI capabilities.

## Popular MCP Servers

### 1. File System

**Purpose**: Access and manipulate local files and directories

**Capabilities**:
- Read files with various formats (text, code, markdown, JSON, etc.)
- Write and edit files
- Create and manage directories
- Search file contents
- List directory structures

**Installation**:
```bash
npx @modelcontextprotocol/server-filesystem /path/to/directory
```

**Use Cases**:
- Code development and editing
- Document processing
- Project management
- File organization

**Configuration** (Claude Code):
```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/home/user/projects"]
    }
  }
}
```

---

### 2. GitHub

**Purpose**: Interact with GitHub repositories

**Capabilities**:
- Search repositories and code
- Read file contents
- Create and manage issues
- Review pull requests
- Fork repositories
- Create files and commits

**Installation**:
```bash
npm install @modelcontextprotocol/server-github
```

**Use Cases**:
- Code review automation
- Issue triage and management
- Repository analysis
- Documentation updates

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

**Required**: GitHub personal access token

---

### 3. Memory

**Purpose**: Persistent knowledge storage across conversations

**Capabilities**:
- Store information permanently
- Create knowledge graphs
- Retrieve relevant context
- Build long-term memory
- Organize entities and relationships

**Installation**:
```bash
npx @modelcontextprotocol/server-memory
```

**Use Cases**:
- Project context retention
- Personal knowledge management
- Multi-session workflows
- Learning from past interactions

**Configuration**:
```json
{
  "mcpServers": {
    "memory": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-memory"]
    }
  }
}
```

---

### 4. Google Drive

**Purpose**: Access and manage Google Drive files

**Capabilities**:
- Read documents, sheets, and slides
- Search Drive content
- Create and update files
- Share files and manage permissions
- Access shared drives

**Installation**:
```bash
npm install @modelcontextprotocol/server-gdrive
```

**Use Cases**:
- Document analysis
- Collaborative work
- Data extraction from sheets
- Report generation

**Configuration**:
```json
{
  "mcpServers": {
    "gdrive": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-gdrive"],
      "env": {
        "GOOGLE_APPLICATION_CREDENTIALS": "/path/to/credentials.json"
      }
    }
  }
}
```

**Required**: Google Cloud credentials

---

### 5. Postgres

**Purpose**: Query and manage PostgreSQL databases

**Capabilities**:
- Execute SQL queries
- Retrieve schema information
- Analyze database structure
- Read and write data
- Perform joins and aggregations

**Installation**:
```bash
npm install @modelcontextprotocol/server-postgres
```

**Use Cases**:
- Database analysis
- Query optimization
- Data extraction
- Schema design
- Report generation

**Configuration**:
```json
{
  "mcpServers": {
    "postgres": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-postgres", "postgresql://user:pass@localhost/db"]
    }
  }
}
```

---

### 6. Brave Search

**Purpose**: Web search using Brave Search API

**Capabilities**:
- Real-time web searches
- News and current events
- Local search results
- Privacy-focused searching

**Installation**:
```bash
npm install @modelcontextprotocol/server-brave-search
```

**Use Cases**:
- Research and fact-checking
- Current event information
- Market research
- Competitive analysis

**Configuration**:
```json
{
  "mcpServers": {
    "brave-search": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-brave-search"],
      "env": {
        "BRAVE_API_KEY": "your_api_key"
      }
    }
  }
}
```

**Required**: Brave Search API key (free tier available)

---

### 7. Slack

**Purpose**: Integrate with Slack workspaces

**Capabilities**:
- Read channel messages
- Send messages and notifications
- Search message history
- Manage channels
- Access thread conversations

**Installation**:
```bash
npm install @modelcontextprotocol/server-slack
```

**Use Cases**:
- Team notifications
- Message analysis
- Automated responses
- Knowledge extraction

**Configuration**:
```json
{
  "mcpServers": {
    "slack": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-slack"],
      "env": {
        "SLACK_BOT_TOKEN": "xoxb-your-token",
        "SLACK_TEAM_ID": "your-team-id"
      }
    }
  }
}
```

---

### 8. Puppeteer (Web Automation)

**Purpose**: Browser automation and web scraping

**Capabilities**:
- Navigate websites
- Take screenshots
- Extract content
- Fill forms
- Execute JavaScript
- Handle dynamic content

**Installation**:
```bash
npm install @modelcontextprotocol/server-puppeteer
```

**Use Cases**:
- Web scraping
- Automated testing
- Screenshot generation
- Data collection

**Configuration**:
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

### 9. SQLite

**Purpose**: Query SQLite databases

**Capabilities**:
- Execute SQL queries
- Analyze database structure
- Read and write data
- Create tables and indexes

**Installation**:
```bash
npm install @modelcontextprotocol/server-sqlite
```

**Use Cases**:
- Local data analysis
- Testing and development
- Lightweight data storage
- Mobile app backends

**Configuration**:
```json
{
  "mcpServers": {
    "sqlite": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-sqlite", "/path/to/database.db"]
    }
  }
}
```

---

## Third-Party MCP Servers

### Notion

**Repository**: https://github.com/makenotion/notion-mcp
**Purpose**: Access Notion databases and pages
**Capabilities**: Read/write pages, query databases, search content

### Linear

**Repository**: https://github.com/linear/linear-mcp
**Purpose**: Manage Linear issues and projects
**Capabilities**: Create issues, update status, search projects

### Figma

**Repository**: https://github.com/figma/figma-mcp
**Purpose**: Access Figma designs
**Capabilities**: Read design files, export assets, access comments

### Sentry

**Repository**: https://github.com/getsentry/sentry-mcp
**Purpose**: Access error tracking data
**Capabilities**: Query errors, analyze issues, manage alerts

---

## Setting Up MCP Servers

### For Claude Desktop

1. Open Claude Desktop settings
2. Navigate to "Developer" section
3. Click "Edit Config"
4. Add MCP server configuration
5. Restart Claude Desktop

### For Claude Code (CLI)

1. Create or edit config file:
   ```bash
   nano ~/.config/claude-code/mcp_config.json
   ```

2. Add server configurations:
   ```json
   {
     "mcpServers": {
       "server-name": {
         "command": "npx",
         "args": ["-y", "@modelcontextprotocol/server-name", "...args"],
         "env": {
           "API_KEY": "your-key"
         }
       }
     }
   }
   ```

3. Restart Claude Code

---

## Creating Custom MCP Servers

### Basic Structure

```typescript
import { Server } from "@modelcontextprotocol/sdk/server/index.js";
import { StdioServerTransport } from "@modelcontextprotocol/sdk/server/stdio.js";

const server = new Server({
  name: "my-custom-server",
  version: "1.0.0",
}, {
  capabilities: {
    resources: {},
    tools: {},
  },
});

// Define tools
server.setRequestHandler("tools/list", async () => {
  return {
    tools: [{
      name: "my_tool",
      description: "What my tool does",
      inputSchema: {
        type: "object",
        properties: {
          param: { type: "string" }
        },
        required: ["param"]
      }
    }]
  };
});

// Handle tool calls
server.setRequestHandler("tools/call", async (request) => {
  if (request.params.name === "my_tool") {
    // Tool implementation
    return {
      content: [{
        type: "text",
        text: "Result from my tool"
      }]
    };
  }
});

// Start server
const transport = new StdioServerTransport();
await server.connect(transport);
```

### Publishing Your MCP Server

1. Create npm package
2. Follow naming convention: `@username/server-name`
3. Add proper documentation
4. Include installation instructions
5. Publish to npm
6. Submit to MCP registry

---

## Best Practices

### Security

- **Never hardcode secrets** in configuration files
- Use environment variables for API keys
- Limit file system access to necessary directories
- Review MCP server source code before using
- Use read-only access when possible

### Performance

- Configure appropriate timeouts
- Cache frequently accessed data
- Use efficient queries
- Limit result sizes
- Monitor resource usage

### Debugging

- Check MCP server logs
- Verify environment variables
- Test with minimal configuration
- Use verbose logging during development
- Check for port conflicts

---

## Troubleshooting

### MCP Server Not Connecting

```bash
# Check if server is running
ps aux | grep mcp

# Test server manually
npx @modelcontextprotocol/server-name --help

# Check configuration syntax
cat ~/.config/claude-code/mcp_config.json | jq
```

### Permission Issues

```bash
# Ensure proper permissions
chmod +x /path/to/mcp/server

# Check file access
ls -la /path/to/resource
```

### API Key Issues

```bash
# Verify environment variable
echo $API_KEY_NAME

# Test API key separately
curl -H "Authorization: Bearer $API_KEY" https://api.example.com
```

---

## Resources

- **Official MCP Documentation**: https://modelcontextprotocol.io
- **MCP SDK**: https://github.com/modelcontextprotocol/typescript-sdk
- **Server Registry**: https://github.com/modelcontextprotocol/servers
- **Community Discord**: [Link to community]

---

**Last Updated**: 2025-10-28

**See Also**:
- [CLI Tools](./cli-tools.md)
- [Web Apps](./web-apps.md)
- [AI Best Practices](../AI-BEST-PRACTICES.md)
