# FAQ

## General

### What is MPC ClearVibe WP?

A WordPress plugin that turns your site into an MCP (Model Context Protocol) server. It lets AI agents like Claude Desktop, Devin, Cursor, and Codex manage your WordPress site — read and write content, manage users, control plugins, run system operations, and more.

### Do I need the MCP Adapter?

Yes. The MCP Adapter is a separate plugin that bridges WordPress abilities to the MCP protocol. Without it, abilities are registered but not exposed to AI clients. Download it from [WordPress/mcp-adapter](https://github.com/WordPress/mcp-adapter).

### Is it safe?

The plugin has multiple security layers: disabled-by-default dangerous categories, per-ability permission checks, dangerous-action confirmation, admin approval flow, audit logging, and secret redaction. However, no software is bug-free — always back up your site and test on staging first. See the [Security Model](security.md).

### Can I limit what the AI agent can do?

Yes. Use the **MCP bots** tab in **Settings → ClearVibe AI** to create a scoped application password that limits the AI client to specific categories or abilities. You can also enable/disable categories and individual abilities in the Abilities tab. See [MCP Bots](README.md#mcp-bots--scoped-access-for-wordpress) for details.

### What are MCP bots?

MCP bots are scoped application passwords created in **Settings → ClearVibe AI → MCP bots tab**. Each bot gets access only to the abilities you select — for example, a "content writer" bot that can only create and edit posts, or a "shop manager" bot that can only manage WooCommerce products. This is safer than using an unrestricted admin password.

## Compatibility

### Which WordPress versions are supported?

WordPress 6.9 or later.

### Which PHP versions are supported?

PHP 8.0 or later.

### Does it work with multisite?

Yes. The core plugin includes a `multisite` category with 9 abilities for managing network sites.

### Which page builders are supported?

- **Gutenberg / block themes** — built into the core plugin (25 abilities)
- **Elementor** — For-Elementor add-on (50 abilities)
- **Breakdance** — For-Breakdance add-on (44 abilities)
- **GeneratePress / GenerateBlocks** — For-GeneratePress add-on (81 abilities)

### Does it work with WooCommerce?

Yes. The For-WooCommerce add-on adds 113 abilities for products, orders, customers, coupons, shipping, tax, reports, and more.

### Does it work with ACF?

Yes. The For-ACF add-on adds 30 abilities for field groups, fields, values, and options pages.

## Troubleshooting

### The AI client says "ability is disabled"

Go to **Settings → ClearVibe AI → Abilities tab** and enable the category the error message mentions.

### The AI client can't connect

- Make sure the MCP Adapter plugin is installed and activated.
- Make sure you're using HTTPS (required for Application Passwords).
- Verify the endpoint URL: `https://your-site.com/wp-json/mcp/mcp-adapter-default-server`
- Verify the Authorization header is correct: `Basic <base64(username:application-password)>`.

### Application Passwords not available

WordPress requires HTTPS for application passwords. For local HTTP development, add this to a must-use plugin:

```php
add_filter( 'wp_is_application_passwords_available', '__return_true' );
```

### An add-on isn't registering abilities

Make sure the add-on's dependency is active:
- For-WooCommerce requires WooCommerce
- For-Elementor requires Elementor
- For-Breakdance requires Breakdance
- For-ACF requires Advanced Custom Fields
- For-GeneratePress works best with GeneratePress theme / GenerateBlocks

### How do I see what the AI client has done?

Go to **Settings → ClearVibe AI → Audit log tab**. Every ability execution is logged with the ability name, user, result, and timestamp.

## Performance

### Does the plugin slow down my site?

No. The plugin only loads on admin pages and REST/MCP requests. It does not add scripts or styles to the front end. Ability registration happens on `plugins_loaded` and adds no overhead to normal page loads.

### Can I disable the audit log?

Yes. Go to **Settings → ClearVibe AI → Settings tab** and toggle audit logging off. You can also set retention to 0 to keep logs indefinitely, or reduce it to a few days.

## Reporting Bugs

Found a bug? Please report it via [GitHub Issues](https://github.com/wonders4you/mpc-clearvibe-wp/issues). Include:

- Plugin version (core + add-ons)
- WordPress version
- PHP version
- Steps to reproduce
- Expected vs. actual behavior
- Error messages or audit log entries (redact sensitive data)
