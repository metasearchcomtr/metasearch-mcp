# Troubleshooting

This guide covers connection and validation problems for the public remote MCP server at `https://metasearch.com.tr/mcp`.

## The client cannot connect

1. Confirm the client supports remote Streamable HTTP MCP servers.
2. Use the exact endpoint `https://metasearch.com.tr/mcp`.
3. Do not add an API key or OAuth configuration: the public endpoint is currently unauthenticated.
4. Retry with the minimal client configuration from `docs/client-setup.md`.
5. If the client exposes transport logs, verify that it is attempting Streamable HTTP rather than stdio or legacy SSE.

## The client connects but tools are missing

Reconnect or restart the MCP client so it refreshes the tool list. The current public server exposes feed detection, normalization, validation, comparison and fix-suggestion tools. Tool names are documented in `docs/tools.md`.

If a directory or third-party catalog shows zero tools while direct MCP clients work, treat that as an indexing lag in the directory rather than as authoritative runtime state.

## A feed fails to parse

Supported static formats are JSON, XML, CSV, TSV and NDJSON. If automatic format detection is ambiguous, pass the format explicitly when the tool supports it.

Common causes:

- malformed JSON or XML,
- inconsistent CSV column counts,
- a delimiter mismatch,
- an empty payload,
- input larger than the validation limit.

## Validation output differs between targets

This is expected. Google Hotel Center, Wego and trivago use target-specific published-contract rules. Meta and Criteo checks are readiness checks, not certification. Generic hotel master-data validation is platform-independent.

Do not interpret a readiness score as platform approval.

## A required field seems undocumented

Open an issue with the target, rule code and the first-party source you believe contradicts the current implementation. The project intentionally avoids inventing undocumented mandatory fields.

## Sensitive feeds

Do not send credentials, secrets or private customer data as feed content. The service is designed not to intentionally persist submitted feed payloads, but public endpoints should still be treated as external services.

See `docs/privacy-and-security.md` for the current data-handling model.

## Reporting a problem

When opening an issue, include:

- MCP client and version,
- transport/connect error or tool name,
- target platform,
- input format,
- a minimal synthetic example that reproduces the issue,
- expected versus actual behavior.

Do not attach production feeds or credentials.
