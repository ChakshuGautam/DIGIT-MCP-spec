# DIGIT UI Components MCP Tool Reference

## Table of Contents

- **[Component Management](#component-management)** (4 tools)
  - [`create_component`](#create_component)
  - [`update_component`](#update_component)
  - [`generate_component_from_design`](#generate_component_from_design)
  - [`compose_component`](#compose_component)

- **[Design System & Theming](#design-system--theming)** (4 tools)
  - [`create_design_token`](#create_design_token)
  - [`generate_theme`](#generate_theme)
  - [`apply_design_system`](#apply_design_system)
  - [`validate_design_consistency`](#validate_design_consistency)

- **[Forms & Data Components](#forms--data-components)** (6 tools)
  - [`generate_form`](#generate_form)
  - [`create_form_field`](#create_form_field)
  - [`validate_form`](#validate_form)
  - [`create_data_table`](#create_data_table)
  - [`create_chart_component`](#create_chart_component)
  - [`create_dashboard_widget`](#create_dashboard_widget)

- **[Layout & Navigation](#layout--navigation)** (3 tools)
  - [`create_grid_layout`](#create_grid_layout)
  - [`create_navigation_menu`](#create_navigation_menu)
  - [`create_router_config`](#create_router_config)

- **[Accessibility](#accessibility)** (3 tools)
  - [`audit_accessibility`](#audit_accessibility)
  - [`add_aria_attributes`](#add_aria_attributes)
  - [`generate_keyboard_navigation`](#generate_keyboard_navigation)

- **[Testing & Quality](#testing--quality)** (3 tools)
  - [`create_component_test`](#create_component_test)
  - [`run_visual_regression`](#run_visual_regression)
  - [`performance_test_component`](#performance_test_component)

- **[Documentation & Storybook](#documentation--storybook)** (4 tools)
  - [`generate_storybook`](#generate_storybook)
  - [`create_component_docs`](#create_component_docs)
  - [`generate_api_reference`](#generate_api_reference)
  - [`create_style_guide`](#create_style_guide)

- **[Micro-Frontend Architecture](#micro-frontend-architecture)** (2 tools)
  - [`create_micro_frontend`](#create_micro_frontend)
  - [`configure_module_federation`](#configure_module_federation)

- **[Styling & Optimization](#styling--optimization)** (2 tools)
  - [`optimize_styles`](#optimize_styles)
  - [`migrate_styles`](#migrate_styles)

## Component Management

### `create_component`

**Description:** Create new UI component with framework-specific templates and styling

**Parameters:**

- **component_name** (string) **(required)**: Unique name for the component
- **component_type** (enum) **(required)**: Type of component (basic, composite, layout, form)
- **framework** (enum) **(required)**: Target framework (react, vue, angular)
- **props** (array) **(required)**: Component properties and their types
- **template** (string) _(optional)_: Base template to use for component generation
- **styles** (object) _(optional)_: Styling configuration and CSS properties
- **variants** (array) _(optional)_: Component variants and their configurations

---

### `update_component`

**Description:** Update existing component with version control and compatibility checks

**Parameters:**

- **component_id** (string) **(required)**: Component identifier to update
- **updates** (object) **(required)**: Component updates and modifications
- **version_bump** (enum) _(optional)_: Version increment type (major, minor, patch)
- **backward_compatible** (boolean) _(optional)_: Ensure backward compatibility

---

### `generate_component_from_design`

**Description:** Generate component code from design files with responsive and accessibility features

**Parameters:**

- **design_file** (string) **(required)**: Path or URL to design file (Figma, Sketch)
- **component_name** (string) **(required)**: Name for the generated component
- **framework** (string) **(required)**: Target development framework
- **responsive** (boolean) _(optional)_: Generate responsive design breakpoints
- **accessibility** (boolean) _(optional)_: Include accessibility attributes and features

---

### `compose_component`

**Description:** Compose complex component from multiple smaller components

**Parameters:**

- **component_name** (string) **(required)**: Name for the composed component
- **composition** (array) **(required)**: List of child components and their configuration
- **layout** (object) **(required)**: Layout structure and positioning rules
- **interactions** (array) _(optional)_: Component interactions and event handlers

---

## Design System & Theming

### `create_design_token`

**Description:** Create design token for consistent styling across components

**Parameters:**

- **token_name** (string) **(required)**: Unique name for the design token
- **token_type** (enum) **(required)**: Token type (color, spacing, typography, shadow)
- **value** (any) **(required)**: Token value (CSS value, number, string)
- **category** (string) **(required)**: Token category for organization
- **description** (string) _(optional)_: Description of token usage and purpose

---

### `generate_theme`

**Description:** Generate complete theme with design tokens and color schemes

**Parameters:**

- **theme_name** (string) **(required)**: Name for the generated theme
- **base_tokens** (object) **(required)**: Base design tokens for the theme
- **mode** (enum) **(required)**: Theme mode (light, dark, auto)
- **brand_colors** (object) _(optional)_: Brand-specific color palette
- **custom_tokens** (object) _(optional)_: Additional custom design tokens

---

### `apply_design_system`

**Description:** Apply design system tokens and styles to existing components

**Parameters:**

- **design_system_id** (string) **(required)**: Design system identifier to apply
- **target_components** (array) **(required)**: Components to apply design system to
- **migration_strategy** (enum) _(optional)_: Migration approach (gradual, immediate)
- **preserve_overrides** (boolean) _(optional)_: Keep existing custom styles

---

### `validate_design_consistency`

**Description:** Validate design consistency across components and flag violations

**Parameters:**

- **scope** (array) _(optional)_: Components or modules to validate
- **rules** (array) _(optional)_: Custom validation rules to apply
- **fix_violations** (boolean) _(optional)_: Automatically fix detected violations
- **report_format** (enum) _(optional)_: Output format for validation report

---

## Forms & Data Components

### `generate_form`

**Description:** Generate complete form with validation, layout, and submission handling

**Parameters:**

- **form_name** (string) **(required)**: Name for the generated form
- **schema** (object) **(required)**: Form schema with field definitions
- **layout** (enum) **(required)**: Form layout type (vertical, horizontal, grid)
- **validation_rules** (array) **(required)**: Field validation rules and constraints
- **submit_action** (object) **(required)**: Form submission configuration
- **features** (array) _(optional)_: Additional form features (auto-save, progress)

---

### `create_form_field`

**Description:** Create custom form field component with validation and formatting

**Parameters:**

- **field_type** (string) **(required)**: Type of form field to create
- **base_type** (enum) **(required)**: Base input type (text, number, select, date)
- **validation** (array) _(optional)_: Field validation rules
- **formatting** (object) _(optional)_: Input formatting and masking options
- **accessibility** (object) _(optional)_: Accessibility attributes and labels

---

### `validate_form`

**Description:** Validate form component functionality and user experience

**Parameters:**

- **form_id** (string) **(required)**: Form component to validate
- **test_data** (object) _(optional)_: Test data for form validation
- **check_accessibility** (boolean) _(optional)_: Include accessibility validation
- **check_performance** (boolean) _(optional)_: Include performance testing

---

### `create_data_table`

**Description:** Create data table component with sorting, filtering, and pagination

**Parameters:**

- **table_name** (string) **(required)**: Name for the data table component
- **columns** (array) **(required)**: Column definitions and configurations
- **features** (array) _(optional)_: Table features (sort, filter, pagination, export)
- **data_source** (object) _(optional)_: Data source configuration and API endpoints

---

### `create_chart_component`

**Description:** Create interactive chart component for data visualization

**Parameters:**

- **chart_name** (string) **(required)**: Name for the chart component
- **chart_type** (enum) **(required)**: Chart type (bar, line, pie, scatter, area)
- **data_structure** (object) **(required)**: Expected data structure and format
- **options** (object) **(required)**: Chart configuration and styling options
- **interactive** (boolean) _(optional)_: Enable interactive features (zoom, hover)
- **responsive** (boolean) _(optional)_: Make chart responsive to container size

---

### `create_dashboard_widget`

**Description:** Create dashboard widget with real-time data binding

**Parameters:**

- **widget_name** (string) **(required)**: Name for the dashboard widget
- **widget_type** (string) **(required)**: Widget type (metric, chart, table, alert)
- **data_binding** (object) **(required)**: Data source and binding configuration
- **refresh_interval** (number) _(optional)_: Auto-refresh interval in seconds
- **actions** (array) _(optional)_: Widget actions and interactions

---

## Layout & Navigation

### `create_grid_layout`

**Description:** Create responsive grid layout system for component positioning

**Parameters:**

- **layout_name** (string) **(required)**: Name for the grid layout
- **grid_type** (enum) **(required)**: Grid type (css-grid, flexbox, bootstrap)
- **breakpoints** (object) **(required)**: Responsive breakpoint definitions
- **gap** (object) **(required)**: Grid gap and spacing configuration
- **areas** (array) _(optional)_: Named grid areas for complex layouts

---

### `create_navigation_menu`

**Description:** Create navigation menu component with accessibility and responsive behavior

**Parameters:**

- **menu_name** (string) **(required)**: Name for the navigation menu
- **menu_type** (enum) **(required)**: Menu type (horizontal, vertical, sidebar, dropdown)
- **items** (array) **(required)**: Navigation items and their configurations
- **collapse_behavior** (object) _(optional)_: Mobile collapse and hamburger menu settings
- **accessibility** (object) _(optional)_: ARIA labels and keyboard navigation

---

### `create_router_config`

**Description:** Create routing configuration for single-page application navigation

**Parameters:**

- **app_name** (string) **(required)**: Application name for routing context
- **routes** (array) **(required)**: Route definitions with paths and components
- **layout_strategy** (enum) **(required)**: Layout strategy (nested, flat, modular)
- **auth_guards** (array) _(optional)_: Authentication guards for protected routes
- **lazy_loading** (boolean) _(optional)_: Enable code splitting for route components

---

## Accessibility

### `audit_accessibility`

**Description:** Perform comprehensive accessibility audit on UI components

**Parameters:**

- **component_id** (string) **(required)**: Component to audit for accessibility
- **wcag_level** (enum) **(required)**: WCAG compliance level (A, AA, AAA)
- **test_scenarios** (array) _(optional)_: Specific accessibility test scenarios
- **fix_issues** (boolean) _(optional)_: Automatically fix detected accessibility issues

---

### `add_aria_attributes`

**Description:** Add ARIA attributes and labels to improve component accessibility

**Parameters:**

- **component_id** (string) **(required)**: Component to enhance with ARIA attributes
- **aria_config** (object) **(required)**: ARIA attribute configuration
- **validate** (boolean) _(optional)_: Validate ARIA implementation after addition

---

### `generate_keyboard_navigation`

**Description:** Generate keyboard navigation support for interactive components

**Parameters:**

- **component_id** (string) **(required)**: Component to add keyboard navigation to
- **navigation_pattern** (enum) **(required)**: Navigation pattern (tab, arrow, custom)
- **shortcuts** (array) _(optional)_: Custom keyboard shortcuts and their actions

---

## Testing & Quality

### `create_component_test`

**Description:** Generate comprehensive test suite for UI component

**Parameters:**

- **component_id** (string) **(required)**: Component to create tests for
- **test_type** (enum) **(required)**: Test type (unit, integration, e2e)
- **test_framework** (enum) **(required)**: Testing framework (jest, cypress, playwright)
- **coverage_threshold** (number) _(optional)_: Minimum code coverage percentage

---

### `run_visual_regression`

**Description:** Execute visual regression testing to detect UI changes

**Parameters:**

- **components** (array) **(required)**: Components to test for visual regressions
- **viewports** (array) **(required)**: Screen sizes and viewports to test
- **threshold** (number) _(optional)_: Pixel difference threshold for failures
- **update_baseline** (boolean) _(optional)_: Update baseline images after test

---

### `performance_test_component`

**Description:** Test component performance and identify optimization opportunities

**Parameters:**

- **component_id** (string) **(required)**: Component to performance test
- **metrics** (array) **(required)**: Performance metrics to measure
- **scenarios** (array) **(required)**: Test scenarios with different data loads
- **threshold** (object) _(optional)_: Performance threshold limits

---

## Documentation & Storybook

### `generate_storybook`

**Description:** Generate Storybook stories for component documentation and testing

**Parameters:**

- **component_id** (string) **(required)**: Component to create Storybook stories for
- **story_types** (array) **(required)**: Types of stories to generate
- **controls** (object) _(optional)_: Interactive controls configuration
- **docs** (boolean) _(optional)_: Generate automatic documentation

---

### `create_component_docs`

**Description:** Generate comprehensive documentation for UI component

**Parameters:**

- **component_id** (string) **(required)**: Component to document
- **doc_sections** (array) **(required)**: Documentation sections to include
- **format** (enum) **(required)**: Documentation format (markdown, html, json)
- **examples** (array) _(optional)_: Code examples and usage scenarios

---

### `generate_api_reference`

**Description:** Generate API reference documentation for component props and methods

**Parameters:**

- **component_id** (string) **(required)**: Component to generate API reference for
- **include_private** (boolean) _(optional)_: Include private methods and props
- **format** (enum) **(required)**: Output format for API reference

---

### `create_style_guide`

**Description:** Create visual style guide showcasing components and design patterns

**Parameters:**

- **guide_name** (string) **(required)**: Name for the style guide
- **components** (array) **(required)**: Components to include in style guide
- **sections** (array) **(required)**: Style guide sections and organization
- **format** (enum) **(required)**: Output format for style guide

---

## Micro-Frontend Architecture

### `create_micro_frontend`

**Description:** Create micro-frontend module with module federation configuration

**Parameters:**

- **module_name** (string) **(required)**: Name for the micro-frontend module
- **framework** (string) **(required)**: Framework for micro-frontend development
- **expose** (array) **(required)**: Components and modules to expose
- **remotes** (array) _(optional)_: Remote micro-frontend dependencies
- **shared** (object) _(optional)_: Shared dependencies configuration

---

### `configure_module_federation`

**Description:** Configure module federation for micro-frontend architecture

**Parameters:**

- **app_name** (string) **(required)**: Application name for module federation
- **modules** (array) **(required)**: Micro-frontend modules configuration
- **shared_dependencies** (object) **(required)**: Shared dependency configuration
- **routing_strategy** (enum) **(required)**: Routing strategy between modules

---

## Styling & Optimization

### `optimize_styles`

**Description:** Optimize component styles for performance and bundle size

**Parameters:**

- **component_id** (string) _(optional)_: Specific component to optimize
- **optimization_type** (array) **(required)**: Optimization types to apply
- **minify** (boolean) _(optional)_: Minify CSS output
- **generate_critical** (boolean) _(optional)_: Extract critical CSS for performance

---

### `migrate_styles`

**Description:** Migrate component styles between different CSS frameworks

**Parameters:**

- **from_system** (enum) **(required)**: Source styling system to migrate from
- **to_system** (enum) **(required)**: Target styling system to migrate to
- **components** (array) **(required)**: Components to migrate styles for
- **preserve_custom** (boolean) _(optional)_: Preserve custom style overrides

---

## Configuration

```json
{
  "--component-library": "@digit-ui/components",
  "--design-system": "@digit-ui/tokens",
  "--framework": "react",
  "--storybook-url": "http://localhost:6006",
  "--figma-token": "figma-api-token",
  "--css-framework": "tailwind",
  "--bundler": "webpack",
  "--test-runner": "jest"
}
```