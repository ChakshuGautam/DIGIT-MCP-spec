# DIGIT MDMS MCP Tool Reference

## Table of Contents

- **[Master Data Management](#master-data-management)** (6 tools)
  - [`create_master`](#create_master)
  - [`update_master`](#update_master)
  - [`delete_master`](#delete_master)
  - [`search_master`](#search_master)
  - [`get_all_masters`](#get_all_masters)
  - [`get_master_by_code`](#get_master_by_code)

- **[Data Validation & Import/Export](#data-validation--importexport)** (4 tools)
  - [`validate_master_data`](#validate_master_data)
  - [`import_master_data`](#import_master_data)
  - [`export_master_data`](#export_master_data)
  - [`get_master_config`](#get_master_config)

- **[Cache Management](#cache-management)** (1 tool)
  - [`reload_mdms_cache`](#reload_mdms_cache)

- **[Tenant Management](#tenant-management)** (3 tools)
  - [`get_tenant_hierarchy`](#get_tenant_hierarchy)
  - [`create_tenant`](#create_tenant)
  - [`update_tenant`](#update_tenant)

- **[Data Migration & Versioning](#data-migration--versioning)** (8 tools)
  - [`migrate_master_data`](#migrate_master_data)
  - [`version_master_data`](#version_master_data)
  - [`rollback_master_version`](#rollback_master_version)
  - [`diff_master_versions`](#diff_master_versions)
  - [`bulk_update_masters`](#bulk_update_masters)
  - [`get_master_dependencies`](#get_master_dependencies)
  - [`validate_tenant_masters`](#validate_tenant_masters)

## Master Data Management

### `create_master`

**Description:** Create new master data entry in specified module and tenant

**Parameters:**

- **module** (string) **(required)**: MDMS module name (e.g., 'common-masters', 'tenant')
- **master** (string) **(required)**: Master data type (e.g., 'Department', 'Designation')
- **tenant_id** (string) **(required)**: Tenant identifier for multi-tenancy
- **data** (object) **(required)**: Master data payload with code and other fields
- **effective_from** (timestamp) _(optional)_: Effective date for the master data

---

### `update_master`

**Description:** Update existing master data entry with versioning support

**Parameters:**

- **module** (string) **(required)**: MDMS module name
- **master** (string) **(required)**: Master data type
- **tenant_id** (string) **(required)**: Tenant identifier for multi-tenancy
- **data** (object) **(required)**: Updated master data payload
- **version** (string) _(optional)_: Version identifier for the update

---

### `delete_master`

**Description:** Delete or soft-delete master data entry by code

**Parameters:**

- **module** (string) **(required)**: MDMS module name
- **master** (string) **(required)**: Master data type
- **tenant_id** (string) **(required)**: Tenant identifier for multi-tenancy
- **code** (string) **(required)**: Master data code to delete
- **soft_delete** (boolean) _(optional)_: Perform soft delete instead of hard delete

---

### `search_master`

**Description:** Search master data with filters and return unique or all matches

**Parameters:**

- **module** (string) **(required)**: MDMS module name
- **master** (string) **(required)**: Master data type
- **tenant_id** (string) **(required)**: Tenant identifier for multi-tenancy
- **filters** (object) _(optional)_: Search filters and criteria
- **unique** (boolean) _(optional)_: Return only unique values

---

### `get_all_masters`

**Description:** Retrieve all master data for tenant with optional module filtering

**Parameters:**

- **tenant_id** (string) **(required)**: Tenant identifier for multi-tenancy
- **module** (string) _(optional)_: Filter by specific module
- **include_state** (boolean) _(optional)_: Include state-level master data

---

### `get_master_by_code`

**Description:** Retrieve specific master data entry by its unique code

**Parameters:**

- **module** (string) **(required)**: MDMS module name
- **master** (string) **(required)**: Master data type
- **code** (string) **(required)**: Master data code to retrieve
- **tenant_id** (string) **(required)**: Tenant identifier for multi-tenancy

---

## Data Validation & Import/Export

### `validate_master_data`

**Description:** Validate master data against schema and business rules

**Parameters:**

- **module** (string) **(required)**: MDMS module name
- **master** (string) **(required)**: Master data type
- **data** (object) **(required)**: Master data to validate
- **tenant_id** (string) **(required)**: Tenant identifier for multi-tenancy

---

### `import_master_data`

**Description:** Import master data from file with format validation

**Parameters:**

- **module** (string) **(required)**: MDMS module name
- **master** (string) **(required)**: Master data type
- **tenant_id** (string) **(required)**: Tenant identifier for multi-tenancy
- **file_url** (string) **(required)**: URL or path to import file
- **format** (string) _(optional)_: File format (json, csv, excel)

---

### `export_master_data`

**Description:** Export master data to various formats for backup or transfer

**Parameters:**

- **module** (string) _(optional)_: Filter by specific module
- **master** (string) _(optional)_: Filter by specific master type
- **tenant_id** (string) **(required)**: Tenant identifier for multi-tenancy
- **format** (string) **(required)**: Export format (json, csv, excel)

---

### `get_master_config`

**Description:** Retrieve configuration schema for master data type

**Parameters:**

- **module** (string) **(required)**: MDMS module name
- **master** (string) **(required)**: Master data type
- **tenant_id** (string) **(required)**: Tenant identifier for multi-tenancy

---

## Cache Management

### `reload_mdms_cache`

**Description:** Refresh MDMS cache for improved performance

**Parameters:**

- **module** (string) _(optional)_: Reload specific module cache
- **master** (string) _(optional)_: Reload specific master cache
- **tenant_id** (string) **(required)**: Tenant identifier for multi-tenancy

---

## Tenant Management

### `get_tenant_hierarchy`

**Description:** Retrieve hierarchical structure of tenant relationships

**Parameters:**

- **tenant_id** (string) **(required)**: Root tenant identifier
- **hierarchy_type** (string) _(optional)_: Type of hierarchy to retrieve

---

### `create_tenant`

**Description:** Create new tenant with initial configuration

**Parameters:**

- **tenant_data** (object) **(required)**: Tenant configuration and metadata
- **parent_tenant** (string) _(optional)_: Parent tenant for hierarchy

---

### `update_tenant`

**Description:** Update tenant configuration and properties

**Parameters:**

- **tenant_id** (string) **(required)**: Tenant identifier to update
- **updates** (object) **(required)**: Tenant property updates

---

## Data Migration & Versioning

### `migrate_master_data`

**Description:** Migrate master data between tenants with selective modules

**Parameters:**

- **source_tenant** (string) **(required)**: Source tenant identifier
- **target_tenant** (string) **(required)**: Target tenant identifier
- **modules** (array) _(optional)_: Modules to migrate (all if not specified)
- **overwrite** (boolean) _(optional)_: Overwrite existing data in target

---

### `version_master_data`

**Description:** Create versioned snapshot of master data with tags

**Parameters:**

- **module** (string) **(required)**: MDMS module name
- **master** (string) **(required)**: Master data type
- **tenant_id** (string) **(required)**: Tenant identifier for multi-tenancy
- **version_tag** (string) **(required)**: Version tag for the snapshot

---

### `rollback_master_version`

**Description:** Rollback master data to previous version

**Parameters:**

- **module** (string) **(required)**: MDMS module name
- **master** (string) **(required)**: Master data type
- **tenant_id** (string) **(required)**: Tenant identifier for multi-tenancy
- **target_version** (string) **(required)**: Version to rollback to

---

### `diff_master_versions`

**Description:** Compare differences between two master data versions

**Parameters:**

- **module** (string) **(required)**: MDMS module name
- **master** (string) **(required)**: Master data type
- **tenant_id** (string) **(required)**: Tenant identifier for multi-tenancy
- **version1** (string) **(required)**: First version for comparison
- **version2** (string) **(required)**: Second version for comparison

---

### `bulk_update_masters`

**Description:** Update multiple master data entries in single atomic operation

**Parameters:**

- **updates** (array) **(required)**: Array of master data updates
- **tenant_id** (string) **(required)**: Tenant identifier for multi-tenancy
- **atomic** (boolean) _(optional)_: Perform as atomic transaction

---

### `get_master_dependencies`

**Description:** Identify dependencies between master data entries

**Parameters:**

- **module** (string) **(required)**: MDMS module name
- **master** (string) **(required)**: Master data type
- **tenant_id** (string) **(required)**: Tenant identifier for multi-tenancy

---

### `validate_tenant_masters`

**Description:** Validate all master data integrity for a tenant

**Parameters:**

- **tenant_id** (string) **(required)**: Tenant identifier to validate
- **fix_issues** (boolean) _(optional)_: Automatically fix detected issues

---

## Configuration

```json
{
  "--mdms-host": "https://mdms.digit.org",
  "--mdms-search-path": "/egov-mdms-service/v1/_search",
  "--mdms-create-path": "/egov-mdms-service/v1/_create",
  "--mdms-update-path": "/egov-mdms-service/v1/_update",
  "--cache-enabled": true
}
```