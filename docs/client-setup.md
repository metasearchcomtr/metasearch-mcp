# Client setup

## Claude Code

```bash
claude mcp add --transport http metasearch https://metasearch.com.tr/mcp
claude mcp list
```

## Cursor

Project configuration (`.cursor/mcp.json`):

```json
{
  "mcpServers": {
    "metasearch": {
      "url": "https://metasearch.com.tr/mcp"
    }
  }
}
```

## VS Code / GitHub Copilot

Workspace configuration (`.vscode/mcp.json`):

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

The endpoint is currently public and unauthenticated. If authentication is introduced later, this guide will be updated together with protected-resource discovery metadata.
