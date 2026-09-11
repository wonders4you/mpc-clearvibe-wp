# MCP Setup Guide

## What is MCP?

The Model Context Protocol (MCP) is an open standard that lets AI clients (like Claude Desktop, Cursor, Devin) communicate with external tools and data sources. MPC ClearVibe WP exposes your WordPress site as an MCP server — the AI client discovers available tools (abilities), calls them with parameters, and gets structured responses back.

## How the Plugin Exposes MCP

The plugin registers WordPress abilities through the official WordPress Abilities API. The **MCP Adapter** plugin (separate download) exposes these abilities as MCP tools over HTTP.

| Setting | Value |
|---------|-------|
| Endpoint URL | `https://your-site.com/wp-json/mcp/mcp-adapter-default-server` |
| Transport | HTTP (Streamable) |
| Auth method | Basic (Application Password) |
| Auth header | `Authorization: Basic <base64(username:password)>` |

## Connecting Claude Desktop

Edit your `claude_desktop_config.json` (located at `~/Library/Application Support/Claude/claude_desktop_config.json` on macOS or `%APPDATA%\Claude\claude_desktop_config.json` on Windows):

```json
{
  "mcpServers": {
    "wordpress": {
      "url": "https://your-site.com/wp-json/mcp/mcp-adapter-default-server",
      "transport": "http",
      "headers": {
        "Authorization": "Basic <base64(username:application-password)>"
      }
    }
  }
}
```

Generate the Base64 token:

```bash
echo -n "admin:your-application-password" | base64
```

Replace `your-site.com` with your actual domain, `admin` with your WordPress username, and `your-application-password` with the application password you created.

Restart Claude Desktop after saving the config.

## Connecting Cursor

Add the same MCP server configuration to your Cursor settings (Settings → MCP):

```json
{
  "mcpServers": {
    "wordpress": {
      "url": "https://your-site.com/wp-json/mcp/mcp-adapter-default-server",
      "transport": "http",
      "headers": {
        "Authorization": "Basic <base64(username:application-password)>"
      }
    }
  }
}
```

## Connecting Other MCP Clients

Any MCP-compatible client can connect using the same endpoint URL and Authorization header. See your client's MCP configuration documentation.

## MCP Protocol Flow

1. **Initialize** — client sends `initialize` request, server responds with capabilities
2. **Notify** — client sends `notifications/initialized`
3. **Discover** — client calls `mcp-adapter-discover-abilities` to list all abilities
4. **Execute** — client calls `mcp-adapter-execute-ability` with ability name and parameters

## Verifying the Connection

After configuring your AI client, try asking it:

- "List the 5 most recent posts on my site"
- "Create a draft post titled 'Hello from AI'"
- "What plugins are installed?"
- "What's the site info?"

The AI client will call the appropriate MCP tools and return the results.

## Quick Test with curl

```bash
# Initialize session
SESSION=$(curl -s -D - -X POST "https://your-site.com/wp-json/mcp/mcp-adapter-default-server" \
  -u "admin:your-app-password" \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc":"2.0","id":1,"method":"initialize","params":{"protocolVersion":"2024-11-05","capabilities":{},"clientInfo":{"name":"test","version":"1.0"}}}' \
  | grep -i "mcp-session-id" | awk '{print $2}' | tr -d '\r')

# Send initialized notification
curl -s -X POST "https://your-site.com/wp-json/mcp/mcp-adapter-default-server" \
  -u "admin:your-app-password" \
  -H "Content-Type: application/json" \
  -H "MCP-Session-Id: $SESSION" \
  -d '{"jsonrpc":"2.0","method":"notifications/initialized"}'

# List recent posts
curl -s -X POST "https://your-site.com/wp-json/mcp/mcp-adapter-default-server" \
  -u "admin:your-app-password" \
  -H "Content-Type: application/json" \
  -H "MCP-Session-Id: $SESSION" \
  -d '{"jsonrpc":"2.0","id":2,"method":"tools/call","params":{"name":"mcp-adapter-execute-ability","arguments":{"ability_name":"mpc-clearvibe-wp/content-list-posts","parameters":{"per_page":5}}}}'
```

## Security Considerations

- **Start with read-only categories** — content read, media read, users read. Enable write categories only when you trust the setup.
- **Use scoped application passwords** — the `users-create-restricted-application-password` ability lets you limit the AI client to specific categories.
- **Keep dangerous categories disabled** — `plugins`, `system`, `snippets`, `system-cli` should stay off unless you fully understand the risks.
- **Review the audit log** — check **Settings → ClearVibe AI → Audit log** regularly to see what the AI client has done.

See the [Security Model](security.md) documentation for full details.
