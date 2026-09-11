# Breakdance Abilities (44)

The For-Breakdance add-on adds 44 abilities across 6 categories. All abilities are prefixed with `mpc-clearvibe-wp/bd-`. All categories are **disabled by default**.

## Categories

| Category | Count | Description |
|----------|-------|-------------|
| `breakdance` | 4 | Version, info, global settings |
| `breakdance-templates` | 8 | Templates CRUD, conditions, types |
| `breakdance-content` | 8 | Builder tree, nodes, render, cache |
| `breakdance-global` | 15 | Global settings, classes, presets, variables, CSS |
| `breakdance-forms` | 4 | Form submissions (personal data — GDPR warning) |
| `breakdance-maintenance` | 5 | CSS cache, settings export/import |

## breakdance (4 abilities — disabled by default)

| Ability | Description | R/W |
|---------|-------------|-----|
| `bd-get-version` | Get Breakdance version and brand mode | Read |
| `bd-get-info` | Get post types, template types, content counts | Read |
| `bd-get-settings` | Get Breakdance global settings | Read |
| `bd-update-settings` | Update Breakdance global settings (shallow merge) | Write |

## breakdance-templates (8 abilities — disabled by default)

| Ability | Description | R/W |
|---------|-------------|-----|
| `bd-list-templates` | List all Breakdance template posts | Read |
| `bd-get-template` | Get a single Breakdance template by ID | Read |
| `bd-create-template` | Create a new Breakdance template | Write |
| `bd-update-template` | Update a Breakdance template post | Write |
| `bd-delete-template` | Delete a Breakdance template | Write |
| `bd-get-template-settings` | Get template conditions and type | Read |
| `bd-update-template-settings` | Update template conditions and type | Write |
| `bd-list-template-types` | List all available Breakdance template types | Read |

## breakdance-content (8 abilities — disabled by default)

| Ability | Description | R/W |
|---------|-------------|-----|
| `bd-get-builder-tree` | Read and decode the Breakdance element tree for a post | Read |
| `bd-update-builder-tree` | Replace the entire element tree for a post | Write |
| `bd-get-node` | Get a single element node by ID from the tree | Read |
| `bd-update-node` | Update a single element node by ID in the tree | Write |
| `bd-add-node` | Add a new element node to the tree | Write |
| `bd-delete-node` | Remove an element node by ID from the tree | Write |
| `bd-render-post` | Server-side render a post/template and return HTML | Read |
| `bd-clear-post-cache` | Clear the CSS cache for a single post | Write |

## breakdance-global (15 abilities — disabled by default)

| Ability | Description | R/W |
|---------|-------------|-----|
| `bd-get-global-settings` | Get the Breakdance global settings envelope | Read |
| `bd-update-global-settings` | Patch the Breakdance global settings | Write |
| `bd-list-global-classes` | List all Breakdance CSS selectors/classes | Read |
| `bd-get-global-class` | Get a single Breakdance CSS class by name | Read |
| `bd-create-global-class` | Create a new Breakdance CSS class | Write |
| `bd-update-global-class` | Update an existing Breakdance CSS class | Write |
| `bd-delete-global-class` | Delete a Breakdance CSS class by name | Write |
| `bd-list-presets` | List all Breakdance design presets | Read |
| `bd-get-preset` | Get a single Breakdance design preset by ID | Read |
| `bd-update-preset` | Update a Breakdance design preset | Write |
| `bd-list-variables` | List all Breakdance design variables | Read |
| `bd-get-variable` | Get a single Breakdance design variable by ID | Read |
| `bd-update-variable` | Update a Breakdance design variable | Write |
| `bd-get-global-css` | Get the Breakdance global custom CSS | Read |
| `bd-update-global-css` | Update the Breakdance global custom CSS | Write |

## breakdance-forms (4 abilities — disabled by default)

> **GDPR Warning:** Form submissions contain personal data (names, emails, IP addresses). Enable only if you accept the privacy risk.

| Ability | Description | R/W |
|---------|-------------|-----|
| `bd-list-form-submissions` | List Breakdance form submissions | Read |
| `bd-get-form-submission` | Get a single form submission by ID | Read |
| `bd-delete-form-submission` | Delete a form submission | Write |
| `bd-export-form-submissions` | Export form submissions as CSV/JSON | Read |

## breakdance-maintenance (5 abilities — disabled by default)

| Ability | Description | R/W |
|---------|-------------|-----|
| `bd-regenerate-css` | Regenerate the Breakdance CSS cache for all posts | Write |
| `bd-clear-cache-all` | Clear all Breakdance CSS cache | Write |
| `bd-get-cache-info` | Get info about the Breakdance CSS cache | Read |
| `bd-export-settings` | Export Breakdance global settings, presets, selectors, variables | Read |
| `bd-import-settings` | Import Breakdance settings from JSON | Write |
