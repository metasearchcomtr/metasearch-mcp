# Changelog

All notable public changes to metasearch MCP are documented here.

The server version is also published in `server.json` and in the official MCP Registry metadata.

## 1.1.0 — 2026-10-08

### Added

- Public Streamable HTTP endpoint at `https://metasearch.com.tr/mcp`.
- Domain-owned registry identity `tr.com.metasearch/metasearch-mcp`.
- Feed format detection for JSON, XML, CSV, TSV and NDJSON.
- Canonical hotel-feed normalization.
- Target-aware validation for Google Hotel Center, Wego and trivago published contracts.
- Readiness checks for Meta Catalog and Criteo Catalog.
- Generic hotel master-data quality checks.
- Cross-platform feed-readiness and requirement comparison.
- Deterministic remediation suggestions.
- MCP resources for platform requirements and canonical hotel schema.
- Claude Code, Cursor and VS Code connection examples.
- Privacy-safe operational telemetry that does not intentionally persist submitted feed payloads.

### Discovery

- Official MCP Registry-compatible `server.json`.
- Domain ownership verification for the `tr.com.metasearch` namespace.
- Public discovery surfaces on metasearch.com.tr.

## Versioning

The public remote server follows semantic versioning for externally visible MCP contract changes. Tool additions, removals, renamed arguments or materially changed output semantics should be reflected in this changelog before a registry version is published.
