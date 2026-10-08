# metasearch MCP

[![Validate MCP metadata](https://github.com/metasearchcomtr/metasearch-mcp/actions/workflows/validate.yml/badge.svg)](https://github.com/metasearchcomtr/metasearch-mcp/actions/workflows/validate.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

Remote Model Context Protocol (MCP) server for **hotel and travel feed validation, normalization, readiness checks, and platform requirement comparison**.

Operated by [metasearch.com.tr](https://metasearch.com.tr) and published under the domain-owned MCP Registry identity:

```text
tr.com.metasearch/metasearch-mcp
```

Remote endpoint:

```text
https://metasearch.com.tr/mcp
```

> The server is independent and is not an official certification service for Google, Wego, trivago, Meta, or Criteo.

## What it does

The server gives AI agents deterministic tools for hotel-feed workflows:

- detect structured feed formats,
- normalize common hotel field aliases,
- validate hotel feeds,
- compare readiness across platforms,
- compare platform requirements,
- suggest remediation steps.

## Validation targets

| Target | Mode |
| --- | --- |
| Google Hotel Center | Published-contract validation |
| Wego Hotels | Published-contract validation |
| trivago hotel data | Published-contract validation |
| Meta Catalog | Readiness / mapping pre-check |
| Criteo Catalog | Readiness / mapping pre-check |
| Generic hotel master data | Platform-independent quality check |

Published-contract and readiness modes are deliberately kept separate. Undocumented mandatory fields are not invented.

## Connect

### Claude Code

```bash
claude mcp add --transport http metasearch https://metasearch.com.tr/mcp
claude mcp list
```

### Cursor

Add to `.cursor/mcp.json`:

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

Add to `.vscode/mcp.json`:

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

Additional setup examples live under [`examples/`](examples/).

## Available tools

| Tool | Purpose |
| --- | --- |
| `detect_feed_format` | Detect supported structured feed formats |
| `normalize_hotel_feed` | Normalize common hotel field aliases |
| `validate_feed` | Run target-aware validation |
| `validate_google_hotel_center_list` | Validate Google Hotel Center hotel-list data |
| `validate_wego_hotel_feed` | Validate Wego hotel-feed data |
| `validate_trivago_hotel_data` | Validate trivago hotel data |
| `validate_meta_catalog` | Run Meta catalog readiness checks |
| `validate_criteo_catalog` | Run Criteo catalog readiness checks |
| `validate_hotel_master_data` | Run generic hotel master-data quality checks |
| `compare_feed_readiness` | Compare feed readiness across targets |
| `compare_platform_requirements` | Compare target requirements |
| `suggest_feed_fixes` | Produce deterministic remediation guidance |

See [docs/tools.md](docs/tools.md) for details.

## Example prompts

Examples include:

- "Validate this hotel CSV for Google Hotel Center."
- "Compare this feed against Wego and trivago requirements."
- "Normalize this hotel dataset and show missing fields."
- "Explain how to fix the validation errors without inventing unsupported fields."

See [examples/prompts.md](examples/prompts.md).

## Privacy and data handling

The validation workflow is designed not to persist submitted feed payloads. Operational telemetry records tool name and explicit target only; it does not intentionally record feed contents.

Do not send credentials or secrets as feed content. See [docs/privacy-and-security.md](docs/privacy-and-security.md) and [SECURITY.md](SECURITY.md).

## Official MCP Registry

The canonical registry descriptor is [`server.json`](server.json).

Registry identity:

```text
tr.com.metasearch/metasearch-mcp
```

The namespace is authenticated using ownership of `metasearch.com.tr`.

## Companion CLI and Node.js SDK

For local development and CI pipelines, use [`@metasearch/feed-validator`](https://www.npmjs.com/package/@metasearch/feed-validator):

```bash
npx @metasearch/feed-validator validate hotels.csv --target google-hotel-center
```

Source: [metasearchcomtr/feed-validator](https://github.com/metasearchcomtr/feed-validator)

## Documentation

- [MCP documentation](https://metasearch.com.tr/en/mcp)
- [Hotel Feed Validator](https://metasearch.com.tr/en/tools/hotel-feed-validator)
- [Hotel feed requirements comparison](https://metasearch.com.tr/en/compare/hotel-feed-requirements)
- [Validate hotel feeds with MCP](https://metasearch.com.tr/en/resources/validate-hotel-feeds-with-mcp)

## Contributing

Issues and focused pull requests are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

MIT. See [LICENSE](LICENSE).
