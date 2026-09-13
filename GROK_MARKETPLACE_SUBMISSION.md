# Grok Marketplace Submission Guide

This document contains the catalog entry for submitting the Merchi MCP plugin to the [xAI Plugin Marketplace](https://github.com/xai-org/plugin-marketplace).

## Submission Process

1. Fork [xai-org/plugin-marketplace](https://github.com/xai-org/plugin-marketplace)
2. Add the catalog entry below to `.grok-plugin/marketplace.json`
3. Regenerate the plugin index: `python3 scripts/generate-plugin-index.py`
4. Validate: `python3 scripts/validate-catalog.py`
5. Open a PR

## Catalog Entry

Add this entry to the `plugins` array in `.grok-plugin/marketplace.json`:

```json
{
  "name": "merchi",
  "description": "MCP connector for Merchi — Australia's custom merchandise platform. Access product catalogs, quotes, orders, and workflows via natural language.",
  "category": "ecommerce",
  "source": {
    "source": "url",
    "url": "https://github.com/merchisdk/merchi_mcp.git",
    "sha": "0000000000000000000000000000000000000000"
  },
  "homepage": "https://merchi.co/mcp",
  "keywords": [
    "merchi",
    "merchandise",
    "ecommerce",
    "australia",
    "custom-products",
    "promotional-products",
    "print-on-demand"
  ],
  "domains": [
    "merchi.co",
    "api.merchi.co"
  ]
}
```

## Important: Pin the Commit SHA

Before submitting to the marketplace, replace the placeholder SHA with an actual public commit from this repository:

```bash
# Get the latest commit SHA
git rev-parse HEAD
```

Example with pinned SHA:
```json
"sha": "a1b2c3d4e5f6g7h8i9j0k1l2m3n4o5p6q7r8s9t0"
```

The SHA must be:
- A full 40-character lowercase hexadecimal string
- A public, reachable commit on the `main` branch
- The commit containing the final reviewed plugin files

## Source Repository

| Field | Value |
|-------|-------|
| Owner | `merchisdk` |
| Repository | `merchi_mcp` |
| URL | https://github.com/merchisdk/merchi_mcp |
| Branch | `main` |

## Plugin Metadata

| Field | Value |
|-------|-------|
| Name | `merchi` |
| Display Name | Merchi |
| Category | `ecommerce` |
| Homepage | https://merchi.co/mcp |
| Icon (256px) | https://merchi.co/mcp/icon.png |
| Icon (128px) | https://merchi.co/mcp/icon-128.png |

## MCP Server Details

| Property | Value |
|----------|-------|
| URL | `https://api.merchi.co/v6/mcp` |
| Transport | HTTP (Streamable HTTP) |
| Authentication | OAuth 2.0 (DCR + PKCE) |

No API keys, environment tokens, or manual setup required. Users authenticate via OAuth flow on merchi.co.

## Checklist

Before submitting:

- [ ] Plugin installs successfully: `grok plugin install merchisdk/merchi_mcp --trust`
- [ ] MCP server connects: `grok mcp doctor merchi`
- [ ] OAuth flow completes successfully
- [ ] Commit SHA is pinned to a public commit
- [ ] All JSON files are valid
- [ ] `plugin-index.json` regenerated after adding entry

## Contact

For questions about this plugin:
- Website: https://merchi.co
- Documentation: https://merchi.co/mcp
