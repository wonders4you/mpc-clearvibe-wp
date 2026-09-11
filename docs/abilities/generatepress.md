# GeneratePress Abilities (85)

The For-GeneratePress add-on adds 85 abilities across 17 categories. All abilities are prefixed with `mpc-clearvibe-wp/gp-`. Categories are **enabled by default**.

## Categories

| Category | Count | Description |
|----------|-------|-------------|
| `generatepress` | 12 | General settings, copyright, import/export, modules |
| `generatepress-colors` | 3 | Color palette |
| `generatepress-typography` | 3 | Typography settings |
| `generatepress-spacing` | 3 | Spacing settings |
| `generatepress-blog` | 3 | Blog module |
| `generatepress-menu` | 6 | Menu Plus, Secondary Nav |
| `generatepress-elements` | 16 | GP Elements (Hook, Layout, Header, Block) |
| `generatepress-page-header` | 4 | Page Header per post |
| `generatepress-disable` | 2 | Disable elements per post |
| `generatepress-hooks` | 2 | Action hooks and filters reference |
| `generatepress-sites` | 2 | Site Library |
| `generatepress-woo` | 5 | GP WooCommerce integration |
| `generatepress-utility` | 4 | Any GP option, regenerate CSS |
| `generatepress-generateblocks` | 8 | GenerateBlocks global styles, patterns |
| `generatepress-custom-css` | 4 | Custom CSS |
| `generatepress-audit` | 3 | Audits |
| `generatepress-theme-mods` | 5 | Theme mods |

## generatepress (12 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `gp-get-settings` | Get main GeneratePress settings | Read |
| `gp-update-settings` | Update main settings (partial merge) | Write |
| `gp-get-copyright` | Get copyright text | Read |
| `gp-update-copyright` | Update copyright text | Write |
| `gp-export-settings` | Export all GP settings as JSON | Read |
| `gp-import-settings` | Import GP settings from JSON | Write |
| `gp-reset-settings` | Reset main settings to defaults | Write |
| `gp-get-defaults` | Get default settings | Read |
| `gp-get-theme-info` | Get GP version, GP Premium version, modules | Read |
| `gp-list-modules` | List all GP Premium modules and status | Read |
| `gp-get-module-status` | Check if a module is active | Read |
| `gp-update-module-status` | Enable or disable a module | Write |

## generatepress-colors (3 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `gp-get-colors` | Get all GP color settings | Read |
| `gp-update-colors` | Update GP colors (partial) | Write |
| `gp-reset-colors` | Reset colors to defaults | Write |

## generatepress-typography (3 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `gp-get-typography` | Get all GP typography settings | Read |
| `gp-update-typography` | Update GP typography (partial) | Write |
| `gp-reset-typography` | Reset typography to defaults | Write |

## generatepress-spacing (3 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `gp-get-spacing` | Get all GP spacing settings | Read |
| `gp-update-spacing` | Update GP spacing (partial) | Write |
| `gp-reset-spacing` | Reset spacing to defaults | Write |

## generatepress-blog (3 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `gp-get-blog-settings` | Get GP Blog module settings | Read |
| `gp-update-blog-settings` | Update Blog module (partial) | Write |
| `gp-reset-blog-settings` | Reset blog settings to defaults | Write |

## generatepress-menu (6 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `gp-get-menu-plus-settings` | Get Menu Plus settings | Read |
| `gp-update-menu-plus-settings` | Update Menu Plus (partial) | Write |
| `gp-reset-menu-plus` | Reset Menu Plus to defaults | Write |
| `gp-get-secondary-nav-settings` | Get Secondary Nav settings | Read |
| `gp-update-secondary-nav-settings` | Update Secondary Nav (partial) | Write |
| `gp-reset-secondary-nav` | Reset Secondary Nav to defaults | Write |

## generatepress-elements (16 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `gp-list-elements` | List GP Elements (optional type filter) | Read |
| `gp-get-element` | Get a single GP Element by ID | Read |
| `gp-create-hook-element` | Create a Hook Element | Write |
| `gp-update-hook-element` | Update a Hook Element | Write |
| `gp-create-layout-element` | Create a Layout Element | Write |
| `gp-update-layout-element` | Update a Layout Element | Write |
| `gp-create-header-element` | Create a Header Element (page hero) | Write |
| `gp-update-header-element` | Update a Header Element | Write |
| `gp-create-block-element` | Create a Block Element (Gutenberg at hook) | Write |
| `gp-update-block-element` | Update a Block Element | Write |
| `gp-delete-element` | Delete a GP Element | Write |
| `gp-get-element-display-rules` | Get display rules for an Element | Read |
| `gp-update-element-display-rules` | Update display rules for an Element | Write |
| `gp-get-element-meta` | Get all meta for an Element | Read |
| `gp-update-element-meta` | Update a meta key for an Element | Write |
| `gp-upsert-block-element` | Idempotently create or update a Block Element | Write |

## generatepress-page-header (4 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `gp-get-page-header` | Get Page Header for a post | Read |
| `gp-update-page-header` | Update Page Header for a post | Write |
| `gp-delete-page-header` | Remove Page Header from a post | Write |
| `gp-list-page-headers` | List posts with Page Header enabled | Read |

## generatepress-disable (2 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `gp-get-disabled-elements` | Get disabled elements for a post | Read |
| `gp-update-disabled-elements` | Update disabled elements for a post | Write |

## generatepress-hooks (2 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `gp-list-hooks` | List all available GP action hooks | Read |
| `gp-list-filters` | List all available GP filters | Read |

## generatepress-sites (2 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `gp-list-sites` | List available Site Library sites | Read |
| `gp-get-site-info` | Get details about a Site Library site | Read |

## generatepress-woo (5 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `gp-get-woo-settings` | Get GP WooCommerce integration settings | Read |
| `gp-update-woo-settings` | Update GP WooCommerce integration | Write |
| `gp-get-woo-colors` | Get GP WooCommerce color settings | Read |
| `gp-update-woo-colors` | Update GP WooCommerce colors | Write |
| `gp-reset-woo-settings` | Reset GP WooCommerce settings | Write |

## generatepress-utility (4 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `gp-get-option` | Get any GP option by key | Read |
| `gp-update-option` | Update any GP option (partial merge) | Write |
| `gp-list-option-keys` | List all known GP option keys | Read |
| `gp-regenerate-css` | Regenerate the GP dynamic CSS cache | Write |

## generatepress-generateblocks (8 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `gp-gb-get-global-styles` | Get GenerateBlocks global styles | Read |
| `gp-gb-update-global-styles` | Update GenerateBlocks global styles | Write |
| `gp-gb-get-options` | Get GenerateBlocks options | Read |
| `gp-gb-update-options` | Update GenerateBlocks options | Write |
| `gp-gb-list-control-surface` | List available control surfaces | Read |
| `gp-gb-list-pattern-libraries` | List pattern libraries | Read |
| `gp-gb-search-pattern-library` | Search pattern library | Read |
| `gp-gb-clear-cache` | Clear GenerateBlocks CSS cache | Write |

## generatepress-custom-css (4 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `gp-get-custom-css` | Get GeneratePress custom CSS | Read |
| `gp-update-custom-css` | Replace custom CSS entirely | Write |
| `gp-patch-custom-css` | Append CSS to custom CSS | Write |
| `gp-clear-custom-css` | Remove all custom CSS | Write |

## generatepress-audit (3 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `gp-audit-duplicate-headlines` | Find duplicate H1 headlines (can fix) | Read/Write |
| `gp-audit-page-layout-meta` | Audit layout meta for all pages | Read |
| `gp-audit-featured-image-sizes` | Audit featured image sizes | Read |

## generatepress-theme-mods (5 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `gp-get-theme-mods` | Get all GeneratePress theme modifications | Read |
| `gp-update-theme-mods` | Update theme modifications (partial merge) | Write |
| `gp-list-setting-keys` | List all known GeneratePress setting keys | Read |
| `gp-list-control-surface` | List available control surfaces | Read |
| `gp-list-module-settings` | List all settings for a specific module | Read |
