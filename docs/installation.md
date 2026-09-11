# Installation Guide

## Before You Begin

Make sure your site meets the requirements:

- **WordPress 6.9** or later
- **PHP 8.0** or later
- **HTTPS** enabled (required for Application Passwords)
- **WordPress MCP Adapter** plugin (separate download — see below)

## Step 1: Install the Core Plugin

1. Download the latest `mpc-clearvibe-wp-<version>.zip` from the [Releases page](https://github.com/wonders4you/mpc-clearvibe-wp/releases).
2. In WordPress admin: **Plugins → Add New → Upload Plugin**.
3. Choose the ZIP file and click **Install Now**.
4. Click **Activate**.

## Step 2: Install the MCP Adapter

The MCP Adapter is the bridge between WordPress abilities and the MCP protocol. Without it, the abilities are registered but not exposed to AI clients.

Download from the [WordPress MCP Adapter repository](https://github.com/WordPress/mcp-adapter) and upload via **Plugins → Add New → Upload Plugin**.

Alternatively, via WP-CLI:

```bash
wp plugin install https://github.com/WordPress/mcp-adapter/releases/latest/download/mcp-adapter.zip --activate
```

## Step 3: Install Add-Ons (Optional)

Download the add-on ZIPs you need from the [Releases page](https://github.com/wonders4you/mpc-clearvibe-wp/releases). Install each the same way as the core plugin.

Install order: **core first**, then add-ons.

### Add-on dependencies

| Add-on | Requires |
|--------|----------|
| For-WooCommerce | WooCommerce plugin active |
| For-GeneratePress | GeneratePress theme or GenerateBlocks plugin |
| For-ACF | Advanced Custom Fields plugin active |
| For-Elementor | Elementor plugin active |
| For-Breakdance | Breakdance plugin active |
| CLI | Core plugin only |

## Step 4: Create an Application Password

MCP clients authenticate via WordPress Application Passwords (not cookies).

1. In WordPress admin: **Users → Profile → Application Passwords**.
2. Enter a name (e.g. "Claude Desktop" or "Devin").
3. Click **Add New Application Password**.
4. **Save the generated password** — you won't see it again.

> **Tip:** For scoped access (limit the AI client to specific categories), use the `mpc-clearvibe-wp/users-create-restricted-application-password` ability instead. Passwords created on the profile screen are unrestricted.

## Step 5: Configure Your AI Client

See the [MCP Setup Guide](mcp-setup.md) for step-by-step instructions for Claude Desktop, Cursor, and other MCP clients.

## Step 6: Enable Categories

After installation, 17 of 20 core categories are enabled by default. Only the three most dangerous categories are disabled:

| Category | Default | Why |
|----------|---------|-----|
| Content, Media, Comments, Users, Meta, Site | **Enabled** | Core content management |
| Menus, Widgets, Options, Taxonomy, Blocks | **Enabled** | Site configuration |
| Themes, Multisite, Tools, Resources, Prompts | **Enabled** | Theme, network, export, read-only resources |
| **Plugins** | **Disabled** | Can install/delete code |
| **System** | **Disabled** | System operations, DB queries, updates |
| **Snippets** | **Disabled** | Code execution (WPCode) |

Add-on categories (WooCommerce, GeneratePress, ACF, Elementor, Breakdance, CLI) are also disabled by default.

To enable/disable categories: **Settings → ClearVibe AI → Abilities tab**.

## Updating

To update to a new version:

1. Download the new ZIP from the [Releases page](https://github.com/wonders4you/mpc-clearvibe-wp/releases).
2. In WordPress admin: **Plugins → Add New → Upload Plugin**.
3. Choose the new ZIP and click **Install Now**.
4. Click **Replace current with uploaded**.

Your settings (enabled categories, audit log, etc.) are preserved across updates.

## Troubleshooting

### "Application Passwords not available"

WordPress requires HTTPS for application passwords. For local HTTP development, add this to a must-use plugin:

```php
add_filter( 'wp_is_application_passwords_available', '__return_true' );
```

### "MCP Adapter not found"

Make sure the MCP Adapter plugin is installed and activated. The core plugin registers abilities, but the MCP Adapter exposes them to AI clients.

### "Ability is disabled"

When an AI client tries to use a disabled ability, it gets a message telling you which category to enable. Go to **Settings → ClearVibe AI → Abilities tab** and enable the category.

### Add-on not registering abilities

Make sure the add-on's dependency is active (e.g. WooCommerce for For-WooCommerce, Elementor for For-Elementor). The add-on will silently skip registration if its dependency is missing.
