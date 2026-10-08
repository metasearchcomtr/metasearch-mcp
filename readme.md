# metasearch MCP

Public integration repository for the remote MCP server operated by [metasearch.com.tr](https://metasearch.com.tr).

- **Remote MCP:** `https://metasearch.com.tr/mcp`
- **Registry name:** `tr.com.metasearch/metasearch-mcp`
- **Website docs:** https://metasearch.com.tr/en/mcp
- **Hotel Feed Validator:** https://metasearch.com.tr/en/tools/hotel-feed-validator

## What it does

metasearch MCP gives AI agents structured tools for hotel/travel feed format detection, normalization, validation, platform requirement comparison, and deterministic remediation guidance.

| Target | Mode |
| --- | --- |
| Google Hotel Center | Published-contract validation |
| Wego Hotels | Published-contract validation |
| trivago FastConnect Hotel Data | Published-contract validation |
| Meta Catalog | Readiness/mapping pre-check |
| Criteo Catalog | Readiness/mapping pre-check |
| Generic Hotel Master Data | Platform-independent quality check |

Published-contract and readiness modes are deliberately kept separate. We do not invent undocumented mandatory fields.

## Quick start

### Claude Code

```bash
claude mcp add --transport http metasearch https://metasearch.com.tr/mcp
claude mcp list
```

### Cursor

`.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "metasearch": {
      "url": "https://metasearch.com.tr/mcp"
    }
  }
}
```

### VS Code / GitHub Copilot

`.vscode/mcp.json`:

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

## Tools

- `detect_feed_format`
- `normalize_hotel_feed`
- `validate_feed`
- `validate_google_hotel_center_list`
- `validate_wego_hotel_feed`
- `validate_trivago_hotel_data`
- `validate_meta_catalog`
- `validate_criteo_catalog`
- `validate_hotel_master_data`
- `compare_feed_readiness`
- `compare_platform_requirements`
- `suggest_feed_fixes`

See [docs/tools.md](docs/tools.md).

## Example prompts

```text
Validate this hotel feed for Google Hotel Center.
Group problems by issue code, show affected rows, and suggest the minimum fixes.
```

```text
Compare this feed for Google Hotel Center, Wego and trivago.
Separate shared canonical fields from platform-specific gaps.
```

More examples: [examples/prompts.md](examples/prompts.md).

## Privacy

The validation workflow intentionally does not persist submitted feed payloads. Usage telemetry records tool name and explicit target only; it does not intentionally record feed contents. Do not send credentials, payment data, secrets, or unrelated personal data.

See [docs/privacy-and-security.md](docs/privacy-and-security.md).

## Registry

The canonical Registry descriptor is [`server.json`](server.json). Publication uses domain ownership for `metasearch.com.tr`, represented by the reverse-DNS namespace `tr.com.metasearch`.

See [docs/registry-publishing.md](docs/registry-publishing.md).

## Companion CLI / Node SDK

```bash
npx @metasearch/feed-validator validate hotels.csv --target google-hotel-center
```

Repository: https://github.com/metasearchcomtr/feed-validator

## License

MIT
