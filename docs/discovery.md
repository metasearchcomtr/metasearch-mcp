# Discovery and directory metadata

Canonical metadata for MCP registries, directories and curated lists.

## Identity

- Name: `metasearch MCP`
- Registry ID: `tr.com.metasearch/metasearch-mcp`
- Remote endpoint: `https://metasearch.com.tr/mcp`
- Transport: Streamable HTTP
- Authentication: none for the current public endpoint
- Repository: `https://github.com/metasearchcomtr/metasearch-mcp`
- Documentation: `https://metasearch.com.tr/en/mcp`
- License: MIT

## Short description

Hotel and travel feed validation, normalization, readiness checks and platform requirement comparison for AI agents.

## Long description

metasearch MCP lets MCP-compatible AI clients detect structured hotel-feed formats, normalize common field aliases, validate feeds against supported target rule packs, compare platform requirements and readiness, and generate deterministic remediation guidance. Google Hotel Center, Wego and trivago use published-contract validation; Meta and Criteo are explicitly labeled readiness checks.

## Categories

Prefer the closest available categories in this order:

1. Travel / Hospitality
2. Developer Tools
3. Data Validation / Data Quality
4. Data & Analytics

## Keywords

`hotel`, `travel`, `metasearch`, `feed-validation`, `data-quality`, `google-hotel-center`, `wego`, `trivago`, `mcp`, `developer-tools`

## Privacy statement

The public endpoint is designed not to intentionally persist submitted feed payloads. Operational telemetry records tool-level metadata rather than raw feed contents. Users should not submit credentials, secrets or private customer data.

## Claims to avoid

Do not describe the server as:

- an official validator for Google, Wego, trivago, Meta or Criteo,
- a certification service,
- an authenticated/private endpoint,
- a live OTA price crawler.

## Canonical setup snippets

### Claude Code

```bash
claude mcp add --transport http metasearch https://metasearch.com.tr/mcp
```

### Cursor

```json
{
  "mcpServers": {
    "metasearch": {
      "url": "https://metasearch.com.tr/mcp"
    }
  }
}
```

### VS Code

```json
{
  "servers": {
    "metasearch": {
      "type": "http",
      "url": "https://metasearch.com.tr/mcp"
    }
  }
}
```

Use this document as the source of truth when submitting the server to third-party directories so descriptions stay consistent across listings.
