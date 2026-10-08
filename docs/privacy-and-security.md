# Privacy and security

Validation payloads are processed to perform the requested MCP tool call and are not intentionally persisted by the validation workflow.

Do not send API keys, passwords, payment data, secrets, access tokens, or unrelated sensitive data.

Hosted usage telemetry may record the tool name and explicit validation target. It does not intentionally log feed payloads or the rest of the tool arguments.

The hosted MCP tools enforce a 2 MB feed-content limit per request.
