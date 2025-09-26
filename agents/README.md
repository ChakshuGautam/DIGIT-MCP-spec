# DIGIT MCP Agents

Specialized AI agents for DIGIT platform operations, each designed for specific tasks and equipped with relevant MCP tools.

## Available Agents

### digit-do-deployer
Deploys DIGIT platform to DigitalOcean Kubernetes Service (DOKS)
- Creates and manages Kubernetes clusters
- Sets up infrastructure (VPC, databases, load balancers)
- Deploys DIGIT services via Helm
- Monitors deployment health

### digit-docs-scraper  
Maintains DIGIT documentation and structure
- Scrapes official documentation
- Updates sitemaps and navigation
- Tracks documentation changes
- Generates summaries

### digit-api-explorer
Explores and tests DIGIT APIs
- Discovers API endpoints
- Tests functionality
- Generates documentation
- Validates contracts

## Agent Configuration

Each agent JSON file contains:
- `name`: Agent identifier
- `description`: Brief description
- `purpose`: Detailed purpose
- `capabilities`: List of what the agent can do
- `tools`: MCP tools the agent has access to
- `configuration`: Agent-specific settings

## Usage

These agent configurations are used by MCP clients to spawn specialized agents with appropriate tool access and configuration for specific DIGIT platform tasks.

```bash
# Example: Deploy DIGIT to DigitalOcean
mcp agent spawn digit-do-deployer --task "Deploy DIGIT to DOKS cluster in NYC"

# Example: Update documentation
mcp agent spawn digit-docs-scraper --task "Update DIGIT documentation structure"

# Example: Test APIs
mcp agent spawn digit-api-explorer --task "Test user service APIs"
```

## Creating New Agents

To create a new specialized agent:

1. Create a JSON file in this directory
2. Define the agent's purpose and capabilities
3. List the required MCP tools
4. Add any agent-specific configuration
5. Document the agent in this README

## Tool Access Patterns

Agents follow these patterns for tool access:
- `mcp__*`: MCP server tools
- `Bash`, `Read`, `Write`, `Edit`: File system operations
- `WebFetch`: Web scraping and API testing
- `TodoWrite`: Task management