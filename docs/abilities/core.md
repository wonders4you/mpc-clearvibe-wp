# Core Abilities (181)

The core plugin provides 181 abilities across 20 categories. All abilities are prefixed with `mpc-clearvibe-wp/`.

## Categories

| Category | Count | Default | Description |
|----------|-------|---------|-------------|
| my | 1 | Enabled | Greeting / health check |
| content | 38 | Enabled | Posts, pages, custom post types, categories, tags, media, revisions, bulk operations |
| site | 3 | Enabled | Site info, user info, environment info |
| meta | 12 | Enabled | Post, user, term, comment meta CRUD |
| media | 10 | Enabled | Attachment details, meta, thumbnails, image editing |
| users | 14 | Enabled | Users, roles, capabilities, application passwords |
| comments | 9 | Enabled | Comments CRUD, moderation, bulk operations |
| plugins | 14 | **Disabled** | Plugin management |
| menus | 9 | Enabled | Navigation menus |
| widgets | 7 | Enabled | Sidebars, widgets |
| options | 9 | Enabled | WordPress options |
| system | 34 | **Disabled** | System operations, DB, cron, cache, updates |
| taxonomy | 6 | Enabled | Custom taxonomies |
| themes | 10 | Enabled | Theme management |
| multisite | 9 | Enabled | Multisite management |
| tools | 6 | Enabled | Export, health, email, GDPR, audit log |
| resources | 12 | Enabled | MCP resources (read-only) |
| prompts | 7 | Enabled | MCP prompts |
| blocks | 25 | Enabled | Block patterns, templates, reusable blocks, global styles |
| snippets | 9 | **Disabled** | WPCode snippets |

## my (1 ability)

| Ability | Description | R/W |
|---------|-------------|-----|
| `my-hello-world` | Greeting with optional site name | Read |

## content (38 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `content-list-posts` | List posts with pagination and filters | Read |
| `content-get-post` | Get a single post by ID | Read |
| `content-create-post` | Create a new post | Write |
| `content-update-post` | Update an existing post | Write |
| `content-delete-post` | Move a post to trash or delete permanently | Write |
| `content-list-pages` | List pages with pagination | Read |
| `content-get-page` | Get a single page by ID | Read |
| `content-create-page` | Create a new page | Write |
| `content-update-page` | Update an existing page | Write |
| `content-delete-page` | Delete a page | Write |
| `content-list-categories` | List categories | Read |
| `content-create-category` | Create a category | Write |
| `content-update-category` | Update a category | Write |
| `content-list-tags` | List tags | Read |
| `content-create-tag` | Create a tag | Write |
| `content-update-tag` | Update a tag | Write |
| `content-get-term` | Get a single taxonomy term | Read |
| `content-list-media` | List media attachments | Read |
| `content-upload-media` | Upload a file to the media library | Write |
| `content-upload-media-base64` | Upload a base64-encoded file | Write |
| `content-set-featured-image` | Set or remove a featured image | Write |
| `content-assign-terms` | Assign terms to a post | Write |
| `content-remove-terms` | Remove terms from a post | Write |
| `content-delete-term` | Delete a taxonomy term | Write |
| `content-list-revisions` | List revisions for a post or page | Read |
| `content-get-revision` | Get a single revision | Read |
| `content-restore-revision` | Restore a revision | Write |
| `content-patch-post` | Find and replace text in a post | Write |
| `content-patch-page` | Find and replace text in a page | Write |
| `content-duplicate` | Duplicate a post or page | Write |
| `content-bulk-update-status` | Update status of multiple posts | Write |
| `content-bulk-delete` | Delete or trash multiple posts | Write |
| `content-search` | Search posts and pages | Read |
| `content-list-custom-posts` | List posts of any registered post type | Read |
| `content-get-custom-post` | Get a single post of any post type | Read |
| `content-create-custom-post` | Create a post of any post type | Write |
| `content-update-custom-post` | Update a post of any post type | Write |
| `content-delete-custom-post` | Delete a post of any post type | Write |

## site (3 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `site-get-site-info` | General site information | Read |
| `site-get-user-info` | Current user information | Read |
| `site-get-environment-info` | PHP, theme and plugin summary | Read |

## meta (12 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `meta-get-post-meta` | Get post meta by key | Read |
| `meta-update-post-meta` | Add or update post meta | Write |
| `meta-delete-post-meta` | Delete post meta by key | Write |
| `meta-get-user-meta` | Get user meta by key | Read |
| `meta-update-user-meta` | Add or update user meta | Write |
| `meta-delete-user-meta` | Delete user meta by key | Write |
| `meta-get-term-meta` | Get term meta by key | Read |
| `meta-update-term-meta` | Add or update term meta | Write |
| `meta-delete-term-meta` | Delete term meta by key | Write |
| `meta-get-comment-meta` | Get comment meta by key | Read |
| `meta-update-comment-meta` | Add or update comment meta | Write |
| `meta-delete-comment-meta` | Delete comment meta by key | Write |

## media (10 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `media-get-meta` | Get media attachment meta | Read |
| `media-update-meta` | Add or update media meta | Write |
| `media-delete-meta` | Delete media attachment meta | Write |
| `media-get-attachment` | Get attachment details and sizes | Read |
| `media-update-attachment` | Update attachment title, caption, alt text | Write |
| `media-delete-attachment` | Delete an attachment | Write |
| `media-upload-base64` | Upload from base64-encoded bytes | Write |
| `media-regenerate-thumbnails` | Regenerate image metadata and thumbnails | Write |
| `media-image-sizes` | List registered image sizes | Read |
| `media-edit-image` | Rotate, flip, resize or crop an image | Write |

## users (14 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `users-list` | List users | Read |
| `users-get` | Get a user | Read |
| `users-create` | Create a user | Write |
| `users-update` | Update a user | Write |
| `users-delete` | Delete a user with optional reassignment | Write |
| `users-list-roles` | List all roles and capabilities | Read |
| `users-get-role` | Get capabilities for a role | Read |
| `users-create-role` | Create a custom role | Write |
| `users-delete-role` | Delete a custom role | Write |
| `users-add-role-cap` | Add a capability to a role | Write |
| `users-remove-role-cap` | Remove a capability from a role | Write |
| `users-list-user-caps` | List capabilities of a user | Read |
| `users-create-restricted-application-password` | Create a scoped application password | Write |
| `users-revoke-current-application-password` | Revoke current application password | Write |

## comments (9 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `comments-list` | List comments | Read |
| `comments-get` | Get a comment | Read |
| `comments-create` | Create a comment | Write |
| `comments-reply` | Reply to a comment | Write |
| `comments-delete` | Delete a comment | Write |
| `comments-update-author-url` | Update comment author URL | Write |
| `comments-update-status` | Approve, hold, spam or trash | Write |
| `comments-bulk-update-status` | Update status of multiple comments | Write |
| `comments-bulk-delete` | Delete multiple comments | Write |

## plugins (14 abilities — disabled by default)

| Ability | Description | R/W |
|---------|-------------|-----|
| `plugins-list` | List installed plugins | Read |
| `plugins-get` | Get detailed plugin info | Read |
| `plugins-list-updates` | List plugins with updates | Read |
| `plugins-update` | Update a single plugin | Write |
| `plugins-delete` | Delete an inactive plugin | Write |
| `plugins-activate` | Activate a plugin | Write |
| `plugins-deactivate` | Deactivate a plugin | Write |
| `plugins-switch` | Activate one, deactivate another | Write |
| `plugins-upload` | Upload a plugin ZIP | Write |
| `plugins-upload-base64` | Upload a plugin ZIP from base64 | Write |
| `plugins-search-directory` | Search WordPress.org plugin directory | Read |
| `plugins-install-directory` | Install from WordPress.org by slug | Write |
| `plugins-list-auto-updates` | List auto-update status | Read |
| `plugins-set-auto-updates` | Enable or disable auto-updates | Write |

## menus (9 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `menus-list` | List navigation menus | Read |
| `menus-get-items` | Get items of a menu | Read |
| `menus-create` | Create a new menu | Write |
| `menus-delete` | Delete a menu | Write |
| `menus-add-item` | Add an item to a menu | Write |
| `menus-update-item` | Update a menu item | Write |
| `menus-upsert-item` | Create or update a menu item | Write |
| `menus-delete-item` | Delete a menu item | Write |
| `menus-assign-location` | Assign a menu to a location | Write |

## widgets (7 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `widgets-list-sidebars` | List registered sidebars | Read |
| `widgets-get-sidebar` | List widgets in a sidebar | Read |
| `widgets-list-available` | List available widget types | Read |
| `widgets-list-locations` | List widget locations | Read |
| `widgets-add-to-sidebar` | Add a widget to a sidebar | Write |
| `widgets-remove` | Remove a widget from a sidebar | Write |
| `widgets-update` | Update a widget instance | Write |

## options (9 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `options-get` | Get a WordPress option | Read |
| `options-update` | Update a WordPress option | Write |
| `options-list` | List options by prefix | Read |
| `options-add` | Add a new option | Write |
| `options-delete` | Delete an option | Write |
| `options-set-autoload` | Enable or disable autoload | Write |
| `options-list-autoloaded` | List autoloaded options | Read |
| `options-pluck` | Extract a nested key via dot-notation | Read |
| `options-patch` | Surgical find-and-replace in an option | Write |

## system (34 abilities — disabled by default)

| Ability | Description | R/W |
|---------|-------------|-----|
| `system-get-transient` | Get a transient value | Read |
| `system-set-transient` | Set a transient value | Write |
| `system-delete-transient` | Delete a transient | Write |
| `system-list-cron-events` | List scheduled cron events | Read |
| `system-run-cron-event` | Run a scheduled cron event | Write |
| `system-flush-rewrite-rules` | Flush rewrite rules | Write |
| `system-list-rewrite-rules` | List current rewrite rules | Read |
| `system-list-post-types` | List registered post types | Read |
| `system-list-taxonomies` | List registered taxonomies | Read |
| `system-create-post-type` | Register a custom post type | Write |
| `system-delete-post-type` | Delete a custom post type | Write |
| `system-ability-timings` | Return ability timing statistics | Read |
| `system-debug-log` | Read the WordPress debug log | Read |
| `system-debug-status` | Report WP_DEBUG and WP_DEBUG_LOG | Read |
| `system-flush-cache` | Flush the object cache | Write |
| `system-list-database-tables` | List database tables | Read |
| `system-optimize-database` | Optimize MyISAM tables | Write |
| `system-list-languages` | List installed languages | Read |
| `system-install-language` | Install a language pack | Write |
| `system-update-translations` | Download updated translations | Write |
| `system-check-updates` | Check for core/plugin/theme updates | Read |
| `system-maintenance-mode` | Enable or disable maintenance mode | Write |
| `system-server-info` | Server and PHP environment info | Read |
| `system-db-query` | Run a read-only SQL query | Read |
| `system-search-replace` | Search-and-replace across DB tables | Write |
| `system-update-core` | Update WordPress core | Write |
| `system-update-db` | Run database upgrade procedure | Write |
| `system-verify-checksums` | Verify core file integrity | Read |
| `system-set-permalink-structure` | Set permalink structure | Write |
| `system-cache-type` | Detect active cache backend | Read |
| `system-get-config` | Return wp-config.php constants | Read |
| `system-purge-cache-plugin` | Purge third-party cache plugin | Write |
| `system-job-status` | Get status of an async job | Read |
| `system-job-list` | List recent async jobs | Read |

## taxonomy (6 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `taxonomy-associate-with-post-type` | Register taxonomy for a post type | Write |
| `taxonomy-disassociate-from-post-type` | Remove taxonomy from post type | Write |
| `taxonomy-create` | Register a custom taxonomy | Write |
| `taxonomy-delete` | Delete a custom taxonomy | Write |
| `taxonomy-list-post-terms` | List terms assigned to a post | Read |
| `taxonomy-merge-terms` | Merge a term into another | Write |

## themes (10 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `themes-list` | List installed themes | Read |
| `themes-get` | Get detailed theme info | Read |
| `themes-activate` | Activate a theme | Write |
| `themes-delete` | Delete an inactive theme | Write |
| `themes-update` | Update a single theme | Write |
| `themes-install` | Install from WordPress.org by slug | Write |
| `themes-install-zip` | Install from a ZIP path or URL | Write |
| `themes-list-updates` | List themes with updates | Read |
| `themes-get-customizer` | Get current theme modifications | Read |
| `themes-set-customizer` | Set a theme modification value | Write |

## multisite (9 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `multisite-list-sites` | List sites in a network | Read |
| `multisite-get-site` | Get a single site | Read |
| `multisite-create-site` | Create a new site | Write |
| `multisite-update-site` | Update a site | Write |
| `multisite-delete-site` | Delete or mark a site as deleted | Write |
| `multisite-switch-site` | Load another site's info | Write |
| `multisite-get-site-meta` | Get site meta | Read |
| `multisite-update-site-meta` | Add or update site meta | Write |
| `multisite-delete-site-meta` | Delete site meta | Write |

## tools (6 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `tools-export` | Export content to WXR file | Read |
| `tools-health-report` | Site health summary | Read |
| `tools-send-email` | Send an email with wp_mail | Write |
| `tools-export-personal-data` | Create personal data export request | Write |
| `tools-erase-personal-data` | Create personal data erasure request | Write |
| `tools-list-audit-log` | List recent MCP tool executions | Read |

## resources (12 abilities — MCP resources, read-only)

| Ability | URI | Description |
|---------|-----|-------------|
| `resources-site-info` | `wordpress://site/info` | Site name, description, URL, language, timezone, WP version |
| `resources-post` | `wordpress://posts/{id}` | Full content of a single post |
| `resources-posts` | `wordpress://posts` | List of published posts |
| `resources-page` | `wordpress://pages/{id}` | Full content of a single page |
| `resources-media` | `wordpress://media/{id}` | Attachment metadata |
| `resources-user` | `wordpress://users/{id}` | Public profile data for a user |
| `resources-option` | `wordpress://options/{key}` | Value of a WordPress option |
| `resources-categories` | `wordpress://categories` | All categories with IDs and counts |
| `resources-comments` | `wordpress://comments` | Recent comments |
| `resources-plugins` | `wordpress://plugins` | Installed plugins |
| `resources-themes` | `wordpress://themes` | Installed themes |
| `resources-active-theme` | `wordpress://theme/active` | Active theme details |

## prompts (7 abilities — MCP prompts)

| Ability | Inputs | Description |
|---------|--------|-------------|
| `prompts-write-blog-post` | `topic`, `tone`, `keywords` | Prompt for writing a blog post |
| `prompts-summarize-comments` | `status`, `limit` | Prompt for summarizing comments |
| `prompts-seo-description` | `post_id`, `max_length` | Prompt for SEO meta description |
| `prompts-review-post` | `post_id`, `focus` | Prompt for reviewing a post |
| `prompts-draft-from-outline` | `outline`, `post_type` | Prompt for drafting from outline |
| `prompts-improve-readability` | `post_id` | Prompt for improving readability |
| `prompts-weekly-summary` | `days` | Prompt for weekly content summary |

## blocks (25 abilities)

| Ability | Description | R/W |
|---------|-------------|-----|
| `blocks-list-patterns` | List all registered block patterns | Read |
| `blocks-get-pattern` | Get a block pattern by name | Read |
| `blocks-create-pattern` | Register a custom block pattern | Write |
| `blocks-delete-pattern` | Unregister a block pattern | Write |
| `blocks-list-pattern-categories` | List block pattern categories | Read |
| `blocks-list-templates` | List block templates (FSE) | Read |
| `blocks-get-template` | Get a block template by ID | Read |
| `blocks-create-template` | Create a block template | Write |
| `blocks-update-template` | Update a block template | Write |
| `blocks-delete-template` | Delete a block template | Write |
| `blocks-list-template-parts` | List template parts | Read |
| `blocks-get-template-part` | Get a template part | Read |
| `blocks-create-template-part` | Create a template part | Write |
| `blocks-update-template-part` | Update a template part | Write |
| `blocks-delete-template-part` | Delete a template part | Write |
| `blocks-list-reusable` | List reusable (synced) blocks | Read |
| `blocks-get-reusable` | Get a reusable block | Read |
| `blocks-create-reusable` | Create a reusable block | Write |
| `blocks-update-reusable` | Update a reusable block | Write |
| `blocks-delete-reusable` | Delete a reusable block | Write |
| `blocks-get-global-styles` | Get global styles (theme.json) | Read |
| `blocks-update-global-styles` | Update global styles | Write |
| `blocks-list-block-categories` | List block categories | Read |
| `blocks-list-block-types` | List all registered block types | Read |
| `blocks-design-preflight` | Design tokens, patterns, styles, classNames | Read |

## snippets (9 abilities — disabled by default)

| Ability | Description | R/W |
|---------|-------------|-----|
| `snippets-list` | List WPCode snippets | Read |
| `snippets-get` | Get a single WPCode snippet | Read |
| `snippets-list-locations` | List auto-insert locations | Read |
| `snippets-list-types` | List supported code types | Read |
| `snippets-create` | Create a new snippet (saved inactive) | Write |
| `snippets-update` | Update an existing snippet | Write |
| `snippets-delete` | Delete or trash a snippet | Write |
| `snippets-activate` | Activate a snippet | Write |
| `snippets-deactivate` | Deactivate a snippet | Write |
