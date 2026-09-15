# Changelog

## 0.8.1 (Pre-release)

- Refactor: For-Woo provider split into four domain classes (products, orders, customers, store)
- Refactor: snippets provider split into per-engine classes (WPCode, Code Snippets, WPCodeBox 2)
- No functional changes

## 0.8.0 (Pre-release)

- For-Breakdance add-on: 48 abilities — new `bd-list-nodes` (flat node list) and `bd-convert-element` (whitelisted element conversion with dry-run reports)
- Breakdance tree access extracted into a dedicated repository; Elementor `_elementor_data` layer extracted the same way
- Safe Breakdance tree writes through the official API path with backups, dry-run and cache regeneration
- Shared admin tabs: add-ons register sections via the `mpc_clearvibe_wp_admin_tabs` filter
- Security: deterministic confirmation gate, audit log redacts app-password UUIDs, backup/restore hardening
- Fix: empty-object input schemas no longer crash during registration; content-upload-media relative paths; Breakdance 3.x detection
- Docker: mcp-adapter + WPCode Lite auto-installed, `docker/plugin-zips/` drop-in for premium plugins, `docker/mcp-call.sh` CLI bridge

## 0.7.1 (Pre-release)

- MCP bots: scoped application passwords — create per-bot passwords with selected abilities (Settings → ClearVibe AI → MCP bots tab)
- Snippets engine: multi-engine support (WPCode, Code Snippets, WPCodeBox 2)
- Translations: updated pl_PL, es_ES, fr_FR for all 7 plugins (1375 msgids, 45 new strings)
- Security: plugin/theme mutation abilities (activate, deactivate, update, install) now require dangerous-action confirmation
- Ability normalization: MCP annotations (readonly/destructive/idempotent) copied to top-level meta
- Cron hardening: malformed schedule/args types handled safely
- Tests: new AbilityTestCase base class, updated integration tests
- Docs: agent-guide.md, MCP bots section in README, SEO optimization

## 0.7.0 (Pre-release)

- First public test build
- Core plugin: 181 abilities, 20 categories
- Add-ons: WooCommerce (113), GeneratePress (81), ACF (30), Elementor (50), Breakdance (44), CLI (2)
- Total: 499+ abilities across 55 categories
- Security: disabled-by-default dangerous categories, dangerous-action confirmation, out-of-band admin approval, per-post write locks, audit logging, secret redaction, scoped application passwords
- MCP: HTTP transport, Application Password authentication, auto-generated annotations (readonly/destructive/idempotent)
- Translations: English, Polish (pl_PL), Spanish (es_ES), French (fr_FR)

---

> This is a pre-release for testing. Things may break, APIs may change. See the [disclaimer](../README.md#disclaimer).
