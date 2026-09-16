# Changelog

## 0.9.0 (Pre-release)

- Security release — all seven findings from the live-fire penetration test fixed with regression coverage
- Internal `simple_press_mpc_*` options blocked from generic `options-*` abilities (read, write, list)
- MCP transport requires `manage_options` by default — low-privilege users can no longer open sessions or enumerate tools (filterable via `mpc_clearvibe_wp_transport_capability` / `mpc_clearvibe_wp_execute_capability`)
- Strict input schemas enforced (`additionalProperties: false` respected) — unknown fields rejected
- Approval ops bound to the requesting user
- Scoped MCP bot passwords confined to the `/mcp/` endpoint — no wp/v2 or XML-RPC access, no self-minting unscoped passwords
- ACF/Elementor IDOR hardening, Woo credential-overwrite fix, WPCodeBox 2 fatal fix
- Field-tested on Breakdance 3.x, GeneratePress and Divi 5 sites; For-Elementor add-on not yet site-tested
- 615 integration tests passing

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
