# Agent Guide — How to Use MPC ClearVibe WP

> Copy this file and paste it into your AI agent (Claude, Codex, Cursor, Devin) as context. It tells the agent how to connect to a WordPress site via MCP and what it can do.

## What This Plugin Does

MPC ClearVibe WP turns a WordPress site into an MCP (Model Context Protocol) server. As an AI agent, you can connect to the site and call abilities to read, create, modify, and delete content — posts, pages, media, users, plugins, themes, WooCommerce, and more.

## How to Connect

The site exposes an MCP endpoint over HTTP. You need:

- **Endpoint URL:** `https://SITE_URL/wp-json/mcp/mcp-adapter-default-server`
- **Auth:** Basic Auth with a WordPress Application Password
- **Auth header:** `Authorization: Basic <base64(username:application-password)>`

Replace `SITE_URL` with the actual domain (e.g. `example.com`).

## MCP Protocol Flow

1. **Initialize** — send `initialize` request, server responds with capabilities
2. **Notify** — send `notifications/initialized`
3. **Discover** — call `tools/list` to see all available abilities
4. **Execute** — call `tools/call` with ability name and parameters

### Example: Initialize

```json
{"jsonrpc":"2.0","id":1,"method":"initialize","params":{"protocolVersion":"2024-11-05","capabilities":{},"clientInfo":{"name":"my-agent","version":"1.0"}}}
```

### Example: List Recent Posts

```json
{"jsonrpc":"2.0","id":2,"method":"tools/call","params":{"name":"mcp-adapter-execute-ability","arguments":{"ability_name":"mpc-clearvibe-wp/content-list-posts","parameters":{"per_page":5}}}}
```

### Example: Create a Draft Post

```json
{"jsonrpc":"2.0","id":3,"method":"tools/call","params":{"name":"mcp-adapter-execute-ability","arguments":{"ability_name":"mpc-clearvibe-wp/content-create-post","parameters":{"title":"Hello from AI","status":"draft","content":"This post was created by an AI agent."}}}}
```

## Ability Naming

All abilities are prefixed with `mpc-clearvibe-wp/`:

- `mpc-clearvibe-wp/content-list-posts` — list posts
- `mpc-clearvibe-wp/content-create-post` — create a post
- `mpc-clearvibe-wp/users-list` — list users
- `mpc-clearvibe-wp/plugins-activate` — activate a plugin
- `mpc-clearvibe-wp/for-woo-list-products` — list WooCommerce products
- `mpc-clearvibe-wp/gp-get-settings` — get GeneratePress settings
- `mpc-clearvibe-wp/elem-list-templates` — list Elementor templates
- `mpc-clearvibe-wp/bd-get-builder-tree` — get Breakdance builder tree
- `mpc-clearvibe-wp/acf-get-post-value` — get ACF field value

Full list: see the [Ability Reference](abilities/) docs.

## Key Categories

| Category | What You Can Do |
|----------|----------------|
| `content` | Posts, pages, custom post types, categories, tags, media upload, revisions, bulk operations |
| `media` | Attachment details, thumbnails, image editing |
| `users` | Users, roles, capabilities, scoped application passwords |
| `comments` | Comments CRUD, moderation |
| `menus` | Navigation menus |
| `widgets` | Sidebars, widgets |
| `options` | WordPress options |
| `taxonomy` | Custom taxonomies |
| `themes` | Theme management, customizer |
| `blocks` | Block patterns, templates, reusable blocks, global styles |
| `plugins` | Plugin management (disabled by default) |
| `system` | Transients, cron, cache, DB queries, search-replace (disabled by default) |
| `snippets` | WPCode snippets (disabled by default) |
| `tools` | Export, site health, email, audit log |
| `resources` | Read-only MCP resources |
| `prompts` | MCP prompts for content tasks |

### Add-on categories

| Add-on | Categories |
|--------|-----------|
| WooCommerce | `for-woo` (products, orders, coupons, shipping, tax), `for-woo-customers` (personal data) |
| GeneratePress | 17 categories — settings, colors, typography, elements, GenerateBlocks |
| ACF | `acf`, `acf-fields`, `acf-values`, `acf-options` |
| Elementor | `elementor`, `elementor-kit`, `elementor-popups`, `elementor-widgets`, `elementor-css`, `elementor-maintenance` |
| Breakdance | 6 categories (all disabled by default) — templates, content, global, forms, maintenance |
| CLI | `system-cli` (whitelisted shell commands, disabled by default) |

## Disabled Abilities

Some categories are disabled by default for safety. When you call a disabled ability, you get an error:

```
The ability "mpc-clearvibe-wp/plugins-list" is disabled because its category "Plugins" is turned off.
Enable the "Plugins" category in the ClearVibe AI admin panel (Settings → ClearVibe AI) to use this ability.
```

Tell the site admin to enable the category in **Settings → ClearVibe AI → Abilities tab**.

## Dangerous Actions and Confirmation

Some abilities require explicit confirmation before executing. These include:

- Deleting plugins, themes, users
- Updating options, transients
- Search-and-replace across the database
- Creating/activating code snippets
- Running CLI commands

### How to confirm

When you call a dangerous ability without confirmation, you get:

```json
{"error":{"code":"simple_press_mpc_confirmation_required","message":"This action requires confirmation. Set confirm_dangerous_action to the ability name."}}
```

Retry with `confirm_dangerous_action` set to the ability name:

```json
{"ability_name":"mpc-clearvibe-wp/plugins-delete","parameters":{"plugin":"hello-dolly","confirm_dangerous_action":"mpc-clearvibe-wp/plugins-delete"}}
```

### Dry-run preview

For `system-search-replace`, you can preview changes before applying:

```json
{"ability_name":"mpc-clearvibe-wp/system-search-replace","parameters":{"search":"old.com","replace":"new.com","dry_run":true}}
```

### Out-of-band approval

For maximum safety, the site admin can require approval. Call with `request_approval=true`:

```json
{"ability_name":"mpc-clearvibe-wp/plugins-delete","parameters":{"plugin":"hello-dolly","request_approval":true}}
```

This creates a pending operation. The admin approves it in wp-admin, then you retry with `confirm_dangerous_action` set to the op id (`op_abc123...`).

## Async Operations

Long-running abilities accept `run_async=true`:

```json
{"ability_name":"mpc-clearvibe-wp/system-search-replace","parameters":{"search":"old.com","replace":"new.com","run_async":true}}
```

Returns immediately with a `job_id`. Poll status:

```json
{"ability_name":"mpc-clearvibe-wp/system-job-status","parameters":{"job_id":"job_abc123..."}}
```

## MCP Annotations

Abilities are annotated as `readonly`, `destructive`, or `idempotent` based on their name:

- **readonly:** `get`, `list`, `is`, `has`, `count`, `search`, `audit`, `export`
- **destructive:** `delete`, `clear`, `reset`, `purge`, `remove`, `destroy`, `drop`, `truncate`
- **idempotent:** `upsert`, `update`, `regenerate`, `activate`, `import`, `set`

Use these to understand the nature of an ability before calling it.

## Audit Log

Every ability execution is logged — successes, failures, and permission denials. The site admin can review what you did in **Settings → ClearVibe AI → Audit log**.

You can also query it:

```json
{"ability_name":"mpc-clearvibe-wp/tools-list-audit-log","parameters":{"per_page":20}}
```

## Tips for Agents

1. **Start with read-only calls** — list posts, get site info, list users. Understand the site before making changes.
2. **Check if a category is enabled** — if you get a "disabled" error, tell the admin to enable it.
3. **Use dry-run for search-replace** — always preview before writing.
4. **Confirm dangerous actions** — set `confirm_dangerous_action` to the ability name.
5. **Use async for long operations** — export, search-replace, core updates.
6. **Respect builder content** — for Elementor/Breakdance posts, use the builder-specific abilities, not generic content writes.
7. **Check the audit log** — if something went wrong, review what was executed.
8. **Back up before writing** — remind the admin to back up before enabling write categories.
9. **Know your scope** — if you get a scope denial error, your bot password doesn't include that ability. Ask the admin to add it in MCP bots tab.

## Quick Reference

| What | Ability |
|------|---------|
| Site info | `mpc-clearvibe-wp/site-get-site-info` |
| List posts | `mpc-clearvibe-wp/content-list-posts` |
| Create post | `mpc-clearvibe-wp/content-create-post` |
| List users | `mpc-clearvibe-wp/users-list` |
| List plugins | `mpc-clearvibe-wp/plugins-list` |
| List WooCommerce products | `mpc-clearvibe-wp/for-woo-list-products` |
| Get GeneratePress settings | `mpc-clearvibe-wp/gp-get-settings` |
| List Elementor templates | `mpc-clearvibe-wp/elem-list-templates` |
| Get Breakdance builder tree | `mpc-clearvibe-wp/bd-get-builder-tree` |
| Get ACF field value | `mpc-clearvibe-wp/acf-get-post-value` |
| Search-replace (dry-run) | `mpc-clearvibe-wp/system-search-replace` with `dry_run: true` |
| Export WXR | `mpc-clearvibe-wp/tools-export` |
| Audit log | `mpc-clearvibe-wp/tools-list-audit-log` |

## Full Documentation

- [Installation](installation.md)
- [MCP Setup](mcp-setup.md)
- [Categories](categories.md)
- [Security Model](security.md)
- [FAQ](faq.md)
- [Changelog](changelog.md)
- [Core Abilities](abilities/core.md)
- [WooCommerce Abilities](abilities/woocommerce.md)
- [GeneratePress Abilities](abilities/generatepress.md)
- [ACF Abilities](abilities/acf.md)
- [Elementor Abilities](abilities/elementor.md)
- [Breakdance Abilities](abilities/breakdance.md)
- [CLI Abilities](abilities/cli.md)
