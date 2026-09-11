# MPC ClearVibe WP

> **Beta — not for production use yet.** This is a public test build. Things may break, APIs may change. Feedback welcome via GitHub Issues.

A WordPress plugin that turns your site into an **MCP server** — letting AI agents like Claude, Devin, Codex, Grok, and Cursor manage your WordPress site securely through the Model Context Protocol.

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
- [Ability Reference](docs/abilities/) — full list of all 499+ abilities
- [Categories](docs/categories.md) — category list, which are enabled/disabled by default
- [Security Model](docs/security.md) — disabled categories, dangerous actions, audit log
- [FAQ](docs/faq.md) — common questions
- [Changelog](docs/changelog.md) — release history

## Supported AI Clients

Any MCP-compatible client works:

- **Claude Desktop / Claude Code** — Anthropic's AI assistant
- **Devin** — Cognition's autonomous software engineer
- **Codex** — OpenAI's coding agent
- **Grok** — xAI's assistant
- **Cursor** — AI-powered IDE
- **Any MCP-compatible CLI or tool**

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

## License

GNU General Public License v2.0 or later — compatible with the WordPress license.
