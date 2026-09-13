# Merchi MCP Plugin

<p align="center">
  <img src="https://merchi.co/mcp/icon.png" alt="Merchi Logo" width="128" height="128">
</p>

**Grok / Cursor marketplace plugin for the [Merchi](https://merchi.co) remote MCP server.**

Merchi is Australia's custom merchandise platform — connecting businesses with suppliers for promotional products, custom apparel, print-on-demand, and more. This plugin provides MCP (Model Context Protocol) access to the Merchi platform, enabling AI assistants to interact with your Merchi workspace.

> **Note:** This is **merchi.co** (Australia), not merchi.cl.

## MCP Server

| Property | Value |
|----------|-------|
| **URL** | `https://api.merchi.co/v6/mcp` |
| **Transport** | HTTP (Streamable HTTP) |
| **Authentication** | OAuth 2.0 (DCR + PKCE) |

No API keys or manual tokens required. Authentication is handled via OAuth flow on merchi.co — when you first use the plugin, you'll be prompted to authorize access through your browser.

## Installation

### Grok Marketplace (Recommended)

Once this plugin is listed in the xAI marketplace, install it directly:

```bash
grok plugin install merchi --trust
```

Or browse the marketplace:

```bash
grok plugin marketplace list
# Find and install "merchi"
```

### Direct Installation from GitHub

Install directly from this repository:

```bash
grok plugin install merchisdk/merchi_mcp --trust
```

> **Note:** This repository was renamed from `merchi-mcp` to `merchi_mcp`. The old GitHub URL (`github.com/merchisdk/merchi-mcp`) automatically redirects to the current location.

### Custom Connector / Manual Setup

For Grok, Cursor, or other MCP-compatible clients, add this configuration to your MCP settings:

**Grok** (`~/.grok/config.toml`):
```toml
[mcp_servers.merchi]
url = "https://api.merchi.co/v6/mcp"
```

**Cursor** (`.cursor/mcp.json` or `~/.cursor/mcp.json`):
```json
{
  "mcpServers": {
    "merchi": {
      "type": "http",
      "url": "https://api.merchi.co/v6/mcp"
    }
  }
}
```

**Claude Desktop** (`claude_desktop_config.json`):
```json
{
  "mcpServers": {
    "merchi": {
      "url": "https://api.merchi.co/v6/mcp"
    }
  }
}
```

## Authentication

This plugin uses **OAuth 2.0 with Dynamic Client Registration (DCR) and PKCE**. When you first invoke a Merchi tool:

1. Your client opens a browser window to `merchi.co`
2. Sign in or create a Merchi account
3. Authorize the requested permission scope:
   - **Read** — View products, orders, and catalog data
   - **Standard** — Read + create quotes and manage drafts
   - **Full** — Complete access including order management
4. The OAuth flow completes automatically

No manual token handling required. Tokens are stored securely by your MCP client.

## Available Tools

The Merchi MCP server provides tools for:

- **Product Catalog** — Search products, browse categories, view product details
- **Quoting** — Create and manage quotes for custom merchandise
- **Orders** — Track order status, view order history
- **Jobs** — Manage production jobs and workflows
- **Domains** — Access domain/storefront configuration
- **Files & Assets** — Upload and manage product images and files

Use `grok mcp doctor merchi` or check your client's MCP panel to see the full tool list after connecting.

## Resources

- **Documentation**: [https://merchi.co/mcp](https://merchi.co/mcp)
- **Merchi Platform**: [https://merchi.co](https://merchi.co)
- **API Reference**: [https://api.merchi.co/docs](https://api.merchi.co/docs)

## Icons

| Size | URL |
|------|-----|
| 256×256 | https://merchi.co/mcp/icon.png |
| 128×128 | https://merchi.co/mcp/icon-128.png |

## License

MIT — see [LICENSE](LICENSE).

---

<p align="center">
  <a href="https://merchi.co">merchi.co</a> · Australia's Custom Merchandise Platform
</p>
