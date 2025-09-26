# DIGIT MCP Documentation

Model Context Protocol (MCP) specifications for the DIGIT platform, providing standardized tool interfaces for AI agents to interact with DIGIT services.

## Index

### Core Services
- [**DIGIT API MCP**](./digit-api-mcp.md) - Universal CRUD operations for all DIGIT entities
- [**DIGIT MDMS MCP**](./digit-mdms-mcp.md) - Master data management and configuration
- [**DIGIT Workflow MCP**](./digit-workflow-mcp.md) - Workflow design, execution, and management

### Platform Operations
- [**DIGIT Health MCP**](./digit-health-mcp.md) - Service health monitoring and diagnostics
- [**DIGIT Data MCP**](./digit-data-mcp.md) - Data operations, ETL, and analytics
- [**DIGIT Telemetry MCP**](./digit-telemetry-mcp.md) - Logging, metrics, tracing, and observability

### Development Tools
- [**DIGIT Documentation MCP**](./digit-documentation-mcp.md) - API documentation generation and management
- [**DIGIT UI Components MCP**](./digit-ui-components-mcp.md) - UI component library and design system
- [**DIGIT Service Patterns MCP**](./digit-service-patterns-mcp.md) - Architectural patterns and code generation

### Template
- [**Service MCP Template**](./service-mcp-template.md) - Template for creating service-specific MCPs

## Quick Reference

| MCP | Primary Use Case | Key Tools |
|-----|-----------------|-----------|
| API | Entity CRUD operations | `create_entity`, `search_entities`, `execute_workflow` |
| MDMS | Configuration management | `create_master`, `search_master`, `version_master_data` |
| Workflow | Business process automation | `create_workflow`, `transition_workflow`, `track_sla_compliance` |
| Health | Service monitoring | `check_service_health`, `diagnose_service_issue`, `get_sla_status` |
| Data | Data processing | `create_etl_pipeline`, `run_data_quality_check`, `execute_query` |
| Telemetry | Observability | `search_logs`, `query_metrics`, `search_traces` |
| Documentation | API docs | `generate_api_docs`, `create_api_playground`, `validate_api_docs` |
| UI Components | Frontend development | `create_component`, `generate_form`, `create_data_table` |
| Service Patterns | Architecture | `generate_microservice`, `implement_cqrs`, `detect_anti_patterns` |

## Configuration

All MCPs share common configuration patterns:

```json
{
  "--base-url": "https://api.digit.org",
  "--auth-token": "bearer-token",
  "--tenant-id": "dj",
  "--timeout": 30000
}
```

## Usage

These MCP specifications define the tools available to AI agents for interacting with the DIGIT platform. Each MCP document lists:

1. **Tools** - Available operations with their parameters
2. **Configuration** - Service-specific configuration options

## Contributing

When creating new MCPs:
1. Use the [Service MCP Template](./service-mcp-template.md) as a starting point
2. Follow the concise format: tool names and parameters only
3. Include all required and optional parameters
4. Add service-specific configuration section

## Entity Types

Common entity types used across MCPs:
- `user`, `employee`
- `property`, `trade_license`
- `water_connection`, `sewerage_connection`
- `bill`, `payment`, `receipt`
- `complaint`, `service_request`
- `birth_registration`, `death_registration`
- `fire_noc`, `building_plan`

## Service Discovery

The API MCP automatically routes entities to their appropriate services:
- User Service: `user`, `employee`
- Property Service: `property`
- Trade License: `trade_license`
- Water Service: `water_connection`, `sewerage_connection`
- Billing Service: `bill`, `demand`
- Payment Service: `payment`, `receipt`
- PGR Service: `complaint`, `service_request`
- And 40+ other services...

## Environment Support

MCPs support multiple environments through configuration:
- Development: `dev.digit.org`
- Staging: `staging.digit.org`
- Production: `api.digit.org`

## Multi-Tenant Architecture

All MCPs support DIGIT's multi-tenant architecture:
- State level: `dj` (Djibouti)
- City level: `dj.city-ali-sabieh`, `dj.city-arta`
- Default tenant: `default`

## Contact

For questions or support regarding DIGIT MCPs, contact the DIGIT platform team.