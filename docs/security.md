# Security Model

## Overview

MPC ClearVibe WP gives AI agents the ability to read and modify your WordPress site. To keep this safe, the plugin implements multiple layers of security:

1. Disabled-by-default categories
2. Per-ability permission checks (least-privilege WordPress capabilities)
3. Dangerous-action confirmation
4. Out-of-band admin approval flow
5. Per-post write locks
6. Content write preflight and builder guard
7. Read-back verification
8. Audit logging
9. Secret redaction
10. Scoped application passwords

## Disabled-by-Default Categories

Categories that can install code, execute code, or perform dangerous system operations start disabled:

- **Plugins** — install/delete code
- **System** — system operations, DB queries, core updates
- **Snippets** — code execution
- **WooCommerce** — store management
- **WooCommerce customers** — personal data (GDPR)
- **Breakdance** (all 6 categories) — builder content and global design
- **CLI** — shell command execution

When an AI client tries to use a disabled ability, it gets a helpful message:

> The ability "mpc-clearvibe-wp/plugins-list" is disabled because its category "Plugins" is turned off. Enable the "Plugins" category in the ClearVibe AI admin panel (Settings → ClearVibe AI) to use this ability.

This way the AI client knows exactly what to ask the site admin to enable.

## Per-Ability Permission Checks

Every ability has a `permission_callback` that checks the least-privilege WordPress capability for the action. For example:

- `content-list-posts` requires `edit_posts`
- `content-create-post` requires `publish_posts`
- `content-delete-post` requires `delete_post` (per post)
- `plugins-activate` requires `activate_plugins`
- `system-db-query` requires `manage_options`

The permission callback runs before the execute callback. If the user lacks the capability, the ability returns a permission error.

## Dangerous-Action Confirmation

Certain abilities are marked as "dangerous" and require explicit confirmation before executing. These include:

- Plugin operations: upload, delete, switch
- Theme operations: delete, update
- User operations: delete, create/revoke application passwords
- Options: update, delete, add, patch
- System: search-replace, update core, update db, set permalink, run cron
- Tools: export
- Multisite: delete/archive site
- Snippets: create, update, delete, activate
- Taxonomy: create, delete
- CLI: run command

### How confirmation works

1. The AI client calls a dangerous ability without a confirmation token.
2. The plugin returns an error: `simple_press_mpc_confirmation_required` with instructions.
3. The AI client retries with `confirm_dangerous_action` set to the ability name (e.g. `"mpc-clearvibe-wp/plugins-delete"`).
4. The ability executes.

### Dry-run bypass

If the ability supports preview (e.g. `system-search-replace`) and the input includes `dry_run=true`, no confirmation is required — the ability runs in preview mode without writing.

## Out-of-Band Admin Approval

For maximum safety, you can require admin approval for dangerous operations:

1. The AI client calls a dangerous ability with `request_approval=true`.
2. The plugin creates a pending operation record and returns:
   - `op_id` (e.g. `op_abc123...`)
   - A dry-run preview (if supported)
   - Expiry timestamp (15 minutes)
   - A link to the admin approval page
3. An admin reviews the pending operation in **Settings → ClearVibe AI → Settings tab** and approves or denies it.
4. The AI client retries with `confirm_dangerous_action` set to the op id (`op_abc123...`).
5. The plugin verifies:
   - The op exists and hasn't expired
   - The HMAC integrity proof is valid (detects tampering)
   - The ability name matches
   - The op was approved
   - The input hasn't changed since approval (input drift check)
   - The site state hasn't changed since the preview (state drift check, if applicable)
6. The op is consumed (single-use) and the ability executes.

### Mandatory approval mode

You can enable **"Require admin approval for dangerous abilities"** in Settings → ClearVibe AI → Settings. When enabled, the plain ability-name confirmation token is rejected — an approved op id is always required.

## Per-Post Write Locks

When an AI client writes to a post, the plugin acquires a short-lived lock (30 seconds by default) on that post. If another client tries to write to the same post while the lock is held, it gets a `simple_press_mpc_post_locked` error. This prevents concurrent edits from corrupting content.

## Content Write Preflight and Builder Guard

Before writing to a post that has page builder content (Elementor, GenerateBlocks, Beaver Builder, etc.), the plugin checks:

- **Builder content guard** — if the post has builder meta, the plugin blocks generic content writes and tells the caller to use `full_rebuild` mode or edit through the builder's add-on abilities.
- **Design markup preservation** — compares design markers (layout blocks, GenerateBlocks) in old vs new content. If markers would be lost, the write is blocked unless the caller explicitly opts in.
- **Content preflight** — runs a filter (`mpc_clearvibe_wp_content_preflight`) that allows site policy adapters to block writes.

## Read-Back Verification

After writing to a post, the plugin verifies the persisted status matches what was requested. If the post is in a different status (or missing entirely), it returns an error. This catches silent failures where WordPress changes the status during save.

## Audit Logging

Every ability execution is logged — both successes and failures, including permission denials. The audit log records:

- Ability name
- User ID
- Success/failure
- Error code (if failed)
- Redacted input context (secrets replaced with `***`, long values truncated)
- Timestamp

### Viewing the audit log

Go to **Settings → ClearVibe AI → Audit log tab**. The log shows recent executions with pagination (20 at a time). You can also query it via the `tools-list-audit-log` ability.

### Retention

Default retention is 30 days. You can change this in Settings → ClearVibe AI → Settings. Set to 0 to keep indefinitely. Old entries are pruned daily via WP-Cron.

## Secret Redaction

The plugin redacts or blocks access to secrets:

- **Options** — `options-get`, `options-list`, and `resources-option` block or redact values matching patterns like `auth_key`, `db_password`, `api_key`, `access_token`, `application_password`.
- **Transients** — secret-like names are blocked for get/set/delete.
- **Debug log** — secret values in `system-debug-log` are redacted.
- **wp-config.php** — `system-get-config` redacts all secret and credential constants (DB_PASSWORD, AUTH_KEY, salts, FTP_PASS, etc.).
- **User meta** — credential keys (`session_tokens`, `_application_passwords`) are denied. Secret patterns (`/secret/`, `/totp/`, `/2fa/`, `/api_key/`, `/password/`) are withheld on read.
- **WooCommerce gateway settings** — sensitive keys are redacted on read, blocked on write.

## Scoped Application Passwords

You can create application passwords that are scoped to specific categories or abilities:

- Use the `users-create-restricted-application-password` ability.
- Specify scopes (e.g. `content`, `media`, or specific ability names).
- The plugin stores scopes in the password's metadata and enforces them on every MCP call.
- Passwords created in the WordPress profile screen are unrestricted.

## CLI Add-On Security

The CLI add-on allows whitelisted shell command execution:

- The allowlist is **code-only** — it is a PHP filter, never a database option. An options-update would allow RCE escalation, so this is by design.
- Commands are executed via `proc_open` in array form (no shell metacharacter interpretation).
- `system-cli-run` is a dangerous ability requiring out-of-band approval.

## Async Operations

Long-running abilities (`tools-export`, `system-search-replace`, `system-update-core`, `system-update-db`, `system-verify-checksums`) accept `run_async=true`:

1. The ability is enqueued as a WP-Cron job.
2. The caller gets a `job_id` immediately.
3. The job runs in the background with the original user's capabilities.
4. Poll status via `system-job-status` or `system-job-list`.

## MCP Annotations

The plugin auto-generates MCP annotations from ability names:

- **readonly** — abilities starting with `get`, `list`, `is`, `has`, `count`, `search`, `audit`, `export`
- **destructive** — abilities starting with `delete`, `clear`, `reset`, `purge`, `remove`, `destroy`, `drop`, `truncate`
- **idempotent** — abilities starting with `upsert`, `update`, `regenerate`, `activate`, `import`, `set`

These annotations help AI clients understand the nature of each tool before calling it.

---

> **Disclaimer:** This plugin gives AI agents write access to your WordPress site. No software is bug-free. Always back up before enabling write categories, test on staging first, and start with read-only categories enabled. See the [full disclaimer](../README.md#disclaimer).
