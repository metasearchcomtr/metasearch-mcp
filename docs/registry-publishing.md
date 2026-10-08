# MCP Registry publishing

Canonical server name:

```text
tr.com.metasearch/metasearch-mcp
```

The namespace is authenticated through ownership of `metasearch.com.tr`.

Before publishing:

1. validate `server.json` with the current `mcp-publisher`,
2. confirm `https://metasearch.com.tr/mcp` is healthy,
3. confirm the website and public repo describe the same capabilities,
4. intentionally bump the version.

The official MCP Registry is a preview service, so re-check its current publishing documentation before every material workflow change.
