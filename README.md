# MPC ClearVibe WP — WordPress MCP Server for AI Agents

> **Beta — not for production use yet.** This is a public test build. Things may break, APIs may change. Feedback welcome via GitHub Issues.

A WordPress plugin that turns your site into an **MCP server** — letting AI agents like Claude, Devin, Codex, Grok, and Cursor manage your WordPress site securely through the Model Context Protocol.

## What Is This?

MPC ClearVibe WP is a WordPress plugin that exposes your site to AI agents via the Model Context Protocol (MCP). Once installed, AI clients can read, create, modify, and delete content on your WordPress site — posts, pages, media, users, WooCommerce products, Elementor templates, and more.

It uses the official WordPress Abilities API and works with any MCP-compatible client: Claude Desktop, Claude Code, Devin, Codex, Grok, Cursor, and other AI agents.

## What It Does

Once installed, any MCP-compatible AI client can:

- **Read and write content** — posts, pages, custom post types, media, comments
- **Manage users and roles** — create users, assign capabilities, create scoped application passwords
- **Control plugins and themes** — list, activate, deactivate, install, update, delete
- **Run system operations** — transients, cron, cache, database queries, search-and-replace
- **Manage site configuration** — options, menus, widgets, taxonomies, permalink structure
- **Execute code snippets** — create, update, activate WPCode snippets (gated behind admin approval)
- **Export and audit** — WXR export, site health, GDPR data, audit logging
- **Manage WooCommerce** — products, orders, customers, coupons, shipping, tax, reports
- **Control page builders** — Elementor, Breakdance, GeneratePress, ACF

All through the standardized **Model Context Protocol** — the AI client discovers available tools, calls them with parameters, and gets structured responses back.

## Quick Start

1. **Download** the latest release ZIPs from the [Releases page](https://github.com/wonders4you/mpc-clearvibe-wp/releases)
2. **Install** in WordPress: Plugins → Add New → Upload Plugin → choose ZIP → Activate
3. **Connect** your AI agent — see the [MCP Setup Guide](docs/mcp-setup.md)

Full installation guide: [Installation](docs/installation.md)

## Add-Ons

The core plugin provides 181 abilities across 20 categories. Optional add-ons extend functionality for specific integrations:

| Add-on | Abilities | Categories | Requires |
|--------|-----------|-----------|----------|
| **Core** | 181 | 20 | WordPress 6.9+, PHP 8.0+ |
| **For-WooCommerce** | 113 | 2 | WooCommerce active |
| **For-GeneratePress** | 81 | 17 | GeneratePress / GenerateBlocks |
| **For-ACF** | 30 | 4 | Advanced Custom Fields |
| **For-Elementor** | 50 | 6 | Elementor |
| **For-Breakdance** | 44 | 6 | Breakdance |
| **CLI** | 2 | 1 | — |

Install only the add-ons you need. Each is a separate plugin — install and activate alongside the core.

## Requirements

- **WordPress 6.9** or later
- **PHP 8.0** or later
- **WordPress MCP Adapter** plugin (for MCP/HTTP communication with AI clients)
- HTTPS enabled (required for Application Passwords)

## Documentation

- [Installation Guide](docs/installation.md) — how to install core + add-ons
- [MCP Setup Guide](docs/mcp-setup.md) — connect your AI agent to WordPress
- [Agent Guide](docs/agent-guide.md) — copy-paste context for your AI agent (Claude, Codex, Cursor)
- [Ability Reference](docs/abilities/) — full list of all 499+ abilities
- [Categories](docs/categories.md) — category list, which are enabled/disabled by default
- [Security Model](docs/security.md) — disabled categories, dangerous actions, audit log
- [FAQ](docs/faq.md) — common questions
- [Changelog](docs/changelog.md) — release history

## Use Cases

- **Content automation** — "Claude, write and publish a blog post about X" — the AI agent creates the post directly in WordPress
- **WooCommerce management** — "List products with low stock and update prices" — the AI agent queries and updates WooCommerce
- **Site maintenance** — "Check for plugin updates and update them" — the AI agent manages plugins and themes
- **Bulk content editing** — "Find and replace old URLs across all posts" — the AI agent runs search-and-replace with dry-run preview
- **Page builder workflows** — "Update the Elementor header template" — the AI agent edits builder content through dedicated abilities
- **SEO optimization** — "Generate SEO meta descriptions for my latest 10 posts" — the AI agent reads posts and writes meta
- **Site audits** — "Show me what changed on my site this week" — the AI agent queries the audit log
- **Multisite management** — "Create a new subsite for the marketing team" — the AI agent manages multisite networks
- **Multiple bots with scoped access** — give each AI agent only the abilities it needs (see MCP Bots below)

## MCP Bots — Scoped Access for WordPress

MPC ClearVibe WP lets you create **scoped application passwords** so each AI agent (bot) gets access only to the abilities it needs. This is the recommended way to connect AI agents to your WordPress site — instead of using an unrestricted admin password.

### How It Works

1. Go to **Settings → ClearVibe AI → MCP bots tab**
2. Choose a WordPress user (the bot will act as this user — capability checks apply)
3. Enter a bot name (e.g. `content-writer`, `woo-manager`, `seo-bot`)
4. Select which categories and abilities the bot can use (checkboxes)
5. Click **Generate** — you get a scoped application password
6. Use that password in your AI client's MCP configuration

### What Scoping Does

- The bot can **only call abilities you selected** — all other abilities return a scope denial error
- The bot **still needs the WordPress capability** for each ability (e.g. `publish_posts`) — scoping is an additional restriction, not a replacement
- Passwords created in **Users → Profile** are **unrestricted** — they can call every enabled ability the user is allowed to use
- Passwords created via **MCP bots** are **scoped** — they can only call the abilities you checked

### Example: Two Bots with Different Access

**Shop Manager bot** (WooCommerce only):
- User: a Shop Manager account
- Abilities: `for-woo-list-products`, `for-woo-get-product`, `for-woo-update-product`, `for-woo-update-stock`
- Can: manage products and stock
- Cannot: edit posts, manage plugins, access customers

**Content Writer bot** (posts only):
- User: an Author account
- Abilities: `content-list-posts`, `content-get-post`, `content-create-post`, `content-update-post`
- Can: read and write posts
- Cannot: manage WooCommerce, plugins, users, system

Each bot gets its own login + password. Configure each in a separate MCP client entry (or use the same client with different credentials).

### Why Use Scoped Bots?

- **Least privilege** — if a bot password leaks, the attacker can only do what the bot can do
- **Separation of concerns** — a content bot can't accidentally delete plugins
- **Audit clarity** — the audit log shows which bot did what (by user and password)
- **Team access** — give different team members different bots with different scopes

### Creating a Bot via MCP

You can also create scoped passwords programmatically through the MCP protocol:

```json
{"ability_name":"mpc-clearvibe-wp/users-create-restricted-application-password","parameters":{"bot_name":"seo-bot","scopes":["content-list-posts","content-get-post","content-update-post"]}}
```

This returns a new application password with the specified scopes.

## Supported AI Clients

Any MCP-compatible client works:

- **Claude Desktop / Claude Code** — Anthropic's AI assistant
- **Devin** — Cognition's autonomous software engineer
- **Codex** — OpenAI's coding agent
- **Grok** — xAI's assistant
- **Cursor** — AI-powered IDE
- **Any MCP-compatible CLI or tool**

## FAQ

### Is this a WordPress plugin?

Yes. MPC ClearVibe WP is a WordPress plugin that exposes your site to AI agents via the Model Context Protocol. Install it like any other WordPress plugin.

### Do I need the MCP Adapter?

Yes. The [WordPress MCP Adapter](https://github.com/WordPress/mcp-adapter) is a separate plugin that bridges WordPress abilities to the MCP protocol. Download it from its repository.

### Can Claude manage my WordPress site?

Yes. Connect Claude Desktop or Claude Code to your WordPress site via MCP, and Claude can read, create, modify, and delete content — posts, pages, media, users, plugins, themes, and WooCommerce products.

### Can Cursor manage WordPress?

Yes. Cursor supports MCP servers. Configure the endpoint URL and Application Password in Cursor's MCP settings, and Cursor can manage your WordPress site.

### Does it work with WooCommerce?

Yes. The For-WooCommerce add-on adds 113 abilities for products, orders, coupons, shipping, tax, reports, customers, and more.

### Does it work with Elementor?

Yes. The For-Elementor add-on adds 50 abilities for templates, popups, kit settings, global colors, typography, and CSS cache.

### Does it work with Breakdance?

Yes. The For-Breakdance add-on adds 44 abilities for templates, builder content, global design, forms, and maintenance.

### Does it work with GeneratePress?

Yes. The For-GeneratePress add-on adds 85 abilities for theme settings, colors, typography, spacing, elements, GenerateBlocks, and custom CSS.

### Does it work with ACF?

Yes. The For-ACF add-on adds 30 abilities for field groups, fields, values, and options pages.

### Is it safe?

The plugin has multiple security layers: disabled-by-default dangerous categories, per-ability permission checks, dangerous-action confirmation, admin approval flow, audit logging, and secret redaction. However, no software is bug-free — always back up your site and test on staging first. See the [Security Model](docs/security.md).

### What WordPress version is required?

WordPress 6.9 or later, PHP 8.0 or later.

### Is it free?

Yes. The plugin is licensed under GPL v2 or later, compatible with the WordPress license.

## Disclaimer

This plugin exposes WordPress functionality to AI agents via the Model Context Protocol (MCP). AI agents can read, create, modify, and delete content on your WordPress site — including posts, pages, media, users, WooCommerce data, theme settings, and more.

**Use at your own risk.** While the plugin includes multiple security layers (disabled-by-default categories, dangerous-action confirmation, per-post write locks, audit logging, and read-back verification), no software is bug-free. Possible issues include but are not limited to:

- **Bugs** that may cause unintended changes to your content or data
- **AI agent errors** — the agent may misinterpret instructions and perform actions you did not intend
- **Compatibility issues** with specific WordPress versions, PHP versions, themes, plugins, or page builders
- **Security vulnerabilities** that may be discovered in the future

### Recommendations

1. **Back up your site** before installing and before enabling any write-capable category
2. **Start with read-only categories enabled** — enable write categories only when you trust the setup
3. **Keep dangerous categories disabled** (`plugins`, `system`, `snippets`, `system-cli`) unless you fully understand the risks
4. **Test on a staging site first**, not on your production site
5. **Review the audit log** regularly — the plugin logs all actions performed by AI agents
6. **Use application passwords or limited-scope API keys**, never admin credentials, for MCP authentication

### No Warranty

This software is provided "as is", without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose, and non-infringement. In no event shall the authors be liable for any claim, damages, or other liability arising from the use of or inability to use this software.

### Reporting Bugs

Found a bug? Please report it via [GitHub Issues](https://github.com/wonders4you/mpc-clearvibe-wp/issues). Include:

- Plugin version (core + add-ons)
- WordPress version
- PHP version
- Steps to reproduce
- Expected vs. actual behavior
- Error messages or audit log entries (redact sensitive data)

## Author

- **Tomasz Urban** — [wonders4you.com](https://wonders4you.com/)

## Source Code

Production source code is available at [mpc-clearvibe-wp-source](https://github.com/wonders4you/mpc-clearvibe-wp-source). Fork it, read it, submit PRs.

## License

GNU General Public License v2.0 or later — compatible with the WordPress license.
