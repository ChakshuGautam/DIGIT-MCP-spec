# DIGIT Workflow MCP Tool Reference

## Table of Contents

- **[Workflow Management](#workflow-management)** (4 tools)
  - [`create_workflow`](#create_workflow)
  - [`update_workflow`](#update_workflow)
  - [`delete_workflow`](#delete_workflow)
  - [`clone_workflow`](#clone_workflow)

- **[Workflow Execution](#workflow-execution)** (6 tools)
  - [`start_workflow_instance`](#start_workflow_instance)
  - [`transition_workflow`](#transition_workflow)
  - [`bulk_transition`](#bulk_transition)
  - [`pause_workflow`](#pause_workflow)
  - [`resume_workflow`](#resume_workflow)
  - [`cancel_workflow`](#cancel_workflow)

- **[Workflow Monitoring & History](#workflow-monitoring--history)** (3 tools)
  - [`search_workflow_instances`](#search_workflow_instances)
  - [`get_workflow_history`](#get_workflow_history)
  - [`get_pending_actions`](#get_pending_actions)

- **[Business Rules & SLA](#business-rules--sla)** (8 tools)
  - [`create_business_rule`](#create_business_rule)
  - [`evaluate_business_rules`](#evaluate_business_rules)
  - [`update_business_rule`](#update_business_rule)
  - [`define_sla`](#define_sla)
  - [`track_sla_compliance`](#track_sla_compliance)
  - [`get_sla_breaches`](#get_sla_breaches)
  - [`configure_escalation`](#configure_escalation)

- **[Workflow Development & Testing](#workflow-development--testing)** (5 tools)
  - [`test_workflow`](#test_workflow)
  - [`debug_workflow_instance`](#debug_workflow_instance)
  - [`simulate_workflow`](#simulate_workflow)
  - [`validate_workflow`](#validate_workflow)

- **[Template Management](#template-management)** (3 tools)
  - [`create_workflow_template`](#create_workflow_template)
  - [`apply_template`](#apply_template)
  - [`list_templates`](#list_templates)

- **[Analytics & Performance](#analytics--performance)** (4 tools)
  - [`get_workflow_statistics`](#get_workflow_statistics)
  - [`monitor_workflow_health`](#monitor_workflow_health)
  - [`get_workflow_metrics`](#get_workflow_metrics)
  - [`analyze_bottlenecks`](#analyze_bottlenecks)

## Workflow Management

### `create_workflow`

**Description:** Create new workflow definition with states and transitions

**Parameters:**

- **workflow_name** (string) **(required)**: Unique name for the workflow
- **business_service** (string) **(required)**: Business service associated with workflow
- **tenant_id** (string) **(required)**: Tenant identifier for multi-tenancy
- **states** (array) **(required)**: Workflow states configuration
- **transitions** (array) **(required)**: State transitions and actions

---

### `update_workflow`

**Description:** Update existing workflow with version management

**Parameters:**

- **workflow_id** (string) **(required)**: Workflow identifier to update
- **updates** (object) **(required)**: Workflow configuration updates
- **version_strategy** (enum) _(optional)_: Version strategy (major, minor, patch)
- **migrate_instances** (boolean) _(optional)_: Migrate existing instances to new version

---

### `delete_workflow`

**Description:** Delete workflow with option to force or archive

**Parameters:**

- **workflow_id** (string) **(required)**: Workflow identifier to delete
- **force** (boolean) _(optional)_: Force deletion with active instances
- **archive** (boolean) _(optional)_: Archive instead of permanent deletion

---

### `clone_workflow`

**Description:** Clone existing workflow with customizations

**Parameters:**

- **source_workflow_id** (string) **(required)**: Source workflow to clone
- **new_name** (string) **(required)**: Name for the new workflow
- **tenant_id** (string) **(required)**: Target tenant for the cloned workflow
- **modifications** (object) _(optional)_: Modifications to apply to cloned workflow

---

## Workflow Execution

### `start_workflow_instance`

**Description:** Start new workflow instance for entity processing

**Parameters:**

- **workflow_id** (string) **(required)**: Workflow definition identifier
- **business_id** (string) **(required)**: Business entity identifier
- **initial_data** (object) **(required)**: Initial workflow data payload
- **assignee** (string) _(optional)_: Initial assignee for the workflow
- **comment** (string) _(optional)_: Initial comment or reason

---

### `transition_workflow`

**Description:** Execute workflow transition with action and data

**Parameters:**

- **instance_id** (string) **(required)**: Workflow instance identifier
- **action** (string) **(required)**: Action to perform (approve, reject, send_back)
- **comment** (string) _(optional)_: Comment for the transition
- **assignee** (string) _(optional)_: Next assignee for the workflow
- **documents** (array) _(optional)_: Supporting documents for transition
- **additional_data** (object) _(optional)_: Additional data for the transition

---

### `bulk_transition`

**Description:** Perform bulk transitions on multiple workflow instances

**Parameters:**

- **transitions** (array) **(required)**: Array of transition configurations
- **transaction_mode** (boolean) _(optional)_: Execute as single transaction

---

### `pause_workflow`

**Description:** Pause workflow instance temporarily

**Parameters:**

- **instance_id** (string) **(required)**: Workflow instance to pause
- **reason** (string) **(required)**: Reason for pausing the workflow
- **expected_resume** (timestamp) _(optional)_: Expected resume timestamp

---

### `resume_workflow`

**Description:** Resume paused workflow instance

**Parameters:**

- **instance_id** (string) **(required)**: Workflow instance to resume
- **comment** (string) _(optional)_: Comment for resuming the workflow

---

### `cancel_workflow`

**Description:** Cancel workflow instance with notification

**Parameters:**

- **instance_id** (string) **(required)**: Workflow instance to cancel
- **reason** (string) **(required)**: Reason for cancellation
- **notify_stakeholders** (boolean) _(optional)_: Send cancellation notifications

---

## Workflow Monitoring & History

### `search_workflow_instances`

**Description:** Search workflow instances with comprehensive filtering

**Parameters:**

- **workflow_id** (string) _(optional)_: Filter by specific workflow
- **business_ids** (array) _(optional)_: Filter by business entity IDs
- **status** (array) _(optional)_: Filter by workflow status
- **assignee** (string) _(optional)_: Filter by current assignee
- **date_range** (object) _(optional)_: Filter by date range
- **include_history** (boolean) _(optional)_: Include workflow history

---

### `get_workflow_history`

**Description:** Retrieve complete workflow instance history and audit trail

**Parameters:**

- **instance_id** (string) **(required)**: Workflow instance identifier
- **include_documents** (boolean) _(optional)_: Include document history
- **include_comments** (boolean) _(optional)_: Include comment history

---

### `get_pending_actions`

**Description:** Get pending workflow actions for user or role

**Parameters:**

- **assignee** (string) **(required)**: User identifier for pending actions
- **workflow_id** (string) _(optional)_: Filter by specific workflow
- **priority** (enum) _(optional)_: Filter by priority (high, medium, low)
- **sla_breach_only** (boolean) _(optional)_: Only show SLA breached items

---

## Business Rules & SLA

### `create_business_rule`

**Description:** Create business rule for workflow automation

**Parameters:**

- **rule_name** (string) **(required)**: Unique name for the business rule
- **workflow_id** (string) **(required)**: Associated workflow identifier
- **rule_type** (enum) **(required)**: Rule type (validation, assignment, notification)
- **condition** (object) **(required)**: Rule trigger conditions
- **action** (object) **(required)**: Action to perform when rule triggers
- **priority** (number) _(optional)_: Rule execution priority

---

### `evaluate_business_rules`

**Description:** Evaluate business rules against workflow context

**Parameters:**

- **instance_id** (string) **(required)**: Workflow instance identifier
- **context** (object) **(required)**: Evaluation context data
- **rules** (array) _(optional)_: Specific rules to evaluate

---

### `update_business_rule`

**Description:** Update existing business rule configuration

**Parameters:**

- **rule_id** (string) **(required)**: Business rule identifier
- **updates** (object) **(required)**: Rule configuration updates
- **test_mode** (boolean) _(optional)_: Test rule without applying changes

---

### `define_sla`

**Description:** Define SLA timelines and escalation for workflow

**Parameters:**

- **workflow_id** (string) **(required)**: Workflow to define SLA for
- **sla_config** (array) **(required)**: SLA configuration by state/action
- **escalation_matrix** (array) _(optional)_: Escalation rules and assignments

---

### `track_sla_compliance`

**Description:** Track SLA compliance metrics and violations

**Parameters:**

- **workflow_id** (string) _(optional)_: Filter by specific workflow
- **time_period** (object) **(required)**: Time period for compliance tracking
- **group_by** (array) _(optional)_: Group metrics by dimensions
- **breach_only** (boolean) _(optional)_: Only show SLA breaches

---

### `get_sla_breaches`

**Description:** Get current and historical SLA breaches

**Parameters:**

- **workflow_id** (string) _(optional)_: Filter by specific workflow
- **severity** (enum) _(optional)_: Filter by breach severity
- **time_range** (object) **(required)**: Time range for breach search

---

### `configure_escalation`

**Description:** Configure escalation rules and notification matrix

**Parameters:**

- **workflow_id** (string) **(required)**: Workflow to configure escalation for
- **escalation_rules** (array) **(required)**: Escalation rules and triggers

---

## Workflow Development & Testing

### `test_workflow`

**Description:** Test workflow with various scenarios and validation

**Parameters:**

- **workflow_id** (string) **(required)**: Workflow to test
- **test_scenarios** (array) **(required)**: Test scenarios and data
- **coverage_report** (boolean) _(optional)_: Generate test coverage report

---

### `debug_workflow_instance`

**Description:** Debug workflow instance with breakpoints and inspection

**Parameters:**

- **instance_id** (string) **(required)**: Workflow instance to debug
- **breakpoints** (array) _(optional)_: Breakpoints for debugging
- **step_mode** (boolean) _(optional)_: Enable step-by-step execution
- **watch_variables** (array) _(optional)_: Variables to watch during debug

---

### `simulate_workflow`

**Description:** Simulate workflow execution with test data

**Parameters:**

- **workflow_id** (string) **(required)**: Workflow to simulate
- **simulation_data** (object) **(required)**: Data for simulation
- **iterations** (number) _(optional)_: Number of simulation iterations
- **randomize** (boolean) _(optional)_: Randomize simulation parameters

---

### `validate_workflow`

**Description:** Validate workflow configuration and detect issues

**Parameters:**

- **workflow_config** (object) **(required)**: Workflow configuration to validate
- **validation_level** (enum) _(optional)_: Validation level (basic, strict, comprehensive)
- **check_deadlocks** (boolean) _(optional)_: Check for potential deadlocks

---

## Template Management

### `create_workflow_template`

**Description:** Create reusable workflow template with parameters

**Parameters:**

- **template_name** (string) **(required)**: Name for the workflow template
- **category** (string) **(required)**: Template category
- **base_workflow** (object) **(required)**: Base workflow configuration
- **variables** (array) _(optional)_: Template variables and parameters
- **documentation** (string) _(optional)_: Template usage documentation

---

### `apply_template`

**Description:** Create workflow from template with customizations

**Parameters:**

- **template_id** (string) **(required)**: Template identifier to apply
- **tenant_id** (string) **(required)**: Target tenant for new workflow
- **customizations** (object) **(required)**: Template customizations
- **workflow_name** (string) **(required)**: Name for the new workflow

---

### `list_templates`

**Description:** List available workflow templates with filtering

**Parameters:**

- **category** (string) _(optional)_: Filter by template category
- **search_text** (string) _(optional)_: Search in template names/descriptions
- **tags** (array) _(optional)_: Filter by template tags

---

## Analytics & Performance

### `get_workflow_statistics`

**Description:** Get comprehensive workflow performance statistics

**Parameters:**

- **workflow_id** (string) **(required)**: Workflow to get statistics for
- **time_period** (object) **(required)**: Time period for statistics
- **metrics** (array) _(optional)_: Specific metrics to include
- **group_by** (string) _(optional)_: Group statistics by dimension

---

### `monitor_workflow_health`

**Description:** Monitor overall workflow system health and performance

**Parameters:**

- **include_metrics** (array) _(optional)_: Specific health metrics to include
- **alert_on_issues** (boolean) _(optional)_: Generate alerts for issues

---

### `get_workflow_metrics`

**Description:** Retrieve detailed workflow performance metrics

**Parameters:**

- **workflow_id** (string) _(optional)_: Filter by specific workflow
- **metrics** (array) **(required)**: Metrics to retrieve
- **time_range** (object) **(required)**: Time range for metrics
- **aggregation** (string) _(optional)_: Aggregation method for metrics

---

### `analyze_bottlenecks`

**Description:** Analyze workflow bottlenecks and performance issues

**Parameters:**

- **workflow_id** (string) **(required)**: Workflow to analyze
- **time_period** (object) **(required)**: Time period for analysis
- **threshold** (number) _(optional)_: Performance threshold for bottleneck detection

---

## Configuration

```json
{
  "--workflow-engine": "camunda",
  "--state-store": "postgresql",
  "--event-bus": "kafka",
  "--sla-check-interval": "5m",
  "--escalation-enabled": true,
  "--audit-enabled": true,
  "--max-retries": 3,
  "--timeout": "30s"
}
```