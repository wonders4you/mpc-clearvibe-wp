# Elementor Abilities (50)

The For-Elementor add-on adds 50 abilities across 6 categories. All abilities are prefixed with `mpc-clearvibe-wp/elem-`. Categories are **enabled by default**.

## Categories

| Category | Count | Description |
|----------|-------|-------------|
| `elementor` | 15 | Version, settings, templates CRUD, import/export |
| `elementor-kit` | 8 | Kit settings, global colors, typography |
| `elementor-popups` | 10 | Popups CRUD, triggers, display settings |
| `elementor-widgets` | 4 | Widget types, controls, defaults |
| `elementor-css` | 3 | CSS cache regenerate, clear, info |
| `elementor-maintenance` | 10 | System info, replace URLs, maintenance mode, roles |

## elementor (15 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `elem-get-version` | Get Elementor and Elementor Pro version | Read |
| `elem-get-settings` | Get Elementor general settings | Read |
| `elem-update-settings` | Update Elementor general settings | Write |
| `elem-list-templates` | List Elementor library templates | Read |
| `elem-get-template` | Get a single template by ID | Read |
| `elem-create-template` | Create a new Elementor template | Write |
| `elem-update-template` | Update an Elementor template | Write |
| `elem-delete-template` | Delete an Elementor template | Write |
| `elem-get-template-data` | Get the Elementor data JSON for a post/template | Read |
| `elem-update-template-data` | Update the Elementor data JSON | Write |
| `elem-export-template` | Export a template as JSON | Read |
| `elem-import-template` | Import a template from JSON | Write |
| `elem-duplicate-template` | Duplicate an Elementor template | Write |
| `elem-get-template-type` | Get the document type for a template | Read |
| `elem-list-template-types` | List all available document types | Read |

## elementor-kit (8 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `elem-get-current-kit` | Get the active kit ID | Read |
| `elem-get-kit-settings` | Get kit settings (custom colors, fonts) | Read |
| `elem-update-kit-settings` | Update kit settings | Write |
| `elem-get-global-colors` | Get global color palette from the kit | Read |
| `elem-update-global-colors` | Update global color palette | Write |
| `elem-get-global-typography` | Get global typography settings | Read |
| `elem-update-global-typography` | Update global typography | Write |
| `elem-get-kit-meta` | Get all kit meta keys | Read |

## elementor-popups (10 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `elem-list-popups` | List all Elementor popups | Read |
| `elem-get-popup` | Get a single popup by ID | Read |
| `elem-create-popup` | Create a new Elementor popup | Write |
| `elem-update-popup` | Update an Elementor popup | Write |
| `elem-delete-popup` | Delete an Elementor popup | Write |
| `elem-get-popup-triggers` | Get triggers for a popup | Read |
| `elem-update-popup-triggers` | Update triggers for a popup | Write |
| `elem-get-popup-display-settings` | Get display conditions for a popup | Read |
| `elem-update-popup-display-settings` | Update display conditions for a popup | Write |
| `elem-get-popup-settings` | Get all popup settings (triggers + display + timing) | Read |

## elementor-widgets (4 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `elem-list-widgets` | List all registered Elementor widget types | Read |
| `elem-get-widget-controls` | Get controls for a widget type | Read |
| `elem-get-widget-defaults` | Get default settings for a widget type | Read |
| `elem-list-elements` | List all elements in a post | Read |

## elementor-css (3 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `elem-regenerate-css` | Regenerate the Elementor CSS cache | Write |
| `elem-clear-css-cache` | Clear all Elementor CSS cache files | Write |
| `elem-get-css-cache-info` | Get info about the CSS cache | Read |

## elementor-maintenance (10 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `elem-get-system-info` | Get Elementor system info | Read |
| `elem-replace-urls` | Replace old URLs with new URLs in all content | Write |
| `elem-get-maintenance-mode` | Get maintenance mode settings | Read |
| `elem-update-maintenance-mode` | Update maintenance mode settings | Write |
| `elem-get-roles` | Get Elementor role restrictions | Read |
| `elem-update-role` | Update role restrictions for a role | Write |
| `elem-get-integrations` | Get Elementor integration settings | Read |
| `elem-update-integration` | Update a specific Elementor integration | Write |
| `elem-get-libraries-info` | Get info about template libraries | Read |
| `elem-reset-disabled-elements` | Re-enable all disabled Elementor elements | Write |
