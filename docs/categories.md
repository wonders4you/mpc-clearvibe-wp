# Categories

## Core Plugin (20 categories)

| Category | Abilities | Default | Description |
|----------|----------|---------|-------------|
| `my` | 1 | Enabled | Greeting / health check |
| `content` | 38 | Enabled | Posts, pages, custom post types, categories, tags, media upload, revisions, bulk operations |
| `site` | 3 | Enabled | Site info, current user info, environment info |
| `meta` | 12 | Enabled | Post, user, term, comment meta CRUD |
| `media` | 10 | Enabled | Attachment details, meta, thumbnails, image editing |
| `users` | 14 | Enabled | Users, roles, capabilities, application passwords |
| `comments` | 9 | Enabled | Comments CRUD, moderation, bulk operations |
| `plugins` | 14 | **Disabled** | Plugin list, activate, deactivate, install, update, delete, auto-updates |
| `menus` | 9 | Enabled | Navigation menus CRUD, items, locations |
| `widgets` | 7 | Enabled | Sidebars, widgets CRUD |
| `options` | 9 | Enabled | WordPress options CRUD, autoload, patch |
| `system` | 34 | **Disabled** | Transients, cron, cache, database, languages, debug, search-replace, core updates, permalinks, async jobs |
| `taxonomy` | 6 | Enabled | Custom taxonomy CRUD, term management |
| `themes` | 10 | Enabled | Themes list, activate, install, update, customizer |
| `multisite` | 9 | Enabled | Multisite site management |
| `tools` | 6 | Enabled | WXR export, site health, email, GDPR data, audit log |
| `resources` | 12 | Enabled | MCP resources (read-only): site, posts, pages, media, users, options, categories, comments, plugins, themes |
| `prompts` | 7 | Enabled | MCP prompts: blog post, comment summary, SEO, review, draft, readability, weekly summary |
| `blocks` | 25 | Enabled | Block patterns, templates, template parts, reusable blocks, global styles, design preflight |
| `snippets` | 9 | **Disabled** | WPCode snippets CRUD, activate, deactivate |

## Add-On Categories

### WooCommerce (2 categories)

| Category | Abilities | Default | Description |
|----------|----------|---------|-------------|
| `for-woo` | 103 | **Disabled** | Products, orders, coupons, shipping, tax, reports, settings, variations, attributes, reviews, notes, downloads, emails |
| `for-woo-customers` | 10 | **Disabled** | Customer data (personal data — GDPR warning) |

### GeneratePress (17 categories)

| Category | Abilities | Default | Description |
|----------|----------|---------|-------------|
| `generatepress` | 12 | Enabled | General settings, copyright, import/export, modules |
| `generatepress-colors` | 3 | Enabled | Color palette |
| `generatepress-typography` | 3 | Enabled | Typography settings |
| `generatepress-spacing` | 3 | Enabled | Spacing settings |
| `generatepress-blog` | 3 | Enabled | Blog module |
| `generatepress-menu` | 6 | Enabled | Menu Plus, Secondary Nav |
| `generatepress-elements` | 16 | Enabled | GP Elements (Hook, Layout, Header, Block) CRUD |
| `generatepress-page-header` | 4 | Enabled | Page Header per post |
| `generatepress-disable` | 2 | Enabled | Disable elements per post |
| `generatepress-hooks` | 2 | Enabled | Action hooks and filters reference |
| `generatepress-sites` | 2 | Enabled | Site Library |
| `generatepress-woo` | 5 | Enabled | GP WooCommerce integration |
| `generatepress-utility` | 4 | Enabled | Any GP option, regenerate CSS |
| `generatepress-generateblocks` | 8 | Enabled | GenerateBlocks global styles, options, patterns |
| `generatepress-custom-css` | 4 | Enabled | Custom CSS read, update, patch, clear |
| `generatepress-audit` | 3 | Enabled | Duplicate headlines, layout meta, featured image audits |
| `generatepress-theme-mods` | 5 | Enabled | Theme mods, setting keys, control surface |

### ACF (4 categories)

| Category | Abilities | Default | Description |
|----------|----------|---------|-------------|
| `acf` | 6 | Enabled | Version, field types, export/import, ACF settings |
| `acf-fields` | 8 | Enabled | Field groups and fields CRUD |
| `acf-values` | 10 | Enabled | Field values for posts, users, terms, attachments |
| `acf-options` | 6 | Enabled | Options pages and values |

### Elementor (6 categories)

| Category | Abilities | Default | Description |
|----------|----------|---------|-------------|
| `elementor` | 15 | Enabled | Version, settings, templates CRUD, import/export |
| `elementor-kit` | 8 | Enabled | Kit settings, global colors, typography |
| `elementor-popups` | 10 | Enabled | Popups CRUD, triggers, display settings |
| `elementor-widgets` | 4 | Enabled | Widget types, controls, defaults |
| `elementor-css` | 3 | Enabled | CSS cache regenerate, clear, info |
| `elementor-maintenance` | 10 | Enabled | System info, replace URLs, maintenance mode, roles |

### Breakdance (6 categories — all disabled by default)

| Category | Abilities | Default | Description |
|----------|----------|---------|-------------|
| `breakdance` | 4 | **Disabled** | Version, info, global settings |
| `breakdance-templates` | 8 | **Disabled** | Templates CRUD, conditions, types |
| `breakdance-content` | 8 | **Disabled** | Builder tree, nodes, render, cache |
| `breakdance-global` | 15 | **Disabled** | Global settings, classes, presets, variables, CSS |
| `breakdance-forms` | 4 | **Disabled** | Form submissions (personal data — GDPR warning) |
| `breakdance-maintenance` | 5 | **Disabled** | CSS cache, settings export/import |

### CLI (1 category)

| Category | Abilities | Default | Description |
|----------|----------|---------|-------------|
| `system-cli` | 2 | **Disabled** | Whitelisted command-line execution |

## How to Enable/Disable Categories

1. Go to **Settings → ClearVibe AI** in WordPress admin.
2. Click the **Abilities** tab.
3. Each category is a card with a toggle button.
4. Click **Enable this category** or **Disable this category**.
5. You can also enable/disable individual abilities within a category.
6. Click **Save Changes** at the top.

## Why Some Categories Are Disabled by Default

Categories that can install code, execute code, or perform system-level operations are disabled by default as a safety measure:

- **Plugins** — can install and delete plugin code
- **System** — system operations, database queries, core updates
- **Snippets** — code execution via WPCode
- **WooCommerce** — store management (financial data)
- **WooCommerce customers** — personal data (GDPR)
- **Breakdance** (all) — builder content and global design
- **CLI** — shell command execution

Enabling a category is the "acceptance step" — once enabled, abilities in that category run without additional confirmation prompts (unless they are marked as dangerous, in which case per-ability confirmation still applies).
