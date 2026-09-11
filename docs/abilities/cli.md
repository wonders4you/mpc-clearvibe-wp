# CLI Abilities (2)

The CLI add-on adds 2 abilities in 1 category. All abilities are prefixed with `mpc-clearvibe-wp/system-cli-`. The category is **disabled by default**.

> **Security Warning:** This add-on allows the MCP client to run whitelisted shell commands. This is equivalent to giving the client limited server shell access. Enable only if you accept the security risk.

## Categories

| Category | Count | Default | Description |
|----------|-------|---------|-------------|
| `system-cli` | 2 | **Disabled** | Whitelisted command-line execution |

## system-cli (2 abilities — disabled by default)

| Ability | Description | R/W | Dangerous |
|---------|-------------|-----|-----------|
| `system-cli-list-commands` | List whitelisted commands that can be executed | Read | No |
| `system-cli-run` | Execute a whitelisted command (output capped, shell metacharacters rejected) | Write | **Yes** — requires out-of-band approval |

## Security

- The allowlist is **code-only** — it is a PHP filter, never a database option. An options-update would allow RCE escalation, so this is by design.
- Commands are executed via `proc_open` in array form (no shell metacharacter interpretation).
- `system-cli-run` is a dangerous ability requiring explicit confirmation or out-of-band admin approval.
