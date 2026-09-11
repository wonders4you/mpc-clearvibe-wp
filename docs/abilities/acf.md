# ACF Abilities (30)

The For-ACF add-on adds 30 abilities across 4 categories. All abilities are prefixed with `mpc-clearvibe-wp/acf-`. Categories are **enabled by default**.

## Categories

| Category | Count | Description |
|----------|-------|-------------|
| `acf` | 6 | Version, field types, export/import, ACF settings |
| `acf-fields` | 8 | Field groups and fields CRUD |
| `acf-values` | 10 | Field values for posts, users, terms, attachments |
| `acf-options` | 6 | Options pages and values |

## acf (6 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `acf-get-version` | Get ACF version and type (free/pro) | Read |
| `acf-list-field-types` | List all available ACF field types | Read |
| `acf-export-field-groups` | Export field groups as JSON | Read |
| `acf-import-field-groups` | Import field groups from JSON | Write |
| `acf-get-acf-options` | Get ACF plugin settings | Read |
| `acf-update-acf-options` | Update ACF plugin settings | Write |

## acf-fields (8 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `acf-list-field-groups` | List all ACF field groups | Read |
| `acf-get-field-group` | Get a single field group by ID | Read |
| `acf-create-field-group` | Create a new ACF field group | Write |
| `acf-update-field-group` | Update an existing field group | Write |
| `acf-delete-field-group` | Delete an ACF field group | Write |
| `acf-list-fields` | List fields in a field group | Read |
| `acf-get-field` | Get a single field by key | Read |
| `acf-delete-field` | Delete a field by key | Write |

## acf-values (10 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `acf-get-post-value` | Get a field value for a post | Read |
| `acf-update-post-value` | Update a field value for a post | Write |
| `acf-delete-post-value` | Delete a field value for a post | Write |
| `acf-get-all-post-values` | Get all ACF field values for a post | Read |
| `acf-get-user-value` | Get a field value for a user | Read |
| `acf-update-user-value` | Update a field value for a user | Write |
| `acf-get-term-value` | Get a field value for a term | Read |
| `acf-update-term-value` | Update a field value for a term | Write |
| `acf-get-attachment-value` | Get a field value for an attachment | Read |
| `acf-update-attachment-value` | Update a field value for an attachment | Write |

## acf-options (6 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `acf-list-options-pages` | List all registered ACF options pages | Read |
| `acf-get-options-page` | Get details of an options page by slug | Read |
| `acf-create-options-page` | Create a new ACF options page (ACF Pro) | Write |
| `acf-get-options-value` | Get a field value from an options page | Read |
| `acf-update-options-value` | Update a field value on an options page | Write |
| `acf-delete-options-value` | Delete a field value from an options page | Write |
