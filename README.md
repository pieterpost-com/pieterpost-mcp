# PieterPost MCP

[PieterPost MCP](https://pieterpost.com/mcp/) is a hosted Model Context Protocol (MCP) server for preparing, pricing, reviewing, paying for, and sending real physical letters, postcards, and printed greeting cards from ChatGPT, Claude, and other compatible AI assistants.

This public repository contains the integration documentation and registry metadata for the hosted PieterPost MCP server.

## Server

- MCP server URL: [pieterpost.com/mcp/setup/](https://pieterpost.com/mcp/setup/)
- Human docs: [PieterPost MCP documentation](https://pieterpost.com/api/docs/mcp)
- Markdown docs: [PieterPost MCP documentation in Markdown](https://pieterpost.com/api/docs/mcp.md)
- OAuth issuer: `https://pieterpost.com/mcp/oauth`

## What It Does

PieterPost gives MCP clients a safe postal outbox. Agents can design printed greeting cards with PNG previews, draft letters and postcards, quote prices, create review links, create hosted payment links, upload assets, use Mailbook contacts, and check order status.

For normal use, agents should create a PieterPost review or payment link. PieterPost sends the mail only after the user reviews and pays.

For greeting cards, use `list_card_options`, `create_card_design`, `get_card_design`, and `update_card_design`. Upload a supplied photo with `upload_asset`, then use its asset ID in the design. The private editor link lets the user refine and order the card. Card drafts do not create a paid order. Explain fallback-font and print warnings before ordering.

The guest server at `https://pieterpost.com/mcp/public/` needs no account or authentication. It includes the four card tools and nine public mail tools. Account tools and saved contacts use the OAuth server above.

## Client Configuration

Use this server URL in MCP clients that support remote Streamable HTTP servers:

```text
https://pieterpost.com/mcp/setup/
```

Example MCP client snippet:

```json
{
  "type": "mcp",
  "name": "PieterPost",
  "server_url": "https://pieterpost.com/mcp/setup/"
}
```

## Docs

- [Setup](docs/setup.md)
- [OAuth and permissions](docs/oauth.md)
- [Tools](docs/tools.md)
- [Safe sending flow](docs/safe-sending.md)

## Contact

For questions, contact `pieter@pieterpost.com`.
