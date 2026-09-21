# Setup

PieterPost MCP is a remote MCP server available at:

```text
https://pieterpost.com/mcp/setup/
```

Use that URL when adding PieterPost as a custom MCP connector in a compatible client.

## Claude

1. Open Claude settings.
2. Go to Connections.
3. Choose Add custom connector.
4. Name it `PieterPost`.
5. Paste the server URL.
6. Connect and approve the PieterPost OAuth flow.

## Generic MCP Client

Use the remote server URL:

```json
{
  "type": "mcp",
  "name": "PieterPost",
  "server_url": "https://pieterpost.com/mcp/setup/"
}
```

## Public References

- Human docs: `https://pieterpost.com/api/docs/mcp`
- Markdown docs: `https://pieterpost.com/api/docs/mcp.md`
- MCP server URL: `https://pieterpost.com/mcp/setup/`
