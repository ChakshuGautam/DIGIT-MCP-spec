# DIGIT Documentation MCP Tool Reference

## Table of Contents

- **[API Documentation](#api-documentation)** (4 tools)
  - [`generate_api_docs`](#generate_api_docs)
  - [`update_api_docs`](#update_api_docs)
  - [`generate_sdk_docs`](#generate_sdk_docs)
  - [`generate_changelog`](#generate_changelog)

- **[API Discovery & Analysis](#api-discovery--analysis)** (4 tools)
  - [`discover_endpoints`](#discover_endpoints)
  - [`analyze_api_usage`](#analyze_api_usage)
  - [`find_similar_apis`](#find_similar_apis)
  - [`map_api_dependencies`](#map_api_dependencies)

- **[Documentation Management](#documentation-management)** (5 tools)
  - [`create_api_collection`](#create_api_collection)
  - [`version_documentation`](#version_documentation)
  - [`publish_documentation`](#publish_documentation)
  - [`archive_documentation`](#archive_documentation)
  - [`sync_docs_with_code`](#sync_docs_with_code)

- **[Interactive Documentation](#interactive-documentation)** (4 tools)
  - [`create_api_playground`](#create_api_playground)
  - [`generate_code_examples`](#generate_code_examples)
  - [`create_api_tutorial`](#create_api_tutorial)
  - [`test_api_examples`](#test_api_examples)

- **[Documentation Quality](#documentation-quality)** (4 tools)
  - [`validate_api_docs`](#validate_api_docs)
  - [`check_docs_completeness`](#check_docs_completeness)
  - [`detect_breaking_changes`](#detect_breaking_changes)
  - [`find_deprecated_apis`](#find_deprecated_apis)

- **[Integration & Import/Export](#integration--importexport)** (4 tools)
  - [`import_postman_collection`](#import_postman_collection)
  - [`export_postman_collection`](#export_postman_collection)
  - [`import_openapi_spec`](#import_openapi_spec)
  - [`export_openapi_spec`](#export_openapi_spec)

- **[Collaboration & Feedback](#collaboration--feedback)** (3 tools)
  - [`create_doc_review`](#create_doc_review)
  - [`add_doc_comment`](#add_doc_comment)
  - [`track_doc_feedback`](#track_doc_feedback)

- **[Analytics & Recommendations](#analytics--recommendations)** (6 tools)
  - [`search_documentation`](#search_documentation)
  - [`get_api_recommendations`](#get_api_recommendations)
  - [`get_doc_metrics`](#get_doc_metrics)
  - [`analyze_doc_usage`](#analyze_doc_usage)
  - [`generate_doc_report`](#generate_doc_report)

## API Documentation

### `generate_api_docs`

**Description:** Auto-generate comprehensive API documentation from various sources

**Parameters:**

- **service_name** (string) **(required)**: Name of the service to document
- **source_type** (enum) **(required)**: Source type (openapi, swagger, code, postman)
- **source_path** (string) **(required)**: Path or URL to the source
- **output_format** (enum) **(required)**: Output format (html, markdown, pdf)
- **include_examples** (boolean) _(optional)_: Include request/response examples
- **languages** (array) _(optional)_: Programming languages for code examples

---

### `update_api_docs`

**Description:** Update existing API documentation with version control

**Parameters:**

- **doc_id** (string) **(required)**: Documentation identifier to update
- **updates** (object) **(required)**: Documentation updates and changes
- **auto_version** (boolean) _(optional)_: Automatically increment version number
- **notify_consumers** (boolean) _(optional)_: Notify API consumers of changes

---

### `generate_sdk_docs`

**Description:** Generate SDK documentation with language-specific examples

**Parameters:**

- **service_name** (string) **(required)**: Service to generate SDK docs for
- **sdk_language** (enum) **(required)**: SDK language (java, python, javascript, curl)
- **sdk_path** (string) **(required)**: Path to SDK source or configuration
- **include_tutorials** (boolean) _(optional)_: Include getting started tutorials

---

### `generate_changelog`

**Description:** Generate changelog documentation from version differences

**Parameters:**

- **service_name** (string) **(required)**: Service to generate changelog for
- **from_version** (string) **(required)**: Starting version for comparison
- **to_version** (string) **(required)**: Ending version for comparison
- **include_breaking** (boolean) _(optional)_: Highlight breaking changes
- **format** (enum) _(optional)_: Changelog format (markdown, html, json)

---

## API Discovery & Analysis

### `discover_endpoints`

**Description:** Discover and catalog API endpoints from various sources

**Parameters:**

- **service_name** (string) _(optional)_: Filter by specific service
- **scan_type** (enum) **(required)**: Discovery method (swagger, code, traffic, manual)
- **include_internal** (boolean) _(optional)_: Include internal/private endpoints
- **group_by** (enum) _(optional)_: Group endpoints by (service, module, version)

---

### `analyze_api_usage`

**Description:** Analyze API usage patterns and adoption metrics

**Parameters:**

- **service_name** (string) _(optional)_: Filter by specific service
- **time_period** (object) **(required)**: Time period for usage analysis
- **metrics** (array) _(optional)_: Specific metrics (calls, users, errors, latency)
- **consumer_breakdown** (boolean) _(optional)_: Include consumer-specific metrics

---

### `find_similar_apis`

**Description:** Find similar API endpoints for consistency and reuse

**Parameters:**

- **reference_endpoint** (string) **(required)**: Reference endpoint for comparison
- **similarity_threshold** (number) _(optional)_: Similarity score threshold (0-1)
- **search_scope** (array) _(optional)_: Services or modules to search within

---

### `map_api_dependencies`

**Description:** Map dependencies between APIs and services

**Parameters:**

- **service_name** (string) **(required)**: Service to map dependencies for
- **depth** (number) _(optional)_: Dependency mapping depth
- **include_external** (boolean) _(optional)_: Include external API dependencies

---

## Documentation Management

### `create_api_collection`

**Description:** Create organized collection of related APIs

**Parameters:**

- **collection_name** (string) **(required)**: Name for the API collection
- **description** (string) **(required)**: Collection description and purpose
- **apis** (array) **(required)**: List of APIs to include in collection
- **tags** (array) _(optional)_: Tags for categorization
- **visibility** (enum) _(optional)_: Collection visibility (public, private, internal)

---

### `version_documentation`

**Description:** Create versioned snapshot of documentation

**Parameters:**

- **doc_id** (string) **(required)**: Documentation to version
- **version** (string) **(required)**: Version identifier
- **change_notes** (string) **(required)**: Notes describing changes
- **mark_stable** (boolean) _(optional)_: Mark version as stable/production

---

### `publish_documentation`

**Description:** Publish documentation to various channels and formats

**Parameters:**

- **doc_id** (string) **(required)**: Documentation to publish
- **target** (enum) **(required)**: Publication target (portal, website, pdf, wiki)
- **visibility** (enum) **(required)**: Publication visibility level
- **notify_subscribers** (boolean) _(optional)_: Notify documentation subscribers

---

### `archive_documentation`

**Description:** Archive outdated documentation with proper redirection

**Parameters:**

- **doc_id** (string) **(required)**: Documentation to archive
- **reason** (string) **(required)**: Reason for archiving
- **redirect_to** (string) _(optional)_: URL to redirect archived content to

---

### `sync_docs_with_code`

**Description:** Synchronize documentation with source code changes

**Parameters:**

- **service_name** (string) **(required)**: Service to synchronize
- **branch** (string) _(optional)_: Git branch to sync from
- **auto_update** (boolean) _(optional)_: Automatically update documentation
- **create_pr** (boolean) _(optional)_: Create pull request for changes

---

## Interactive Documentation

### `create_api_playground`

**Description:** Create interactive API testing playground

**Parameters:**

- **api_endpoint** (string) **(required)**: API endpoint for playground
- **auth_config** (object) **(required)**: Authentication configuration
- **sample_data** (object) _(optional)_: Sample request data
- **sandbox_mode** (boolean) _(optional)_: Enable sandbox mode for safe testing

---

### `generate_code_examples`

**Description:** Generate code examples in multiple programming languages

**Parameters:**

- **api_endpoint** (string) **(required)**: API endpoint for examples
- **languages** (array) **(required)**: Programming languages to generate
- **auth_type** (string) **(required)**: Authentication method for examples
- **include_error_handling** (boolean) _(optional)_: Include error handling code
- **use_async** (boolean) _(optional)_: Generate async/await examples

---

### `create_api_tutorial`

**Description:** Create step-by-step API integration tutorial

**Parameters:**

- **tutorial_name** (string) **(required)**: Name for the tutorial
- **apis** (array) **(required)**: APIs covered in the tutorial
- **steps** (array) **(required)**: Tutorial steps and instructions
- **difficulty** (enum) **(required)**: Tutorial difficulty (beginner, intermediate, advanced)
- **estimated_time** (string) _(optional)_: Estimated completion time

---

### `test_api_examples`

**Description:** Test documentation examples for accuracy and functionality

**Parameters:**

- **doc_id** (string) **(required)**: Documentation to test examples for
- **environment** (string) **(required)**: Testing environment (dev, staging, prod)
- **fix_failures** (boolean) _(optional)_: Automatically fix failing examples
- **update_docs** (boolean) _(optional)_: Update documentation with fixes

---

## Documentation Quality

### `validate_api_docs`

**Description:** Validate documentation completeness and accuracy

**Parameters:**

- **doc_id** (string) **(required)**: Documentation to validate
- **validation_type** (enum) **(required)**: Validation type (completeness, accuracy, standards)
- **fix_issues** (boolean) _(optional)_: Automatically fix validation issues
- **strict_mode** (boolean) _(optional)_: Enable strict validation rules

---

### `check_docs_completeness`

**Description:** Check documentation coverage and identify gaps

**Parameters:**

- **service_name** (string) **(required)**: Service to check documentation for
- **coverage_threshold** (number) _(optional)_: Minimum coverage threshold percentage
- **required_sections** (array) _(optional)_: Required documentation sections

---

### `detect_breaking_changes`

**Description:** Detect breaking changes between API versions

**Parameters:**

- **old_spec** (string) **(required)**: Previous API specification
- **new_spec** (string) **(required)**: New API specification
- **severity_threshold** (enum) _(optional)_: Minimum severity to report

---

### `find_deprecated_apis`

**Description:** Find deprecated APIs and suggest alternatives

**Parameters:**

- **scan_scope** (array) _(optional)_: Services or modules to scan
- **include_alternatives** (boolean) _(optional)_: Suggest alternative APIs
- **grace_period** (string) _(optional)_: Deprecation grace period filter

---

## Integration & Import/Export

### `import_postman_collection`

**Description:** Import Postman collection and generate documentation

**Parameters:**

- **collection_file** (string) **(required)**: Path to Postman collection file
- **environment_file** (string) _(optional)_: Path to environment file
- **generate_docs** (boolean) _(optional)_: Auto-generate documentation from collection
- **merge_existing** (boolean) _(optional)_: Merge with existing documentation

---

### `export_postman_collection`

**Description:** Export API documentation as Postman collection

**Parameters:**

- **service_name** (string) **(required)**: Service to export collection for
- **include_examples** (boolean) _(optional)_: Include request/response examples
- **include_tests** (boolean) _(optional)_: Include Postman test scripts
- **environment_config** (object) _(optional)_: Environment variables configuration

---

### `import_openapi_spec`

**Description:** Import OpenAPI specification and create documentation

**Parameters:**

- **spec_url** (string) **(required)**: URL or path to OpenAPI specification
- **version** (enum) **(required)**: OpenAPI version (2.0, 3.0, 3.1)
- **validate** (boolean) _(optional)_: Validate spec before import
- **enhance** (boolean) _(optional)_: Enhance with additional documentation

---

### `export_openapi_spec`

**Description:** Export documentation as OpenAPI specification

**Parameters:**

- **service_name** (string) **(required)**: Service to export specification for
- **version** (enum) **(required)**: OpenAPI specification version
- **include_extensions** (boolean) _(optional)_: Include vendor extensions

---

## Collaboration & Feedback

### `create_doc_review`

**Description:** Create documentation review with assigned reviewers

**Parameters:**

- **doc_id** (string) **(required)**: Documentation to review
- **reviewers** (array) **(required)**: List of reviewer identifiers
- **review_type** (enum) **(required)**: Review type (technical, editorial, approval)
- **deadline** (timestamp) _(optional)_: Review deadline

---

### `add_doc_comment`

**Description:** Add comment or suggestion to documentation

**Parameters:**

- **doc_id** (string) **(required)**: Documentation to comment on
- **section** (string) **(required)**: Documentation section for comment
- **comment** (string) **(required)**: Comment content
- **suggestion** (string) _(optional)_: Suggested improvement or correction

---

### `track_doc_feedback`

**Description:** Track and analyze documentation feedback and ratings

**Parameters:**

- **doc_id** (string) _(optional)_: Filter by specific documentation
- **time_period** (object) **(required)**: Time period for feedback analysis
- **sentiment_analysis** (boolean) _(optional)_: Perform sentiment analysis on feedback

---

## Analytics & Recommendations

### `search_documentation`

**Description:** Search across all documentation with advanced filtering

**Parameters:**

- **query** (string) **(required)**: Search query text
- **filters** (object) _(optional)_: Search filters (service, version, tags)
- **search_type** (enum) _(optional)_: Search type (exact, fuzzy, semantic)
- **limit** (number) _(optional)_: Maximum number of results

---

### `get_api_recommendations`

**Description:** Get API recommendations based on use case and context

**Parameters:**

- **use_case** (string) **(required)**: Specific use case or requirement
- **preferred_language** (string) _(optional)_: Preferred programming language
- **complexity** (enum) _(optional)_: Preferred complexity level (simple, moderate, advanced)

---

### `get_doc_metrics`

**Description:** Get comprehensive documentation metrics and KPIs

**Parameters:**

- **doc_id** (string) _(optional)_: Filter by specific documentation
- **metrics** (array) **(required)**: Metrics to include (views, ratings, completion)
- **time_range** (object) **(required)**: Time range for metrics
- **group_by** (string) _(optional)_: Group metrics by dimension

---

### `analyze_doc_usage`

**Description:** Analyze documentation usage patterns and user behavior

**Parameters:**

- **time_period** (object) **(required)**: Time period for usage analysis
- **user_segments** (array) _(optional)_: User segments to analyze
- **popular_paths** (boolean) _(optional)_: Include popular navigation paths

---

### `generate_doc_report`

**Description:** Generate comprehensive documentation analytics report

**Parameters:**

- **report_type** (enum) **(required)**: Report type (usage, quality, coverage, feedback)
- **services** (array) _(optional)_: Services to include in report
- **format** (enum) **(required)**: Report format (pdf, html, excel)

---

## Configuration

```json
{
  "--doc-portal-url": "https://docs.digit.org",
  "--openapi-validator": "spectral",
  "--code-languages": ["curl", "javascript", "python", "java"],
  "--versioning-strategy": "semantic",
  "--auto-generate": true,
  "--sync-interval": "1h",
  "--search-engine": "elasticsearch"
}
```