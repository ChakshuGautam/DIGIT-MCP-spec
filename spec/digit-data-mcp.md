# DIGIT Data MCP Tool Reference

## Table of Contents

- **[Data Querying & Search](#data-querying--search)** (4 tools)
  - [`query_data`](#query_data)
  - [`aggregate_data`](#aggregate_data)
  - [`join_data`](#join_data)
  - [`search_data`](#search_data)

- **[Data Pipeline Management](#data-pipeline-management)** (4 tools)
  - [`create_pipeline`](#create_pipeline)
  - [`run_pipeline`](#run_pipeline)
  - [`monitor_pipeline`](#monitor_pipeline)
  - [`validate_pipeline`](#validate_pipeline)

- **[Data Quality & Validation](#data-quality--validation)** (4 tools)
  - [`profile_data`](#profile_data)
  - [`validate_data_quality`](#validate_data_quality)
  - [`cleanse_data`](#cleanse_data)
  - [`detect_anomalies`](#detect_anomalies)

- **[Data Migration & Synchronization](#data-migration--synchronization)** (3 tools)
  - [`migrate_data`](#migrate_data)
  - [`sync_data`](#sync_data)
  - [`archive_data`](#archive_data)

- **[Backup & Recovery](#backup--recovery)** (4 tools)
  - [`restore_data`](#restore_data)
  - [`create_backup`](#create_backup)
  - [`list_backups`](#list_backups)
  - [`verify_backup`](#verify_backup)

- **[Analytics & Reporting](#analytics--reporting)** (4 tools)
  - [`run_analytics`](#run_analytics)
  - [`create_dashboard`](#create_dashboard)
  - [`generate_report`](#generate_report)
  - [`calculate_metrics`](#calculate_metrics)

- **[Data Lineage & Documentation](#data-lineage--documentation)** (3 tools)
  - [`trace_data_lineage`](#trace_data_lineage)
  - [`document_schema`](#document_schema)
  - [`map_relationships`](#map_relationships)

- **[Performance Optimization](#performance-optimization)** (3 tools)
  - [`optimize_query`](#optimize_query)
  - [`analyze_table_statistics`](#analyze_table_statistics)
  - [`rebuild_indices`](#rebuild_indices)

## Data Querying & Search

### `query_data`

**Description:** Execute SQL, NoSQL, or API queries across multiple data sources

**Parameters:**

- **query_type** (enum) **(required)**: Type of query (sql, nosql, api, graphql)
- **query** (string) **(required)**: Query statement or expression
- **datasource** (string) **(required)**: Target data source identifier
- **tenant_id** (string) _(optional)_: Tenant context for multi-tenant queries
- **timeout** (number) _(optional)_: Query timeout in seconds
- **limit** (number) _(optional)_: Maximum number of results to return

---

### `aggregate_data`

**Description:** Perform data aggregations with grouping and filtering

**Parameters:**

- **entity_type** (string) **(required)**: Entity type to aggregate
- **aggregations** (array) **(required)**: Aggregation functions (sum, count, avg, min, max)
- **group_by** (array) _(optional)_: Fields to group aggregations by
- **filters** (object) _(optional)_: Filter conditions for aggregation
- **time_range** (object) _(optional)_: Time-based filtering for aggregation

---

### `join_data`

**Description:** Join data from multiple sources with relationship mapping

**Parameters:**

- **primary_source** (object) **(required)**: Primary data source configuration
- **joins** (array) **(required)**: Join configurations with other sources
- **output_format** (enum) _(optional)_: Output format (json, csv, parquet)

---

### `search_data`

**Description:** Full-text search across indexed data with advanced filtering

**Parameters:**

- **search_text** (string) **(required)**: Text to search for
- **indices** (array) _(optional)_: Specific indices to search in
- **entity_types** (array) _(optional)_: Entity types to include in search
- **fields** (array) _(optional)_: Specific fields to search
- **fuzzy** (boolean) _(optional)_: Enable fuzzy matching
- **boost_fields** (object) _(optional)_: Field-specific search boost weights

---

## Data Pipeline Management

### `create_pipeline`

**Description:** Create ETL/ELT data pipeline with transformations and scheduling

**Parameters:**

- **pipeline_name** (string) **(required)**: Unique name for the pipeline
- **source** (object) **(required)**: Source data configuration
- **transformations** (array) **(required)**: Data transformation steps
- **destination** (object) **(required)**: Destination configuration
- **schedule** (string) _(optional)_: Cron expression for pipeline scheduling

---

### `run_pipeline`

**Description:** Execute data pipeline with monitoring and error handling

**Parameters:**

- **pipeline_name** (string) **(required)**: Name of pipeline to execute
- **mode** (enum) **(required)**: Execution mode (full, incremental, test)
- **parameters** (object) _(optional)_: Runtime parameters for pipeline
- **async** (boolean) _(optional)_: Run pipeline asynchronously

---

### `monitor_pipeline`

**Description:** Monitor pipeline execution status and performance metrics

**Parameters:**

- **pipeline_name** (string) _(optional)_: Specific pipeline to monitor
- **execution_id** (string) _(optional)_: Specific execution to monitor
- **status_filter** (array) _(optional)_: Filter by execution status
- **include_metrics** (boolean) _(optional)_: Include performance metrics

---

### `validate_pipeline`

**Description:** Validate pipeline configuration and test with sample data

**Parameters:**

- **pipeline_config** (object) **(required)**: Pipeline configuration to validate
- **dry_run** (boolean) _(optional)_: Perform dry run without data processing
- **sample_size** (number) _(optional)_: Size of sample data for testing

---

## Data Quality & Validation

### `profile_data`

**Description:** Generate comprehensive data profile with statistics and patterns

**Parameters:**

- **entity_type** (string) **(required)**: Entity type to profile
- **tenant_id** (string) **(required)**: Tenant context for data profiling
- **checks** (array) _(optional)_: Specific data quality checks to run
- **sample_size** (number) _(optional)_: Sample size for profiling analysis

---

### `validate_data_quality`

**Description:** Validate data against quality rules and business constraints

**Parameters:**

- **entity_type** (string) **(required)**: Entity type to validate
- **rules** (array) **(required)**: Data quality rules to apply
- **action_on_failure** (enum) _(optional)_: Action when validation fails (log, alert, reject)

---

### `cleanse_data`

**Description:** Clean and standardize data using configurable rules

**Parameters:**

- **entity_type** (string) **(required)**: Entity type to cleanse
- **cleansing_rules** (array) **(required)**: Data cleansing rules to apply
- **backup_original** (boolean) _(optional)_: Create backup before cleansing

---

### `detect_anomalies`

**Description:** Detect anomalies in data patterns using statistical methods

**Parameters:**

- **entity_type** (string) **(required)**: Entity type to analyze
- **method** (enum) **(required)**: Anomaly detection method (statistical, ml, rule-based)
- **sensitivity** (number) _(optional)_: Sensitivity level for anomaly detection
- **time_window** (string) _(optional)_: Time window for anomaly analysis

---

## Data Migration & Synchronization

### `migrate_data`

**Description:** Migrate data between systems with validation and rollback

**Parameters:**

- **source** (object) **(required)**: Source system configuration
- **destination** (object) **(required)**: Destination system configuration
- **mapping** (object) **(required)**: Field mapping between source and destination
- **validation_rules** (array) _(optional)_: Rules to validate migrated data
- **batch_size** (number) _(optional)_: Number of records per batch
- **parallel_threads** (number) _(optional)_: Number of parallel processing threads

---

### `sync_data`

**Description:** Synchronize data between systems with conflict resolution

**Parameters:**

- **source_entity** (string) **(required)**: Source entity type
- **target_entity** (string) **(required)**: Target entity type
- **sync_mode** (enum) **(required)**: Synchronization mode (full, incremental, bidirectional)
- **conflict_resolution** (enum) _(optional)_: Conflict resolution strategy
- **field_mapping** (object) _(optional)_: Field mappings between entities

---

### `archive_data`

**Description:** Archive old data with retention policies and compression

**Parameters:**

- **entity_type** (string) **(required)**: Entity type to archive
- **criteria** (object) **(required)**: Archival criteria (age, status, etc.)
- **destination** (string) **(required)**: Archive destination path or storage
- **retention_period** (string) _(optional)_: Data retention period
- **compression** (boolean) _(optional)_: Enable data compression

---

## Backup & Recovery

### `restore_data`

**Description:** Restore data from backup with integrity verification

**Parameters:**

- **backup_id** (string) **(required)**: Backup identifier to restore from
- **restore_point** (timestamp) _(optional)_: Point-in-time to restore to
- **target_location** (string) _(optional)_: Target location for restored data
- **validate_integrity** (boolean) _(optional)_: Verify data integrity after restore

---

### `create_backup`

**Description:** Create data backup with encryption and compression options

**Parameters:**

- **backup_name** (string) **(required)**: Name for the backup
- **entities** (array) **(required)**: Entities to include in backup
- **backup_type** (enum) **(required)**: Backup type (full, incremental, differential)
- **compression** (boolean) _(optional)_: Enable backup compression
- **encryption** (boolean) _(optional)_: Enable backup encryption

---

### `list_backups`

**Description:** List available backups with filtering and metadata

**Parameters:**

- **entity_type** (string) _(optional)_: Filter backups by entity type
- **date_range** (object) _(optional)_: Filter by backup creation date
- **status** (array) _(optional)_: Filter by backup status

---

### `verify_backup`

**Description:** Verify backup integrity and completeness

**Parameters:**

- **backup_id** (string) **(required)**: Backup identifier to verify
- **deep_check** (boolean) _(optional)_: Perform comprehensive integrity check

---

## Analytics & Reporting

### `run_analytics`

**Description:** Execute analytics workloads with advanced processing

**Parameters:**

- **analysis_type** (string) **(required)**: Type of analysis to perform
- **parameters** (object) **(required)**: Analysis parameters and configuration
- **output_format** (enum) _(optional)_: Output format for results
- **visualization** (object) _(optional)_: Visualization configuration

---

### `create_dashboard`

**Description:** Create interactive dashboard with multiple data widgets

**Parameters:**

- **dashboard_name** (string) **(required)**: Name for the dashboard
- **widgets** (array) **(required)**: Dashboard widget configurations
- **refresh_interval** (string) _(optional)_: Auto-refresh interval
- **filters** (array) _(optional)_: Global dashboard filters

---

### `generate_report`

**Description:** Generate formatted reports with data visualization

**Parameters:**

- **report_type** (string) **(required)**: Type of report to generate
- **parameters** (object) **(required)**: Report parameters and filters
- **format** (enum) **(required)**: Report format (pdf, excel, html, json)
- **schedule** (string) _(optional)_: Schedule for recurring reports
- **recipients** (array) _(optional)_: Report distribution list

---

### `calculate_metrics`

**Description:** Calculate business metrics and KPIs over time periods

**Parameters:**

- **metric_name** (string) **(required)**: Name of metric to calculate
- **time_period** (object) **(required)**: Time period for calculation
- **dimensions** (array) _(optional)_: Dimensions to group metrics by
- **filters** (object) _(optional)_: Filters to apply before calculation

---

## Data Lineage & Documentation

### `trace_data_lineage`

**Description:** Trace data flow and dependencies across systems

**Parameters:**

- **entity_id** (string) **(required)**: Entity to trace lineage for
- **direction** (enum) **(required)**: Tracing direction (upstream, downstream, both)
- **depth** (number) _(optional)_: Maximum depth to trace
- **include_transformations** (boolean) _(optional)_: Include transformation details

---

### `document_schema`

**Description:** Generate comprehensive schema documentation

**Parameters:**

- **entity_type** (string) **(required)**: Entity type to document
- **version** (string) _(optional)_: Specific schema version
- **format** (enum) _(optional)_: Documentation format (markdown, html, json)
- **include_samples** (boolean) _(optional)_: Include sample data

---

### `map_relationships`

**Description:** Map and visualize entity relationships and dependencies

**Parameters:**

- **root_entity** (string) **(required)**: Starting entity for relationship mapping
- **depth** (number) _(optional)_: Maximum relationship depth to map
- **relationship_types** (array) _(optional)_: Types of relationships to include
- **output_format** (enum) _(optional)_: Output format for relationship map

---

## Performance Optimization

### `optimize_query`

**Description:** Analyze and optimize database queries for better performance

**Parameters:**

- **query** (string) **(required)**: Query to optimize
- **datasource** (string) **(required)**: Target database system
- **explain_plan** (boolean) _(optional)_: Generate query execution plan
- **suggest_indices** (boolean) _(optional)_: Suggest index improvements

---

### `analyze_table_statistics`

**Description:** Analyze table statistics for query optimization

**Parameters:**

- **table_name** (string) **(required)**: Table to analyze
- **compute_statistics** (boolean) _(optional)_: Compute fresh statistics
- **include_indices** (boolean) _(optional)_: Include index statistics

---

### `rebuild_indices`

**Description:** Rebuild database indices for improved query performance

**Parameters:**

- **entity_type** (string) **(required)**: Entity type to rebuild indices for
- **indices** (array) _(optional)_: Specific indices to rebuild
- **online** (boolean) _(optional)_: Perform online rebuild without downtime

---

## Configuration

```json
{
  "--data-warehouse-url": "jdbc:postgresql://localhost:5432/analytics",
  "--elasticsearch-url": "http://localhost:9200",
  "--kafka-brokers": "localhost:9092",
  "--batch-size": 1000,
  "--parallel-threads": 4,
  "--cache-enabled": true,
  "--compression": "gzip",
  "--retention-days": 90
}
```