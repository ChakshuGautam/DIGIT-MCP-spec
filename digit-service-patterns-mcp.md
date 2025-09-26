# DIGIT Service Patterns MCP Tool Reference

## Table of Contents

- **[Service Generation](#service-generation)** (4 tools)
  - [`generate_microservice`](#generate_microservice)
  - [`generate_api_gateway`](#generate_api_gateway)
  - [`generate_service_mesh`](#generate_service_mesh)
  - [`generate_bff_layer`](#generate_bff_layer)

- **[Pattern Implementation](#pattern-implementation)** (6 tools)
  - [`implement_cqrs`](#implement_cqrs)
  - [`implement_event_sourcing`](#implement_event_sourcing)
  - [`implement_saga_pattern`](#implement_saga_pattern)
  - [`implement_circuit_breaker`](#implement_circuit_breaker)
  - [`implement_retry_pattern`](#implement_retry_pattern)
  - [`implement_bulkhead`](#implement_bulkhead)

- **[Data Patterns](#data-patterns)** (5 tools)
  - [`implement_repository_pattern`](#implement_repository_pattern)
  - [`implement_unit_of_work`](#implement_unit_of_work)
  - [`implement_data_mapper`](#implement_data_mapper)
  - [`implement_cache_aside`](#implement_cache_aside)
  - [`implement_database_per_service`](#implement_database_per_service)

- **[Integration Patterns](#integration-patterns)** (4 tools)
  - [`implement_api_composition`](#implement_api_composition)
  - [`implement_async_messaging`](#implement_async_messaging)
  - [`implement_webhook_pattern`](#implement_webhook_pattern)
  - [`implement_polling_pattern`](#implement_polling_pattern)

- **[Security Patterns](#security-patterns)** (4 tools)
  - [`implement_oauth2_flow`](#implement_oauth2_flow)
  - [`implement_api_key_auth`](#implement_api_key_auth)
  - [`implement_rate_limiting`](#implement_rate_limiting)
  - [`implement_encryption_pattern`](#implement_encryption_pattern)

- **[Observability Patterns](#observability-patterns)** (3 tools)
  - [`implement_distributed_tracing`](#implement_distributed_tracing)
  - [`implement_health_checks`](#implement_health_checks)
  - [`implement_audit_logging`](#implement_audit_logging)

- **[Anti-Pattern Detection](#anti-pattern-detection)** (3 tools)
  - [`detect_anti_patterns`](#detect_anti_patterns)
  - [`analyze_coupling`](#analyze_coupling)
  - [`detect_god_objects`](#detect_god_objects)

- **[Migration Patterns](#migration-patterns)** (3 tools)
  - [`implement_strangler_fig`](#implement_strangler_fig)
  - [`implement_branch_by_abstraction`](#implement_branch_by_abstraction)
  - [`implement_parallel_run`](#implement_parallel_run)

## Service Generation

### `generate_microservice`

**Description:** Generate complete microservice with DIGIT standards and patterns

**Parameters:**
- **service_name** (string) **(required)**: Name of the microservice
- **service_type** (enum) **(required)**: Type of service (crud, workflow, integration, batch)
- **database** (enum) **(required)**: Database type (postgresql, mongodb, redis)
- **framework** (enum) **(required)**: Framework (spring-boot, node-express, python-fastapi)
- **patterns** (array) _(optional)_: Patterns to include (repository, cqrs, event-sourcing)
- **integrations** (array) _(optional)_: External service integrations

---

### `generate_api_gateway`

**Description:** Generate API gateway with routing, authentication, and rate limiting

**Parameters:**
- **gateway_name** (string) **(required)**: Name of the API gateway
- **backend_services** (array) **(required)**: Backend service configurations
- **auth_provider** (string) **(required)**: Authentication provider configuration
- **rate_limit_config** (object) _(optional)_: Rate limiting rules
- **cors_config** (object) _(optional)_: CORS configuration

---

### `generate_service_mesh`

**Description:** Generate service mesh configuration with Istio/Linkerd

**Parameters:**
- **mesh_type** (enum) **(required)**: Service mesh type (istio, linkerd, consul)
- **services** (array) **(required)**: Services to include in mesh
- **traffic_policies** (object) **(required)**: Traffic management policies
- **security_policies** (object) _(optional)_: Security and mTLS configuration

---

### `generate_bff_layer`

**Description:** Generate Backend-for-Frontend layer for client optimization

**Parameters:**
- **bff_name** (string) **(required)**: Name of the BFF service
- **client_type** (enum) **(required)**: Client type (web, mobile, desktop)
- **backend_services** (array) **(required)**: Backend services to aggregate
- **graphql_enabled** (boolean) _(optional)_: Enable GraphQL endpoint

---

## Pattern Implementation

### `implement_cqrs`

**Description:** Implement Command Query Responsibility Segregation pattern

**Parameters:**
- **service_name** (string) **(required)**: Service to implement CQRS in
- **command_model** (object) **(required)**: Command side model definition
- **query_model** (object) **(required)**: Query side model definition
- **event_store** (string) **(required)**: Event store configuration
- **projections** (array) _(optional)_: Read model projections

---

### `implement_event_sourcing`

**Description:** Implement event sourcing for audit and state management

**Parameters:**
- **aggregate_root** (string) **(required)**: Aggregate root entity
- **events** (array) **(required)**: Domain events definition
- **event_store** (string) **(required)**: Event store configuration
- **snapshots** (object) _(optional)_: Snapshot configuration

---

### `implement_saga_pattern`

**Description:** Implement saga for distributed transaction management

**Parameters:**
- **saga_name** (string) **(required)**: Name of the saga
- **participants** (array) **(required)**: Participating services
- **compensation_logic** (object) **(required)**: Compensation handlers
- **saga_type** (enum) **(required)**: Saga type (choreography, orchestration)

---

### `implement_circuit_breaker`

**Description:** Implement circuit breaker for fault tolerance

**Parameters:**
- **service_name** (string) **(required)**: Service to protect
- **threshold** (number) **(required)**: Failure threshold percentage
- **timeout** (number) **(required)**: Timeout in milliseconds
- **fallback** (object) **(required)**: Fallback configuration

---

### `implement_retry_pattern`

**Description:** Implement retry logic with exponential backoff

**Parameters:**
- **operation** (string) **(required)**: Operation to retry
- **max_retries** (number) **(required)**: Maximum retry attempts
- **backoff_strategy** (enum) **(required)**: Backoff strategy (linear, exponential, fibonacci)
- **jitter** (boolean) _(optional)_: Add jitter to prevent thundering herd

---

### `implement_bulkhead`

**Description:** Implement bulkhead pattern for resource isolation

**Parameters:**
- **resource_name** (string) **(required)**: Resource to isolate
- **pool_size** (number) **(required)**: Thread pool size
- **queue_size** (number) **(required)**: Queue size for pending requests
- **timeout** (number) _(optional)_: Request timeout

---

## Data Patterns

### `implement_repository_pattern`

**Description:** Implement repository pattern for data access abstraction

**Parameters:**
- **entity_name** (string) **(required)**: Entity for repository
- **database_type** (string) **(required)**: Underlying database type
- **operations** (array) **(required)**: Repository operations to generate
- **caching** (object) _(optional)_: Caching configuration

---

### `implement_unit_of_work`

**Description:** Implement unit of work for transaction management

**Parameters:**
- **repositories** (array) **(required)**: Repositories to include
- **transaction_boundary** (string) **(required)**: Transaction boundary definition
- **isolation_level** (enum) _(optional)_: Transaction isolation level

---

### `implement_data_mapper`

**Description:** Implement data mapper for object-relational mapping

**Parameters:**
- **domain_model** (object) **(required)**: Domain model definition
- **database_schema** (object) **(required)**: Database schema definition
- **mapping_rules** (array) **(required)**: Mapping rules and transformations

---

### `implement_cache_aside`

**Description:** Implement cache-aside pattern for performance optimization

**Parameters:**
- **cache_provider** (enum) **(required)**: Cache provider (redis, memcached, hazelcast)
- **cache_keys** (array) **(required)**: Cache key patterns
- **ttl_config** (object) **(required)**: Time-to-live configuration
- **invalidation_strategy** (string) _(optional)_: Cache invalidation strategy

---

### `implement_database_per_service`

**Description:** Implement database-per-service pattern for data isolation

**Parameters:**
- **service_name** (string) **(required)**: Service requiring database
- **database_type** (enum) **(required)**: Database type
- **schema_design** (object) **(required)**: Database schema
- **data_sync_strategy** (string) _(optional)_: Cross-service data sync approach

---

## Integration Patterns

### `implement_api_composition`

**Description:** Implement API composition for aggregating service responses

**Parameters:**
- **composer_name** (string) **(required)**: API composer service name
- **source_apis** (array) **(required)**: APIs to compose
- **aggregation_logic** (object) **(required)**: Response aggregation rules
- **error_handling** (string) _(optional)_: Partial failure handling strategy

---

### `implement_async_messaging`

**Description:** Implement asynchronous messaging between services

**Parameters:**
- **message_broker** (enum) **(required)**: Message broker (kafka, rabbitmq, sqs)
- **topics** (array) **(required)**: Topic/queue configurations
- **producer_config** (object) **(required)**: Producer configuration
- **consumer_config** (object) **(required)**: Consumer configuration

---

### `implement_webhook_pattern`

**Description:** Implement webhook pattern for event notifications

**Parameters:**
- **webhook_name** (string) **(required)**: Webhook identifier
- **events** (array) **(required)**: Events to trigger webhooks
- **retry_policy** (object) **(required)**: Webhook retry configuration
- **security** (object) _(optional)_: Webhook security (HMAC, OAuth)

---

### `implement_polling_pattern`

**Description:** Implement polling pattern for status checking

**Parameters:**
- **resource** (string) **(required)**: Resource to poll
- **interval** (number) **(required)**: Polling interval in milliseconds
- **max_attempts** (number) **(required)**: Maximum polling attempts
- **success_criteria** (object) **(required)**: Success condition definition

---

## Security Patterns

### `implement_oauth2_flow`

**Description:** Implement OAuth2 authentication flow

**Parameters:**
- **flow_type** (enum) **(required)**: OAuth2 flow type (authorization_code, client_credentials, implicit)
- **auth_server** (string) **(required)**: Authorization server configuration
- **scopes** (array) **(required)**: OAuth2 scopes
- **token_storage** (string) _(optional)_: Token storage strategy

---

### `implement_api_key_auth`

**Description:** Implement API key authentication

**Parameters:**
- **key_generation** (object) **(required)**: Key generation strategy
- **key_storage** (string) **(required)**: Key storage configuration
- **rate_limiting** (object) _(optional)_: Per-key rate limits
- **key_rotation** (object) _(optional)_: Key rotation policy

---

### `implement_rate_limiting`

**Description:** Implement rate limiting for API protection

**Parameters:**
- **algorithm** (enum) **(required)**: Rate limiting algorithm (token_bucket, sliding_window, fixed_window)
- **limits** (object) **(required)**: Rate limit configurations
- **storage** (string) **(required)**: Rate limit counter storage
- **bypass_rules** (array) _(optional)_: Rate limit bypass conditions

---

### `implement_encryption_pattern`

**Description:** Implement encryption for data protection

**Parameters:**
- **encryption_type** (enum) **(required)**: Encryption type (at_rest, in_transit, field_level)
- **algorithm** (string) **(required)**: Encryption algorithm
- **key_management** (object) **(required)**: Key management configuration
- **fields** (array) _(optional)_: Fields to encrypt (for field-level)

---

## Observability Patterns

### `implement_distributed_tracing`

**Description:** Implement distributed tracing across services

**Parameters:**
- **tracing_backend** (enum) **(required)**: Tracing backend (jaeger, zipkin, datadog)
- **sampling_rate** (number) **(required)**: Trace sampling rate (0-1)
- **propagation_format** (string) **(required)**: Trace propagation format
- **custom_spans** (array) _(optional)_: Custom span definitions

---

### `implement_health_checks`

**Description:** Implement health check endpoints and monitoring

**Parameters:**
- **check_types** (array) **(required)**: Health check types (liveness, readiness, startup)
- **dependencies** (array) **(required)**: External dependencies to check
- **thresholds** (object) **(required)**: Health check thresholds
- **custom_checks** (array) _(optional)_: Custom health check logic

---

### `implement_audit_logging`

**Description:** Implement comprehensive audit logging

**Parameters:**
- **events_to_audit** (array) **(required)**: Events requiring audit
- **log_destination** (string) **(required)**: Audit log destination
- **retention_policy** (object) **(required)**: Log retention configuration
- **pii_handling** (object) _(optional)_: PII data handling rules

---

## Anti-Pattern Detection

### `detect_anti_patterns`

**Description:** Detect common anti-patterns in service architecture

**Parameters:**
- **scan_scope** (array) **(required)**: Services/components to scan
- **pattern_types** (array) _(optional)_: Specific anti-patterns to detect
- **severity_threshold** (enum) _(optional)_: Minimum severity to report

---

### `analyze_coupling`

**Description:** Analyze service coupling and dependencies

**Parameters:**
- **services** (array) **(required)**: Services to analyze
- **coupling_metrics** (array) **(required)**: Metrics to calculate
- **threshold** (object) _(optional)_: Coupling thresholds

---

### `detect_god_objects`

**Description:** Detect god objects and oversized components

**Parameters:**
- **scan_path** (string) **(required)**: Path to scan for god objects
- **metrics** (object) **(required)**: Size and complexity metrics
- **refactoring_suggestions** (boolean) _(optional)_: Generate refactoring suggestions

---

## Migration Patterns

### `implement_strangler_fig`

**Description:** Implement strangler fig pattern for gradual migration

**Parameters:**
- **legacy_service** (string) **(required)**: Legacy service to replace
- **new_service** (string) **(required)**: New service implementation
- **routing_rules** (array) **(required)**: Traffic routing configuration
- **migration_phases** (array) **(required)**: Migration phase definitions

---

### `implement_branch_by_abstraction`

**Description:** Implement branch by abstraction for safe refactoring

**Parameters:**
- **abstraction_layer** (string) **(required)**: Abstraction layer name
- **old_implementation** (string) **(required)**: Existing implementation
- **new_implementation** (string) **(required)**: New implementation
- **toggle_config** (object) **(required)**: Feature toggle configuration

---

### `implement_parallel_run`

**Description:** Implement parallel run pattern for verification

**Parameters:**
- **primary_service** (string) **(required)**: Primary service (source of truth)
- **shadow_service** (string) **(required)**: Shadow service to verify
- **comparison_rules** (object) **(required)**: Response comparison configuration
- **discrepancy_handling** (string) **(required)**: Discrepancy resolution strategy

---

## Configuration

```json
{
  "--language": "java",
  "--framework": "spring-boot",
  "--build-tool": "maven",
  "--test-framework": "junit",
  "--container-registry": "docker.io/digit",
  "--kubernetes-namespace": "digit",
  "--monitoring-backend": "prometheus",
  "--tracing-backend": "jaeger",
  "--message-broker": "kafka"
}
```