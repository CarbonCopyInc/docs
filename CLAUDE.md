# Carbon Copy API Documentation

Mintlify-powered documentation site for the Carbon Copy public API.

## Build & Preview

```bash
npx mintlify dev      # Local preview at localhost:3000
```

## Structure

```
docs.json                    # Mintlify config (nav, colors, branding)
index.mdx                   # Introduction
quickstart.mdx               # Getting started guide
authentication.mdx           # Auth methods (API key + Privy JWT)
rate-limits.mdx              # Rate limiting details
errors.mdx                   # Error codes and formats
pagination.mdx               # Cursor-based pagination guide
api-reference/
  introduction.mdx           # API reference intro
  openapi.json               # OpenAPI 3.1 spec (SOURCE OF TRUTH for docs)
```

## Public API Ecosystem

Carbon Copy has three repos that form the public API surface:

| Repo | Purpose | Deploys to |
|---|---|---|
| `CarbonCopyInc/habakkuk` | App + Convex backend + REST API (source of truth) | Vercel + Convex |
| `CarbonCopyInc/docs` (this repo) | Mintlify API documentation | Mintlify |
| `CarbonCopyInc/carboncopy-mcp` | MCP server (thin wrapper over REST API) | npm |

### Sync Rules

- **`habakkuk` is the source of truth** for API behavior. This repo documents it.
- `openapi.json` must be updated whenever API endpoints change in habakkuk.
- Mintlify auto-generates the interactive API playground from `openapi.json`.
- Guide pages (authentication, errors, etc.) only need updating for conceptual changes.

## Conventions

- Use MDX for all content pages
- Keep `openapi.json` as a single file (no splitting)
- Brand colors: primary navy `#1a3a5c`, accent green `#18E299`, dark green `#0C8C5E`
