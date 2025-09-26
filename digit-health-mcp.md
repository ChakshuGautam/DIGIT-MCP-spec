# DIGIT Health MCP Tool Reference

## Table of Contents

- **[Service Health Monitoring](#service-health-monitoring)** (5 tools)
  - [`check_service_health`](#check_service_health)
  - [`check_all_services`](#check_all_services)
  - [`get_dependency_health`](#get_dependency_health)
  - [`check_circuit_breaker`](#check_circuit_breaker)
  - [`get_sla_status`](#get_sla_status)

- **[Infrastructure Health](#infrastructure-health)** (4 tools)
  - [`check_database`](#check_database)
  - [`check_kafka`](#check_kafka)
  - [`check_redis`](#check_redis)
  - [`check_elasticsearch`](#check_elasticsearch)

- **[Performance & Diagnostics](#performance--diagnostics)** (7 tools)
  - [`get_service_metrics`](#get_service_metrics)
  - [`analyze_health_trend`](#analyze_health_trend)
  - [`diagnose_service_issue`](#diagnose_service_issue)
  - [`get_health_history`](#get_health_history)
  - [`run_diagnostic_script`](#run_diagnostic_script)
  - [`export_health_report`](#export_health_report)
  - [`benchmark_api`](#benchmark_api)

- **[Health Configuration](#health-configuration)** (4 tools)
  - [`trigger_health_check`](#trigger_health_check)
  - [`configure_health_check`](#configure_health_check)
  - [`disable_health_check`](#disable_health_check)
  - [`schedule_maintenance`](#schedule_maintenance)

- **[Issue Management](#issue-management)** (4 tools)
  - [`create_health_alert`](#create_health_alert)
  - [`acknowledge_health_issue`](#acknowledge_health_issue)
  - [`resolve_health_issue`](#resolve_health_issue)
  - [`get_alert_history`](#get_alert_history)

- **[Service Operations](#service-operations)** (3 tools)
  - [`restart_unhealthy_service`](#restart_unhealthy_service)
  - [`scale_service`](#scale_service)
  - [`rollback_deployment`](#rollback_deployment)

## Service Health Monitoring

### `check_service_health`

**Description:** Check health status of specific DIGIT service with dependency analysis

**Parameters:**

- **service_name** (string) **(required)**: Name of the service to check
- **health_type** (string) **(required)**: Type of health check (basic, detailed, deep)
- **include_dependencies** (boolean) _(optional)_: Include dependency health status
- **timeout** (number) _(optional)_: Health check timeout in seconds

---

### `check_all_services`

**Description:** Perform comprehensive health check across all DIGIT services

**Parameters:**

- **category** (string) _(optional)_: Service category filter (core, oss, studio)
- **tenant_id** (string) _(optional)_: Check services for specific tenant
- **parallel** (boolean) _(optional)_: Run checks in parallel for speed

---

### `get_dependency_health`

**Description:** Analyze health status of service dependencies and upstream services

**Parameters:**

- **service_name** (string) **(required)**: Service to analyze dependencies for
- **depth** (number) _(optional)_: Dependency tree depth to check
- **include_external** (boolean) _(optional)_: Include external dependencies

---

### `check_circuit_breaker`

**Description:** Check circuit breaker status for service endpoints

**Parameters:**

- **service_name** (string) **(required)**: Service with circuit breaker
- **endpoint** (string) _(optional)_: Specific endpoint to check

---

### `get_sla_status`

**Description:** Retrieve SLA compliance status and metrics for services

**Parameters:**

- **service_name** (string) _(optional)_: Filter by specific service
- **time_period** (object) **(required)**: Time period for SLA calculation
- **sla_metrics** (array) _(optional)_: Specific SLA metrics to include

---

## Infrastructure Health

### `check_database`

**Description:** Monitor database health including connections and performance

**Parameters:**

- **database_name** (string) **(required)**: Database instance to check
- **checks** (array) _(optional)_: Specific checks (connections, queries, locks)
- **include_metrics** (boolean) _(optional)_: Include performance metrics

---

### `check_kafka`

**Description:** Monitor Kafka cluster health including topics and consumer lag

**Parameters:**

- **cluster_name** (string) _(optional)_: Kafka cluster identifier
- **topics** (array) _(optional)_: Specific topics to check
- **check_lag** (boolean) _(optional)_: Include consumer lag analysis

---

### `check_redis`

**Description:** Monitor Redis instance health and performance metrics

**Parameters:**

- **instance_name** (string) **(required)**: Redis instance identifier
- **check_memory** (boolean) _(optional)_: Include memory usage analysis
- **check_persistence** (boolean) _(optional)_: Check persistence status

---

### `check_elasticsearch`

**Description:** Monitor Elasticsearch cluster health and index status

**Parameters:**

- **cluster_name** (string) **(required)**: Elasticsearch cluster name
- **indices** (array) _(optional)_: Specific indices to check
- **check_shards** (boolean) _(optional)_: Include shard health analysis

---

## Performance & Diagnostics

### `get_service_metrics`

**Description:** Retrieve performance metrics for service analysis

**Parameters:**

- **service_name** (string) **(required)**: Service to get metrics for
- **metric_types** (array) **(required)**: Types of metrics (cpu, memory, requests)
- **time_range** (object) **(required)**: Time period for metrics collection

---

### `analyze_health_trend`

**Description:** Analyze health trends and predict potential issues

**Parameters:**

- **service_name** (string) _(optional)_: Service to analyze trends for
- **period** (string) **(required)**: Analysis period (1h, 24h, 7d, 30d)
- **alert_on_degradation** (boolean) _(optional)_: Create alert for degradation

---

### `diagnose_service_issue`

**Description:** Diagnose service issues using symptoms and historical data

**Parameters:**

- **service_name** (string) **(required)**: Service with issues
- **symptoms** (array) **(required)**: Observed symptoms and errors
- **deep_analysis** (boolean) _(optional)_: Perform comprehensive analysis

---

### `get_health_history`

**Description:** Retrieve historical health data for trend analysis

**Parameters:**

- **service_name** (string) **(required)**: Service to get history for
- **time_range** (object) **(required)**: Time period for history
- **include_incidents** (boolean) _(optional)_: Include incident data

---

### `run_diagnostic_script`

**Description:** Execute diagnostic scripts for detailed service analysis

**Parameters:**

- **service_name** (string) **(required)**: Target service for diagnostics
- **script_name** (string) **(required)**: Diagnostic script to execute
- **parameters** (object) _(optional)_: Script execution parameters

---

### `export_health_report`

**Description:** Generate comprehensive health report for stakeholders

**Parameters:**

- **time_range** (object) **(required)**: Report time period
- **services** (array) _(optional)_: Services to include in report
- **format** (string) **(required)**: Export format (pdf, excel, json)

---

### `benchmark_api`

**Description:** Performance benchmark API endpoints under load

**Parameters:**

- **endpoint** (string) **(required)**: API endpoint to benchmark
- **load_profile** (object) **(required)**: Load testing configuration
- **collect_metrics** (array) _(optional)_: Metrics to collect during test

---

## Health Configuration

### `trigger_health_check`

**Description:** Manually trigger health checks on demand

**Parameters:**

- **check_type** (string) **(required)**: Type of health check to trigger
- **targets** (array) **(required)**: Services or components to check
- **async** (boolean) _(optional)_: Run check asynchronously

---

### `configure_health_check`

**Description:** Configure health check parameters and schedules

**Parameters:**

- **service_name** (string) **(required)**: Service to configure health check for
- **health_config** (object) **(required)**: Health check configuration
- **schedule** (string) _(optional)_: Check schedule (cron expression)

---

### `disable_health_check`

**Description:** Temporarily disable health checks for maintenance

**Parameters:**

- **service_name** (string) **(required)**: Service to disable checks for
- **check_name** (string) **(required)**: Specific check to disable
- **reason** (string) **(required)**: Reason for disabling check

---

### `schedule_maintenance`

**Description:** Schedule maintenance windows with health check suspension

**Parameters:**

- **services** (array) **(required)**: Services undergoing maintenance
- **maintenance_window** (object) **(required)**: Maintenance schedule
- **notify_users** (boolean) _(optional)_: Send maintenance notifications

---

## Issue Management

### `create_health_alert`

**Description:** Create alert rules for health monitoring and notifications

**Parameters:**

- **alert_name** (string) **(required)**: Name for the alert rule
- **condition** (object) **(required)**: Alert trigger conditions
- **severity** (string) **(required)**: Alert severity level
- **notification_channels** (array) **(required)**: Alert notification channels

---

### `acknowledge_health_issue`

**Description:** Acknowledge health issues to track resolution progress

**Parameters:**

- **issue_id** (string) **(required)**: Health issue identifier
- **acknowledged_by** (string) **(required)**: Person acknowledging the issue
- **notes** (string) _(optional)_: Acknowledgment notes or comments

---

### `resolve_health_issue`

**Description:** Mark health issues as resolved with resolution details

**Parameters:**

- **issue_id** (string) **(required)**: Health issue identifier
- **resolution** (string) **(required)**: Resolution description
- **resolved_by** (string) **(required)**: Person resolving the issue

---

### `get_alert_history`

**Description:** Retrieve history of health alerts and their resolution

**Parameters:**

- **alert_name** (string) _(optional)_: Filter by specific alert
- **severity** (array) _(optional)_: Filter by severity levels
- **status** (array) _(optional)_: Filter by alert status
- **time_range** (object) **(required)**: Time period for alert history

---

## Service Operations

### `restart_unhealthy_service`

**Description:** Restart services that are in unhealthy state

**Parameters:**

- **service_name** (string) **(required)**: Service to restart
- **force** (boolean) _(optional)_: Force restart without graceful shutdown
- **wait_for_drain** (boolean) _(optional)_: Wait for connection draining

---

### `scale_service`

**Description:** Scale service instances based on health and load metrics

**Parameters:**

- **service_name** (string) **(required)**: Service to scale
- **replicas** (number) **(required)**: Target number of replicas
- **reason** (string) **(required)**: Reason for scaling operation

---

### `rollback_deployment`

**Description:** Rollback service to previous version due to health issues

**Parameters:**

- **service_name** (string) **(required)**: Service to rollback
- **target_version** (string) **(required)**: Version to rollback to
- **reason** (string) **(required)**: Reason for rollback

---

## Configuration

```json
{
  "--health-check-interval": "30s",
  "--health-endpoint": "/health",
  "--metrics-endpoint": "/metrics",
  "--timeout": "10s",
  "--retry-count": 3
}
```