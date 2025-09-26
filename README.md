# DIGIT MCP

Model Context Protocol specifications for the DIGIT platform.

## Why

[Read why MCP for DIGIT](./why-mcp.md)

## Problem

[Understanding the challenges](./problems-with-mcp.md)

## Solution

[How MCP addresses DIGIT complexity](./solution-for-mcp.md)

## Specifications

### Available Specs

- [`digit-api-mcp.md`](./spec/digit-api-mcp.md)
- [`digit-mdms-mcp.md`](./spec/digit-mdms-mcp.md)
- [`digit-workflow-mcp.md`](./spec/digit-workflow-mcp.md)
- [`digit-data-mcp.md`](./spec/digit-data-mcp.md)
- [`digit-dashboard-analytics-mcp.md`](./spec/digit-dashboard-analytics-mcp.md)
- [`digit-telemetry-mcp.md`](./spec/digit-telemetry-mcp.md)
- [`digit-documentation-mcp.md`](./spec/digit-documentation-mcp.md)
- [`digit-ui-components-mcp.md`](./spec/digit-ui-components-mcp.md)
- [`digit-service-patterns-mcp.md`](./spec/digit-service-patterns-mcp.md)

## Installation

### Requirements

- [Node.js 22.12.0](https://nodejs.org/) or newer
- [npm](https://www.npmjs.com/)
- DIGIT platform credentials

### Getting Started

Add the following config to your MCP client:

```json
{
  "mcpServers": {
    "digit-mcp": {
      "command": "npx",
      "args": ["digit-mcp@latest"]
    }
  }
}
```

> [!NOTE]  
> Using `digit-mcp@latest` ensures that your MCP client will always use the latest version of the DIGIT MCP server.
> Authentication will be done by logging in through the DIGIT platform.

### MCP Client Configuration

<details>
  <summary>Claude Code</summary>
    Use the Claude Code CLI to add the DIGIT MCP server:

```bash
claude mcp add digit-mcp npx digit-mcp@latest
```

</details>

<details>
  <summary>Cline</summary>
  Follow https://docs.cline.bot/mcp/configuring-mcp-servers and use the config provided above.
</details>

<details>
  <summary>Cursor</summary>

Go to `Cursor Settings` -> `MCP` -> `New MCP Server`. Use the config provided above.

</details>

<details>
  <summary>Copilot / VS Code</summary>
  Follow the MCP install guide, with the standard config from above. You can also install the DIGIT MCP server using the VS Code CLI:
  
  ```bash
  code --add-mcp '{"name":"digit-mcp","command":"npx","args":["digit-mcp@latest"]}'
  ```
</details>

<details>
  <summary>JetBrains AI Assistant</summary>

Go to `Settings | Tools | AI Assistant | Model Context Protocol (MCP)` -> `Add`. Use the config provided above.

</details>

### Configuration Options

Pass configuration via the `args` property:

```json
{
  "mcpServers": {
    "digit-mcp": {
      "command": "npx",
      "args": [
        "digit-mcp@latest",
        "--environment=production",
        "--tenant=dj"
      ]
    }
  }
}
```

Available options:
- `--environment`: Target environment (dev, staging, production)
- `--tenant`: Tenant identifier (e.g., dj for Djibouti)
- `--base-url`: Custom DIGIT API endpoint
- `--timeout`: Request timeout in milliseconds

### Your First Prompt

Enter the following prompt in your MCP Client to verify installation:

```
Search for active trade licenses in the system
```

Your MCP client should connect to DIGIT and retrieve the data.

## Authentication

The DIGIT MCP server handles authentication through the DIGIT platform's standard OAuth flow. On first use, you'll be prompted to:

1. Login through the DIGIT platform portal
2. Authorize the MCP client
3. Token will be securely stored for subsequent requests

> [!NOTE]  
> Credentials are stored securely in your system's credential manager and refreshed automatically when expired.

## Kubernetes Integration

The [kubernetes-mcp-server](https://github.com/containers/kubernetes-mcp-server) will be forked and tailored to DIGIT platform needs, providing:

- Direct integration with DIGIT's Kubernetes deployments
- Service mesh management for DIGIT microservices
- Automated scaling based on DIGIT-specific metrics
- Helm chart management for DIGIT modules
- Custom resource definitions for DIGIT workloads