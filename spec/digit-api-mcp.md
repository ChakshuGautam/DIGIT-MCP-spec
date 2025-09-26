# DIGIT API MCP Tool Reference

## Table of Contents

- **[Entity Operations](#entity-operations)** (5 tools)
  - [`create_entity`](#create_entity)
  - [`read_entity`](#read_entity)
  - [`update_entity`](#update_entity)
  - [`delete_entity`](#delete_entity)
  - [`search_entities`](#search_entities)

- **[Bulk Operations](#bulk-operations)** (3 tools)
  - [`bulk_create`](#bulk_create)
  - [`bulk_update`](#bulk_update)
  - [`bulk_delete`](#bulk_delete)

- **[Workflow Operations](#workflow-operations)** (4 tools)
  - [`execute_workflow`](#execute_workflow)
  - [`get_workflow_status`](#get_workflow_status)
  - [`cancel_workflow`](#cancel_workflow)
  - [`retry_workflow`](#retry_workflow)

- **[Transaction Management](#transaction-management)** (3 tools)
  - [`begin_transaction`](#begin_transaction)
  - [`commit_transaction`](#commit_transaction)
  - [`rollback_transaction`](#rollback_transaction)

- **[Service Discovery](#service-discovery)** (2 tools)
  - [`discover_service`](#discover_service)
  - [`get_service_metadata`](#get_service_metadata)

- **[Validation & Schema](#validation--schema)** (3 tools)
  - [`validate_entity`](#validate_entity)
  - [`get_entity_schema`](#get_entity_schema)
  - [`validate_request`](#validate_request)

- **[Audit & History](#audit--history)** (2 tools)
  - [`get_entity_history`](#get_entity_history)
  - [`get_audit_log`](#get_audit_log)

- **[Notifications](#notifications)** (2 tools)
  - [`send_notification`](#send_notification)
  - [`get_notification_status`](#get_notification_status)

## Entity Operations

### `create_entity`

**Description:** Create new entity with automatic service routing and validation

**Parameters:**
- **entity_type** (string) **(required)**: Type of entity (user, property, trade_license, etc.)
- **tenant_id** (string) **(required)**: Tenant identifier
- **entity_data** (object) **(required)**: Entity-specific data payload
- **request_info** (object) **(required)**: Standard DIGIT RequestInfo
- **idgen_name** (string) _(optional)_: ID generation format name
- **persist_formdata** (boolean) _(optional)_: Persist form data for workflows

---

### `read_entity`

**Description:** Retrieve entity by ID with related data expansion

**Parameters:**
- **entity_type** (string) **(required)**: Type of entity to retrieve
- **entity_id** (string) **(required)**: Unique identifier of the entity
- **tenant_id** (string) **(required)**: Tenant identifier
- **expand** (array) _(optional)_: Related entities to include
- **fields** (array) _(optional)_: Specific fields to return

---

### `update_entity`

**Description:** Update existing entity with optimistic locking

**Parameters:**
- **entity_type** (string) **(required)**: Type of entity to update
- **entity_id** (string) **(required)**: Entity identifier
- **tenant_id** (string) **(required)**: Tenant identifier
- **entity_data** (object) **(required)**: Updated entity data
- **request_info** (object) **(required)**: Standard DIGIT RequestInfo
- **version** (number) _(optional)_: Version for optimistic locking

---

### `delete_entity`

**Description:** Delete or soft-delete entity based on service configuration

**Parameters:**
- **entity_type** (string) **(required)**: Type of entity to delete
- **entity_id** (string) **(required)**: Entity identifier
- **tenant_id** (string) **(required)**: Tenant identifier
- **request_info** (object) **(required)**: Standard DIGIT RequestInfo
- **reason** (string) _(optional)_: Reason for deletion
- **hard_delete** (boolean) _(optional)_: Force permanent deletion

---

### `search_entities`

**Description:** Search entities with filtering, pagination, and sorting

**Parameters:**
- **entity_type** (string) **(required)**: Type of entity to search
- **tenant_id** (string) **(required)**: Tenant identifier
- **search_criteria** (object) **(required)**: Search filters and conditions
- **pagination** (object) _(optional)_: Limit and offset parameters
- **sort** (array) _(optional)_: Sort fields and order
- **request_info** (object) **(required)**: Standard DIGIT RequestInfo

---

## Bulk Operations

### `bulk_create`

**Description:** Create multiple entities in a single transaction

**Parameters:**
- **entity_type** (string) **(required)**: Type of entities to create
- **tenant_id** (string) **(required)**: Tenant identifier
- **entities** (array) **(required)**: Array of entity data objects
- **request_info** (object) **(required)**: Standard DIGIT RequestInfo
- **batch_size** (number) _(optional)_: Batch processing size
- **continue_on_error** (boolean) _(optional)_: Continue processing on individual failures

---

### `bulk_update`

**Description:** Update multiple entities in batch with validation

**Parameters:**
- **entity_type** (string) **(required)**: Type of entities to update
- **tenant_id** (string) **(required)**: Tenant identifier
- **entities** (array) **(required)**: Array of entity updates with IDs
- **request_info** (object) **(required)**: Standard DIGIT RequestInfo
- **validate_all** (boolean) _(optional)_: Validate all before updating any

---

### `bulk_delete`

**Description:** Delete multiple entities by ID or criteria

**Parameters:**
- **entity_type** (string) **(required)**: Type of entities to delete
- **tenant_id** (string) **(required)**: Tenant identifier
- **entity_ids** (array) _(optional)_: List of entity IDs to delete
- **delete_criteria** (object) _(optional)_: Criteria-based deletion
- **request_info** (object) **(required)**: Standard DIGIT RequestInfo

---

## Workflow Operations

### `execute_workflow`

**Description:** Execute workflow action on entity with state transition

**Parameters:**
- **entity_type** (string) **(required)**: Entity type with workflow
- **entity_id** (string) **(required)**: Entity to execute workflow on
- **action** (string) **(required)**: Workflow action to perform
- **tenant_id** (string) **(required)**: Tenant identifier
- **request_info** (object) **(required)**: Standard DIGIT RequestInfo
- **comment** (string) _(optional)_: Action comment or reason
- **documents** (array) _(optional)_: Supporting documents
- **assignee** (string) _(optional)_: Assign to specific user/role

---

### `get_workflow_status`

**Description:** Get current workflow state and available actions

**Parameters:**
- **entity_type** (string) **(required)**: Entity type with workflow
- **entity_id** (string) **(required)**: Entity identifier
- **tenant_id** (string) **(required)**: Tenant identifier
- **include_history** (boolean) _(optional)_: Include workflow history

---

### `cancel_workflow`

**Description:** Cancel active workflow instance

**Parameters:**
- **workflow_id** (string) **(required)**: Workflow instance ID
- **reason** (string) **(required)**: Cancellation reason
- **request_info** (object) **(required)**: Standard DIGIT RequestInfo

---

### `retry_workflow`

**Description:** Retry failed workflow action

**Parameters:**
- **workflow_id** (string) **(required)**: Workflow instance ID
- **action_id** (string) **(required)**: Failed action to retry
- **request_info** (object) **(required)**: Standard DIGIT RequestInfo

---

## Transaction Management

### `begin_transaction`

**Description:** Start distributed transaction across services

**Parameters:**
- **transaction_id** (string) _(optional)_: Custom transaction ID
- **services** (array) **(required)**: Services participating in transaction
- **timeout** (number) _(optional)_: Transaction timeout in seconds
- **isolation_level** (string) _(optional)_: Transaction isolation level

---

### `commit_transaction`

**Description:** Commit distributed transaction

**Parameters:**
- **transaction_id** (string) **(required)**: Transaction to commit
- **request_info** (object) **(required)**: Standard DIGIT RequestInfo

---

### `rollback_transaction`

**Description:** Rollback distributed transaction

**Parameters:**
- **transaction_id** (string) **(required)**: Transaction to rollback
- **reason** (string) _(optional)_: Rollback reason
- **request_info** (object) **(required)**: Standard DIGIT RequestInfo

---

## Service Discovery

### `discover_service`

**Description:** Discover service endpoint for entity type

**Parameters:**
- **entity_type** (string) **(required)**: Entity type to find service for
- **operation** (string) **(required)**: Operation type (create, read, update, delete, search)
- **version** (string) _(optional)_: API version preference

---

### `get_service_metadata`

**Description:** Get service capabilities and metadata

**Parameters:**
- **service_name** (string) **(required)**: Service to get metadata for
- **include_endpoints** (boolean) _(optional)_: Include endpoint details
- **include_schema** (boolean) _(optional)_: Include entity schemas

---

## Validation & Schema

### `validate_entity`

**Description:** Validate entity data against service schema

**Parameters:**
- **entity_type** (string) **(required)**: Entity type to validate
- **entity_data** (object) **(required)**: Entity data to validate
- **validation_level** (string) _(optional)_: Validation strictness level
- **custom_rules** (array) _(optional)_: Additional validation rules

---

### `get_entity_schema`

**Description:** Get JSON schema for entity type

**Parameters:**
- **entity_type** (string) **(required)**: Entity type to get schema for
- **version** (string) _(optional)_: Schema version
- **include_examples** (boolean) _(optional)_: Include example data

---

### `validate_request`

**Description:** Validate API request format and data

**Parameters:**
- **service_name** (string) **(required)**: Target service name
- **endpoint** (string) **(required)**: API endpoint path
- **request_data** (object) **(required)**: Request payload to validate

---

## Audit & History

### `get_entity_history`

**Description:** Get complete audit history for entity

**Parameters:**
- **entity_type** (string) **(required)**: Type of entity
- **entity_id** (string) **(required)**: Entity identifier
- **tenant_id** (string) **(required)**: Tenant identifier
- **from_date** (timestamp) _(optional)_: History start date
- **to_date** (timestamp) _(optional)_: History end date
- **include_changes** (boolean) _(optional)_: Include field-level changes

---

### `get_audit_log`

**Description:** Retrieve audit logs for operations

**Parameters:**
- **entity_type** (string) _(optional)_: Filter by entity type
- **user_id** (string) _(optional)_: Filter by user
- **action** (string) _(optional)_: Filter by action type
- **from_date** (timestamp) **(required)**: Start date for logs
- **to_date** (timestamp) **(required)**: End date for logs
- **tenant_id** (string) **(required)**: Tenant identifier

---

## Notifications

### `send_notification`

**Description:** Send notification through configured channels

**Parameters:**
- **entity_type** (string) **(required)**: Related entity type
- **entity_id** (string) **(required)**: Related entity ID
- **event_type** (string) **(required)**: Notification event type
- **recipient** (object) **(required)**: Recipient details
- **channel** (array) _(optional)_: Notification channels (sms, email, app)
- **template_id** (string) _(optional)_: Message template ID

---

### `get_notification_status`

**Description:** Check notification delivery status

**Parameters:**
- **notification_id** (string) **(required)**: Notification ID to check
- **include_details** (boolean) _(optional)_: Include delivery details

---

## Configuration

```json
{
  "--base-url": "https://api.digit.org",
  "--auth-token": "bearer-token",
  "--tenant-id": "dj",
  "--request-info": {
    "apiId": "Rainmaker",
    "ver": ".01",
    "ts": "",
    "action": "",
    "did": "1",
    "key": "",
    "msgId": "20170310130900|en_IN"
  },
  "--timeout": 30000,
  "--retry-count": 3,
  "--batch-size": 100
}
```