# DIGIT Dashboard & Analytics MCP Tool Reference

## Table of Contents

- **[Dashboard Management](#dashboard-management)** (5 tools)
  - [`create_dashboard`](#create_dashboard)
  - [`update_dashboard`](#update_dashboard)
  - [`clone_dashboard`](#clone_dashboard)
  - [`delete_dashboard`](#delete_dashboard)
  - [`publish_dashboard`](#publish_dashboard)

- **[Chart Configuration](#chart-configuration)** (6 tools)
  - [`create_chart`](#create_chart)
  - [`configure_chart_data`](#configure_chart_data)
  - [`set_chart_visualization`](#set_chart_visualization)
  - [`add_chart_filters`](#add_chart_filters)
  - [`configure_drill_down`](#configure_drill_down)
  - [`set_chart_thresholds`](#set_chart_thresholds)

- **[Data Pipeline](#data-pipeline)** (5 tools)
  - [`configure_data_source`](#configure_data_source)
  - [`create_data_aggregation`](#create_data_aggregation)
  - [`setup_kafka_pipeline`](#setup_kafka_pipeline)
  - [`configure_elasticsearch_index`](#configure_elasticsearch_index)
  - [`setup_data_transformation`](#setup_data_transformation)

- **[KPI Management](#kpi-management)** (4 tools)
  - [`define_kpi`](#define_kpi)
  - [`calculate_kpi_metrics`](#calculate_kpi_metrics)
  - [`set_kpi_targets`](#set_kpi_targets)
  - [`track_kpi_performance`](#track_kpi_performance)

- **[Real-time Analytics](#real-time-analytics)** (4 tools)
  - [`create_realtime_widget`](#create_realtime_widget)
  - [`setup_event_stream`](#setup_event_stream)
  - [`configure_live_updates`](#configure_live_updates)
  - [`create_alert_rule`](#create_alert_rule)

- **[Report Generation](#report-generation)** (5 tools)
  - [`generate_report`](#generate_report)
  - [`schedule_report`](#schedule_report)
  - [`export_dashboard_data`](#export_dashboard_data)
  - [`create_report_template`](#create_report_template)
  - [`distribute_report`](#distribute_report)

- **[Access Control](#access-control)** (3 tools)
  - [`set_dashboard_permissions`](#set_dashboard_permissions)
  - [`create_role_based_view`](#create_role_based_view)
  - [`configure_data_masking`](#configure_data_masking)

- **[DSS Integration](#dss-integration)** (4 tools)
  - [`configure_dss_ingest`](#configure_dss_ingest)
  - [`setup_enrichment_pipeline`](#setup_enrichment_pipeline)
  - [`configure_master_dashboard`](#configure_master_dashboard)
  - [`sync_dss_collections`](#sync_dss_collections)

## Dashboard Management

### `create_dashboard`

**Description:** Create new dashboard with layout and widget configuration

**Parameters:**
- **dashboard_name** (string) **(required)**: Name of the dashboard
- **dashboard_type** (enum) **(required)**: Type (operational, management, citizen, dss)
- **layout** (object) **(required)**: Grid layout configuration
- **widgets** (array) **(required)**: Initial widget configurations
- **refresh_interval** (number) _(optional)_: Auto-refresh interval in seconds
- **filters** (array) _(optional)_: Global dashboard filters

---

### `update_dashboard`

**Description:** Update existing dashboard configuration and layout

**Parameters:**
- **dashboard_id** (string) **(required)**: Dashboard identifier
- **updates** (object) **(required)**: Dashboard configuration updates
- **version** (string) _(optional)_: Version for change tracking
- **preserve_state** (boolean) _(optional)_: Preserve user customizations

---

### `clone_dashboard`

**Description:** Clone existing dashboard with modifications

**Parameters:**
- **source_dashboard_id** (string) **(required)**: Source dashboard to clone
- **new_name** (string) **(required)**: Name for cloned dashboard
- **modifications** (object) _(optional)_: Changes to apply to clone
- **target_tenant** (string) _(optional)_: Target tenant for clone

---

### `delete_dashboard`

**Description:** Delete dashboard and associated configurations

**Parameters:**
- **dashboard_id** (string) **(required)**: Dashboard to delete
- **cascade** (boolean) _(optional)_: Delete associated widgets and data
- **archive** (boolean) _(optional)_: Archive instead of permanent deletion

---

### `publish_dashboard`

**Description:** Publish dashboard to production environment

**Parameters:**
- **dashboard_id** (string) **(required)**: Dashboard to publish
- **environment** (enum) **(required)**: Target environment (dev, staging, prod)
- **access_level** (enum) **(required)**: Access level (public, restricted, private)
- **notification_list** (array) _(optional)_: Users to notify about publication

---

## Chart Configuration

### `create_chart`

**Description:** Create chart visualization with data binding

**Parameters:**
- **chart_name** (string) **(required)**: Name of the chart
- **chart_type** (enum) **(required)**: Type (line, bar, pie, donut, table, metric, heatmap)
- **data_source** (object) **(required)**: Data source configuration
- **aggregation** (object) **(required)**: Data aggregation rules
- **visualization** (object) **(required)**: Visual properties and styling

---

### `configure_chart_data`

**Description:** Configure chart data source and queries

**Parameters:**
- **chart_id** (string) **(required)**: Chart identifier
- **query_type** (enum) **(required)**: Query type (elasticsearch, sql, api)
- **query** (object) **(required)**: Query configuration
- **mappings** (object) **(required)**: Field mappings for chart
- **cache_config** (object) _(optional)_: Caching configuration

---

### `set_chart_visualization`

**Description:** Configure chart visual properties and styling

**Parameters:**
- **chart_id** (string) **(required)**: Chart identifier
- **colors** (array) **(required)**: Color palette configuration
- **axes** (object) **(required)**: Axes configuration (labels, scales)
- **legend** (object) _(optional)_: Legend configuration
- **annotations** (array) _(optional)_: Chart annotations and markers

---

### `add_chart_filters`

**Description:** Add interactive filters to chart

**Parameters:**
- **chart_id** (string) **(required)**: Chart identifier
- **filter_type** (enum) **(required)**: Filter type (dropdown, range, date, search)
- **filter_field** (string) **(required)**: Field to filter on
- **filter_config** (object) **(required)**: Filter configuration
- **default_value** (any) _(optional)_: Default filter value

---

### `configure_drill_down`

**Description:** Setup drill-down navigation for chart interactions

**Parameters:**
- **chart_id** (string) **(required)**: Chart identifier
- **drill_levels** (array) **(required)**: Drill-down hierarchy levels
- **target_dashboard** (string) _(optional)_: Dashboard to navigate to
- **context_params** (array) _(optional)_: Parameters to pass on drill-down

---

### `set_chart_thresholds`

**Description:** Configure threshold alerts and visual indicators

**Parameters:**
- **chart_id** (string) **(required)**: Chart identifier
- **thresholds** (array) **(required)**: Threshold configurations
- **visual_indicators** (object) **(required)**: Visual threshold indicators
- **alert_config** (object) _(optional)_: Alert configuration for threshold breach

---

## Data Pipeline

### `configure_data_source`

**Description:** Setup data source connection for analytics

**Parameters:**
- **source_type** (enum) **(required)**: Source type (postgres, elasticsearch, kafka, api)
- **connection_config** (object) **(required)**: Connection configuration
- **sync_schedule** (object) **(required)**: Data sync schedule
- **transformation_rules** (array) _(optional)_: Data transformation rules

---

### `create_data_aggregation`

**Description:** Create data aggregation pipeline for analytics

**Parameters:**
- **aggregation_name** (string) **(required)**: Name of aggregation
- **source_collection** (string) **(required)**: Source data collection
- **aggregation_rules** (array) **(required)**: Aggregation rule definitions
- **output_format** (object) **(required)**: Output data format
- **schedule** (object) _(optional)_: Aggregation schedule

---

### `setup_kafka_pipeline`

**Description:** Configure Kafka streaming pipeline for real-time data

**Parameters:**
- **pipeline_name** (string) **(required)**: Pipeline identifier
- **kafka_config** (object) **(required)**: Kafka connection configuration
- **topics** (array) **(required)**: Kafka topics to consume
- **processing_rules** (array) **(required)**: Stream processing rules
- **sink_config** (object) **(required)**: Data sink configuration

---

### `configure_elasticsearch_index`

**Description:** Setup Elasticsearch index for analytics queries

**Parameters:**
- **index_name** (string) **(required)**: Elasticsearch index name
- **mapping** (object) **(required)**: Index mapping configuration
- **settings** (object) **(required)**: Index settings (shards, replicas)
- **lifecycle_policy** (object) _(optional)_: Index lifecycle management

---

### `setup_data_transformation`

**Description:** Configure data transformation and enrichment rules

**Parameters:**
- **transformation_name** (string) **(required)**: Transformation identifier
- **source_schema** (object) **(required)**: Source data schema
- **target_schema** (object) **(required)**: Target data schema
- **transformation_rules** (array) **(required)**: Transformation rule set
- **enrichment_config** (object) _(optional)_: Data enrichment configuration

---

## KPI Management

### `define_kpi`

**Description:** Define key performance indicator with calculation rules

**Parameters:**
- **kpi_name** (string) **(required)**: KPI identifier
- **category** (string) **(required)**: KPI category
- **calculation_formula** (object) **(required)**: KPI calculation formula
- **data_sources** (array) **(required)**: Required data sources
- **aggregation_period** (enum) **(required)**: Period (daily, weekly, monthly)
- **unit** (string) _(optional)_: KPI unit of measurement

---

### `calculate_kpi_metrics`

**Description:** Calculate KPI metrics for specified period

**Parameters:**
- **kpi_id** (string) **(required)**: KPI identifier
- **date_range** (object) **(required)**: Calculation period
- **filters** (object) _(optional)_: Additional filters
- **comparison_period** (object) _(optional)_: Period for comparison

---

### `set_kpi_targets`

**Description:** Set performance targets and benchmarks for KPIs

**Parameters:**
- **kpi_id** (string) **(required)**: KPI identifier
- **targets** (array) **(required)**: Target configurations
- **benchmark_type** (enum) **(required)**: Benchmark type (absolute, relative, percentile)
- **alert_thresholds** (object) _(optional)_: Alert threshold configuration

---

### `track_kpi_performance`

**Description:** Track KPI performance against targets

**Parameters:**
- **kpi_ids** (array) **(required)**: KPIs to track
- **tracking_period** (object) **(required)**: Performance tracking period
- **include_trends** (boolean) _(optional)_: Include trend analysis
- **include_predictions** (boolean) _(optional)_: Include predictive analytics

---

## Real-time Analytics

### `create_realtime_widget`

**Description:** Create widget for real-time data visualization

**Parameters:**
- **widget_name** (string) **(required)**: Widget identifier
- **widget_type** (enum) **(required)**: Widget type (counter, gauge, timeline, map)
- **data_stream** (object) **(required)**: Real-time data stream configuration
- **update_frequency** (number) **(required)**: Update frequency in milliseconds
- **aggregation_window** (object) _(optional)_: Time window for aggregation

---

### `setup_event_stream`

**Description:** Configure event stream for real-time analytics

**Parameters:**
- **stream_name** (string) **(required)**: Stream identifier
- **event_source** (object) **(required)**: Event source configuration
- **event_filters** (array) **(required)**: Event filtering rules
- **processing_logic** (object) **(required)**: Event processing logic

---

### `configure_live_updates`

**Description:** Setup live update mechanism for dashboards

**Parameters:**
- **dashboard_id** (string) **(required)**: Dashboard to enable live updates
- **update_strategy** (enum) **(required)**: Update strategy (push, poll, websocket)
- **update_rules** (array) **(required)**: Rules for triggering updates
- **throttle_config** (object) _(optional)_: Update throttling configuration

---

### `create_alert_rule`

**Description:** Create alert rule for real-time monitoring

**Parameters:**
- **alert_name** (string) **(required)**: Alert identifier
- **condition** (object) **(required)**: Alert trigger condition
- **severity** (enum) **(required)**: Alert severity (critical, warning, info)
- **notification_channels** (array) **(required)**: Notification configuration
- **cooldown_period** (number) _(optional)_: Alert cooldown in seconds

---

## Report Generation

### `generate_report`

**Description:** Generate analytical report from dashboard data

**Parameters:**
- **report_type** (enum) **(required)**: Report type (pdf, excel, csv, html)
- **dashboard_id** (string) **(required)**: Source dashboard
- **date_range** (object) **(required)**: Report period
- **sections** (array) **(required)**: Report sections to include
- **format_options** (object) _(optional)_: Formatting preferences

---

### `schedule_report`

**Description:** Schedule periodic report generation and distribution

**Parameters:**
- **report_config** (object) **(required)**: Report configuration
- **schedule** (object) **(required)**: Schedule configuration (cron format)
- **recipients** (array) **(required)**: Report recipients
- **delivery_method** (enum) **(required)**: Delivery method (email, sftp, api)

---

### `export_dashboard_data`

**Description:** Export dashboard data in various formats

**Parameters:**
- **dashboard_id** (string) **(required)**: Dashboard to export
- **export_format** (enum) **(required)**: Export format (json, csv, excel)
- **date_range** (object) **(required)**: Data period to export
- **include_metadata** (boolean) _(optional)_: Include metadata in export

---

### `create_report_template`

**Description:** Create reusable report template

**Parameters:**
- **template_name** (string) **(required)**: Template identifier
- **layout** (object) **(required)**: Report layout configuration
- **data_bindings** (array) **(required)**: Data binding configurations
- **styling** (object) **(required)**: Report styling configuration

---

### `distribute_report`

**Description:** Distribute generated report to stakeholders

**Parameters:**
- **report_id** (string) **(required)**: Report to distribute
- **distribution_list** (array) **(required)**: Distribution recipients
- **channels** (array) **(required)**: Distribution channels
- **message** (string) _(optional)_: Accompanying message

---

## Access Control

### `set_dashboard_permissions`

**Description:** Configure role-based access for dashboards

**Parameters:**
- **dashboard_id** (string) **(required)**: Dashboard identifier
- **permissions** (array) **(required)**: Permission configurations
- **inherit_from** (string) _(optional)_: Parent dashboard for inheritance

---

### `create_role_based_view`

**Description:** Create customized dashboard view based on user role

**Parameters:**
- **base_dashboard_id** (string) **(required)**: Base dashboard
- **role** (string) **(required)**: Target user role
- **visible_widgets** (array) **(required)**: Widgets visible to role
- **data_filters** (array) _(optional)_: Role-specific data filters

---

### `configure_data_masking`

**Description:** Setup data masking rules for sensitive information

**Parameters:**
- **dashboard_id** (string) **(required)**: Dashboard identifier
- **masking_rules** (array) **(required)**: Data masking configurations
- **exempt_roles** (array) _(optional)_: Roles exempt from masking

---

## DSS Integration

### `configure_dss_ingest`

**Description:** Configure DSS data ingestion pipeline

**Parameters:**
- **ingest_name** (string) **(required)**: Ingestion pipeline name
- **source_system** (string) **(required)**: Source system identifier
- **collection_config** (object) **(required)**: Collection configuration
- **transform_config** (object) **(required)**: Transformation rules
- **target_index** (string) **(required)**: Target ES index

---

### `setup_enrichment_pipeline`

**Description:** Setup data enrichment for DSS analytics

**Parameters:**
- **pipeline_name** (string) **(required)**: Enrichment pipeline name
- **source_data** (object) **(required)**: Source data configuration
- **enrichment_sources** (array) **(required)**: Enrichment data sources
- **merge_rules** (array) **(required)**: Data merge rules

---

### `configure_master_dashboard`

**Description:** Configure DSS master dashboard with KPIs

**Parameters:**
- **dashboard_name** (string) **(required)**: Master dashboard name
- **service_modules** (array) **(required)**: Service modules to include
- **kpi_categories** (array) **(required)**: KPI categories
- **layout_template** (string) **(required)**: Layout template

---

### `sync_dss_collections`

**Description:** Synchronize DSS data collections with source systems

**Parameters:**
- **collections** (array) **(required)**: Collections to sync
- **sync_mode** (enum) **(required)**: Sync mode (full, incremental, delta)
- **conflict_resolution** (enum) _(optional)_: Conflict resolution strategy

---

## Configuration

```json
{
  "--dss-host": "https://dss.digit.org",
  "--elasticsearch-url": "http://elasticsearch:9200",
  "--kafka-brokers": "kafka:9092",
  "--postgres-connection": "postgresql://user:pass@localhost:5432/analytics",
  "--cache-redis": "redis://localhost:6379",
  "--refresh-interval": 30,
  "--max-query-size": 10000,
  "--aggregation-workers": 4,
  "--realtime-buffer": 1000
}
```