# Service MCP Tool Reference

- **[Core Tools](#core-tools)** (5 tools)
  - [`docs`](#docs)
  - [`apis`](#apis)
  - [`health`](#health)
  - [`trace`](#trace)
  - [`logs`](#logs)
- **[Service-Specific Tools](#service-specific-tools)** (9 tools)
  - [`tools_user_search`](#tools_user_search)
  - [`tools_user_role_update`](#tools_user_role_update)
  - [`tools_workflow_transition`](#tools_workflow_transition)
  - [`tools_workflow_history`](#tools_workflow_history)
  - [`tools_notification_send`](#tools_notification_send)
  - [`tools_report_generate`](#tools_report_generate)
  - [`tools_report_schedule`](#tools_report_schedule)
  - [`tools_mdms_search`](#tools_mdms_search)
  - [`tools_mdms_update`](#tools_mdms_update)

## Core Tools

### `docs`

**Description:** Returns markdown documentation including service layer, dependencies, and integration patterns

**Parameters:**
- **service_name** (string) **(required)**: Name of the service

---

### `apis`

**Description:** Returns OpenAPI specification with all endpoints, schemas, and samples

**Parameters:**
- **service_name** (string) **(required)**: Name of the service

---

### `health`

**Description:** Returns service health status including dependencies and connectivity

**Parameters:**
- **service_name** (string) **(required)**: Name of the service

---

### `trace`

**Description:** Returns distributed trace information for debugging request flows

**Parameters:**
- **trace_id** (string) _(optional)_: Distributed trace identifier
- **request_id** (string) _(optional)_: Request correlation ID (required if trace_id not provided)

---

### `logs`

**Description:** Returns last N log entries from the service

**Parameters:**
- **service_name** (string) **(required)**: Name of the service
- **last_n** (number) _(optional)_: Number of log entries to return (default: 100)

---

## Service-Specific Tools
These tools are examples; actual tools will vary by service.

### `tools_search`

**Description:** Return data filtered from the service by criteria

**Parameters:**
- **tenant_id** (string) **(required)**: Tenant identifier
- **search_criteria** (object) _(optional)_: Search filters

---

