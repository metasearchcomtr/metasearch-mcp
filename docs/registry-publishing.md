# MCP Registry publishing

Canonical server name:

```text
tr.com.metasearch/metasearch-mcp
```

Remote endpoint:

```text
https://metasearch.com.tr/mcp
```

The namespace is authenticated through ownership of `metasearch.com.tr`.

## One-time domain verification setup

The repository uses DNS authentication for the official MCP Registry. The TXT record must be placed at the apex `metasearch.com.tr`.

On macOS, install OpenSSL 3 because the system LibreSSL does not support the recommended Ed25519 flow:

```bash
brew install openssl@3
```

Generate the key pair locally. Never commit `mcp-registry-key.pem`.

```bash
OPENSSL="$(brew --prefix openssl@3)/bin/openssl"
$OPENSSL genpkey -algorithm Ed25519 -out mcp-registry-key.pem
```

Generate the public key and print the DNS TXT record:

```bash
PUBLIC_KEY="$($OPENSSL pkey -in mcp-registry-key.pem -pubout -outform DER | tail -c 32 | base64)"
echo "metasearch.com.tr. IN TXT \"v=MCPv1; k=ed25519; p=${PUBLIC_KEY}\""
```

Add only the quoted TXT value to the apex/root record in the DNS provider:

```text
v=MCPv1; k=ed25519; p=PUBLIC_KEY
```

Then extract the private key as the 64-character hex value expected by `mcp-publisher`:

```bash
MCP_PRIVATE_KEY="$($OPENSSL pkey -in mcp-registry-key.pem -noout -text | grep -A3 'priv:' | tail -n +2 | tr -d ' :\n')"
echo "$MCP_PRIVATE_KEY"
```

Store that value as the GitHub Actions repository secret `MCP_PRIVATE_KEY` in `metasearchcomtr/metasearch-mcp`. Do not add the private key to DNS, source control, issues, logs, or documentation.

After DNS propagation, the manual `Publish MCP Registry` workflow performs:

1. install the current official `mcp-publisher`,
2. validate `server.json`,
3. authenticate with `mcp-publisher login dns --domain metasearch.com.tr`,
4. publish `server.json` to the official Registry.

## Validation

Every push to `main` runs the current official publisher validator:

```bash
mcp-publisher validate server.json
```

The MCP Registry is a preview service. Re-check the current official Registry documentation before changing authentication or publishing behavior.
