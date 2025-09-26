# DIGIT Telemetry MCP Tool Reference

## Table of Contents

- **[Log Management](#log-management)** (5 tools)
  - [`search_logs`](#search_logs)
  - [`tail_logs`](#tail_logs)
  - [`aggregate_logs`](#aggregate_logs)
  - [`export_logs`](#export_logs)
  - [`analyze_error_logs`](#analyze_error_logs)

- **[Metrics & Monitoring](#metrics--monitoring)** (5 tools)
  - [`query_metrics`](#query_metrics)
  - [`create_custom_metric`](#create_custom_metric)
  - [`record_metric`](#record_metric)
  - [`get_metric_statistics`](#get_metric_statistics)
  - [`create_metric_alert`](#create_metric_alert)

- **[Distributed Tracing](#distributed-tracing)** (5 tools)
  - [`search_traces`](#search_traces)
  - [`get_trace_details`](#get_trace_details)
  - [`analyze_trace_patterns`](#analyze_trace_patterns)
  - [`compare_traces`](#compare_traces)
  - [`create_trace_dashboard`](#create_trace_dashboard)

- **[Audit & Compliance](#audit--compliance)** (4 tools)
  - [`query_audit_logs`](#query_audit_logs)
  - [`create_audit_report`](#create_audit_report)
  - [`track_data_lineage`](#track_data_lineage)
  - [`compliance_audit`](#compliance_audit)

- **[Performance Profiling](#performance-profiling)** (4 tools)
  - [`profile_service`](#profile_service)
  - [`analyze_bottlenecks`](#analyze_bottlenecks)
  - [`generate_flame_graph`](#generate_flame_graph)
  - [`benchmark_api`](#benchmark_api)

- **[Alerting & Notifications](#alerting--notifications)** (4 tools)
  - [`create_alert_rule`](#create_alert_rule)
  - [`manage_alert_subscription`](#manage_alert_subscription)
  - [`acknowledge_alert`](#acknowledge_alert)
  - [`get_alert_history`](#get_alert_history)

- **[Dashboard & Visualization](#dashboard--visualization)** (3 tools)
  - [`create_dashboard`](#create_dashboard)
  - [`export_dashboard`](#export_dashboard)
  - [`share_dashboard`](#share_dashboard)

- **[Advanced Analytics](#advanced-analytics)** (3 tools)
  - [`analyze_trends`](#analyze_trends)
  - [`detect_anomalies`](#detect_anomalies)
  - [`correlate_events`](#correlate_events)

## Log Management

### `search_logs`

**Description:** Search and filter logs across services with advanced query capabilities

**Parameters:**

- **query** (string) **(required)**: Log search query with filters and conditions
- **services** (array) _(optional)_: Specific services to search logs from
- **log_level** (array) _(optional)_: Log levels to include (ERROR, WARN, INFO, DEBUG)
- **time_range** (object) **(required)**: Time range for log search
- **fields** (array) _(optional)_: Specific fields to return in results
- **limit** (number) _(optional)_: Maximum number of log entries to return

---

### `tail_logs`

**Description:** Stream real-time logs from services with filtering

**Parameters:**

- **services** (array) **(required)**: Services to tail logs from
- **filters** (object) _(optional)_: Log filters and conditions
- **follow** (boolean) _(optional)_: Continue streaming new logs
- **lines** (number) _(optional)_: Number of recent lines to show initially

---

### `aggregate_logs`

**Description:** Aggregate log data for analysis and reporting

**Parameters:**

- **aggregation_type** (enum) **(required)**: Aggregation type (count, sum, avg, terms)
- **field** (string) **(required)**: Field to aggregate on
- **group_by** (array) _(optional)_: Fields to group aggregation by
- **time_interval** (string) _(optional)_: Time interval for temporal aggregation
- **filters** (object) _(optional)_: Filters to apply before aggregation

---

### `export_logs`

**Description:** Export filtered logs to various formats for analysis

**Parameters:**

- **query** (string) **(required)**: Query to filter logs for export
- **format** (enum) **(required)**: Export format (json, csv, txt)
- **time_range** (object) **(required)**: Time range for log export
- **destination** (string) _(optional)_: Export destination path or URL

---

### `analyze_error_logs`

**Description:** Analyze error patterns and classify common issues

**Parameters:**

- **services** (array) _(optional)_: Services to analyze errors for
- **time_window** (string) **(required)**: Time window for error analysis
- **group_similar** (boolean) _(optional)_: Group similar error messages
- **include_stack_trace** (boolean) _(optional)_: Include stack trace analysis

---

## Metrics & Monitoring

### `query_metrics`

**Description:** Query time-series metrics with aggregation and filtering

**Parameters:**

- **metric_name** (string) **(required)**: Name of the metric to query
- **filters** (object) _(optional)_: Metric label filters
- **aggregation** (enum) _(optional)_: Aggregation function (sum, avg, max, min)
- **time_range** (object) **(required)**: Time range for metric query
- **step** (string) _(optional)_: Time step interval for data points

---

### `create_custom_metric`

**Description:** Create custom business or application metric

**Parameters:**

- **metric_name** (string) **(required)**: Unique name for the custom metric
- **metric_type** (enum) **(required)**: Metric type (counter, gauge, histogram)
- **description** (string) **(required)**: Description of what the metric measures
- **labels** (array) _(optional)_: Labels for metric categorization
- **unit** (string) _(optional)_: Unit of measurement

---

### `record_metric`

**Description:** Record data point for custom or application metrics

**Parameters:**

- **metric_name** (string) **(required)**: Name of the metric to record
- **value** (number) **(required)**: Metric value to record
- **labels** (object) _(optional)_: Label values for the metric
- **timestamp** (timestamp) _(optional)_: Timestamp for the data point

---

### `get_metric_statistics`

**Description:** Get statistical analysis of metric data over time

**Parameters:**

- **metric_name** (string) **(required)**: Metric to get statistics for
- **statistic** (array) **(required)**: Statistics to calculate (avg, max, min, sum, count)
- **time_range** (object) **(required)**: Time range for statistics
- **dimensions** (array) _(optional)_: Dimensions to group statistics by

---

### `create_metric_alert`

**Description:** Create alert rules based on metric thresholds and conditions

**Parameters:**

- **alert_name** (string) **(required)**: Name for the alert rule
- **metric_query** (string) **(required)**: Metric query for alert condition
- **threshold** (number) **(required)**: Threshold value for alert trigger
- **condition** (enum) **(required)**: Alert condition (greater, less, equal)
- **duration** (string) **(required)**: Duration condition must be true
- **severity** (enum) **(required)**: Alert severity level

---

## Distributed Tracing

### `search_traces`

**Description:** Search distributed traces with complex filtering criteria

**Parameters:**

- **service_name** (string) _(optional)_: Filter by specific service
- **operation_name** (string) _(optional)_: Filter by operation or endpoint
- **trace_id** (string) _(optional)_: Search for specific trace ID
- **min_duration** (number) _(optional)_: Minimum trace duration filter
- **max_duration** (number) _(optional)_: Maximum trace duration filter
- **tags** (object) _(optional)_: Trace tag filters
- **time_range** (object) **(required)**: Time range for trace search

---

### `get_trace_details`

**Description:** Get detailed information about specific trace execution

**Parameters:**

- **trace_id** (string) **(required)**: Trace identifier to get details for
- **include_logs** (boolean) _(optional)_: Include associated log events
- **include_metrics** (boolean) _(optional)_: Include span metrics and timing

---

### `analyze_trace_patterns`

**Description:** Analyze trace patterns to identify performance issues

**Parameters:**

- **service_name** (string) _(optional)_: Filter analysis by service
- **time_window** (string) **(required)**: Time window for pattern analysis
- **pattern_type** (enum) **(required)**: Pattern type (latency, errors, throughput)
- **anomaly_detection** (boolean) _(optional)_: Enable anomaly detection

---

### `compare_traces`

**Description:** Compare multiple traces to identify differences and issues

**Parameters:**

- **trace_ids** (array) **(required)**: List of trace IDs to compare
- **comparison_type** (enum) **(required)**: Comparison type (performance, structure, data)
- **highlight_differences** (boolean) _(optional)_: Highlight key differences

---

### `create_trace_dashboard`

**Description:** Create dashboard for trace monitoring and analysis

**Parameters:**

- **dashboard_name** (string) **(required)**: Name for the trace dashboard
- **services** (array) **(required)**: Services to include in dashboard
- **metrics** (array) **(required)**: Trace metrics to visualize
- **layout** (object) _(optional)_: Dashboard layout configuration

---

## Audit & Compliance

### `query_audit_logs`

**Description:** Query audit logs for compliance and security monitoring

**Parameters:**

- **entity_type** (string) _(optional)_: Filter by entity type
- **entity_id** (string) _(optional)_: Filter by specific entity
- **user_id** (string) _(optional)_: Filter by user who performed action
- **action** (array) _(optional)_: Filter by action types
- **time_range** (object) **(required)**: Time range for audit query
- **include_details** (boolean) _(optional)_: Include detailed audit information

---

### `create_audit_report`

**Description:** Generate compliance and audit reports

**Parameters:**

- **report_type** (enum) **(required)**: Report type (access, changes, compliance, security)
- **filters** (object) **(required)**: Report filters and criteria
- **time_period** (object) **(required)**: Time period covered by report
- **format** (enum) **(required)**: Report format (pdf, excel, html)
- **group_by** (array) _(optional)_: Group report data by dimensions

---

### `track_data_lineage`

**Description:** Track data lineage and access patterns for audit

**Parameters:**

- **entity_type** (string) **(required)**: Entity type to track lineage for
- **entity_id** (string) **(required)**: Specific entity identifier
- **time_range** (object) **(required)**: Time range for lineage tracking
- **include_reads** (boolean) _(optional)_: Include read operations

---

### `compliance_audit`

**Description:** Perform compliance audit against regulations and policies

**Parameters:**

- **compliance_type** (enum) **(required)**: Compliance framework (gdpr, sox, hipaa, custom)
- **scope** (array) **(required)**: Audit scope (services, data, users)
- **detailed_report** (boolean) _(optional)_: Generate detailed compliance report

---

## Performance Profiling

### `profile_service`

**Description:** Profile service performance with detailed execution analysis

**Parameters:**

- **service_name** (string) **(required)**: Service to profile
- **profile_type** (enum) **(required)**: Profiling type (cpu, memory, network, io)
- **duration** (string) **(required)**: Profiling duration
- **sampling_rate** (number) _(optional)_: Profiling sampling rate

---

### `analyze_bottlenecks`

**Description:** Analyze performance bottlenecks across service interactions

**Parameters:**

- **service_name** (string) _(optional)_: Focus analysis on specific service
- **resource_type** (enum) **(required)**: Resource type (cpu, memory, database, network)
- **time_window** (string) **(required)**: Time window for bottleneck analysis
- **threshold_percentile** (number) _(optional)_: Performance threshold percentile

---

### `generate_flame_graph`

**Description:** Generate flame graph visualization for performance analysis

**Parameters:**

- **service_name** (string) **(required)**: Service to generate flame graph for
- **profile_data** (string) **(required)**: Profile data source or query
- **time_range** (object) **(required)**: Time range for flame graph
- **filter_threshold** (number) _(optional)_: Filter out functions below threshold

---

### `benchmark_api`

**Description:** Benchmark API performance with load testing

**Parameters:**

- **endpoint** (string) **(required)**: API endpoint to benchmark
- **load_profile** (object) **(required)**: Load testing configuration
- **collect_metrics** (array) _(optional)_: Additional metrics to collect

---

## Alerting & Notifications

### `create_alert_rule`

**Description:** Create intelligent alert rules with conditions and actions

**Parameters:**

- **rule_name** (string) **(required)**: Name for the alert rule
- **rule_type** (enum) **(required)**: Rule type (metric, log, trace, anomaly)
- **condition** (object) **(required)**: Alert condition configuration
- **severity** (enum) **(required)**: Alert severity level
- **notification_channels** (array) **(required)**: Notification channels and recipients
- **cooldown_period** (string) _(optional)_: Cooldown period between alerts

---

### `manage_alert_subscription`

**Description:** Manage user subscriptions to different alert types

**Parameters:**

- **action** (enum) **(required)**: Subscription action (subscribe, unsubscribe, update)
- **user_id** (string) **(required)**: User identifier for subscription
- **alert_types** (array) **(required)**: Alert types to manage
- **channels** (array) **(required)**: Notification channels for alerts
- **filters** (object) _(optional)_: Alert filters and preferences

---

### `acknowledge_alert`

**Description:** Acknowledge alerts to track resolution and reduce noise

**Parameters:**

- **alert_id** (string) **(required)**: Alert identifier to acknowledge
- **acknowledged_by** (string) **(required)**: Person acknowledging the alert
- **comment** (string) _(optional)_: Acknowledgment comment
- **expected_resolution** (timestamp) _(optional)_: Expected resolution time

---

### `get_alert_history`

**Description:** Retrieve historical alert data for analysis and trends

**Parameters:**

- **alert_name** (string) _(optional)_: Filter by specific alert rule
- **severity** (array) _(optional)_: Filter by severity levels
- **status** (array) _(optional)_: Filter by alert status
- **time_range** (object) **(required)**: Time range for alert history

---

## Dashboard & Visualization

### `create_dashboard`

**Description:** Create comprehensive monitoring dashboard with multiple panels

**Parameters:**

- **dashboard_name** (string) **(required)**: Name for the dashboard
- **panels** (array) **(required)**: Dashboard panels configuration
- **variables** (array) _(optional)_: Dashboard template variables
- **refresh_interval** (string) _(optional)_: Auto-refresh interval

---

### `export_dashboard`

**Description:** Export dashboard configuration and data

**Parameters:**

- **dashboard_id** (string) **(required)**: Dashboard to export
- **format** (enum) **(required)**: Export format (json, pdf, png)
- **include_data** (boolean) _(optional)_: Include current data in export

---

### `share_dashboard`

**Description:** Share dashboard with team members or external users

**Parameters:**

- **dashboard_id** (string) **(required)**: Dashboard to share
- **share_with** (array) **(required)**: Users or groups to share with
- **permission** (enum) **(required)**: Share permission level (view, edit, admin)
- **expiry** (timestamp) _(optional)_: Share link expiry time

---

## Advanced Analytics

### `analyze_trends`

**Description:** Analyze trends in telemetry data with predictive capabilities

**Parameters:**

- **data_source** (enum) **(required)**: Data source type (metrics, logs, traces)
- **trend_type** (enum) **(required)**: Trend analysis type (linear, seasonal, anomaly)
- **time_period** (object) **(required)**: Time period for trend analysis
- **prediction_window** (string) _(optional)_: Future prediction window

---

### `detect_anomalies`

**Description:** Detect anomalies in telemetry data using ML algorithms

**Parameters:**

- **data_source** (string) **(required)**: Data source or metric to analyze
- **algorithm** (enum) **(required)**: Anomaly detection algorithm
- **sensitivity** (number) **(required)**: Detection sensitivity level
- **training_period** (string) **(required)**: Historical data training period

---

### `correlate_events`

**Description:** Correlate events across different telemetry sources

**Parameters:**

- **event_types** (array) **(required)**: Types of events to correlate
- **time_window** (string) **(required)**: Time window for correlation analysis
- **correlation_threshold** (number) _(optional)_: Correlation significance threshold
- **include_causality** (boolean) _(optional)_: Analyze causal relationships

---

## Configuration

```json
{
  "--elasticsearch-url": "http://localhost:9200",
  "--prometheus-url": "http://localhost:9090",
  "--jaeger-url": "http://localhost:16686",
  "--kafka-brokers": "localhost:9092",
  "--retention-days": 30,
  "--sampling-rate": 0.1,
  "--buffer-size": 10000,
  "--flush-interval": "10s"
}
```