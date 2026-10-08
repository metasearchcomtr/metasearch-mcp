# Contributing

Thanks for helping improve the metasearch MCP integration surface.

## Scope

This repository contains public MCP metadata, client examples, documentation, and registry integration assets. Runtime behavior is documented here but the production service is operated at `https://metasearch.com.tr/mcp`.

## Contribution guidelines

- Keep published-contract validation distinct from readiness or heuristic checks.
- Do not claim official platform certification unless a platform explicitly provides it.
- Keep examples minimal and reproducible.
- Do not commit private keys, credentials, customer feeds, or production payloads.
- Update `server.json` intentionally when registry metadata changes.

## Pull requests

Prefer focused changes with a short explanation of the user-facing impact. Documentation and client-configuration improvements are welcome.

## Security

For security-sensitive reports, avoid public issues containing secrets or private data. See [SECURITY.md](SECURITY.md).
