# PieterPost MCP

[PieterPost MCP](https://pieterpost.com/mcp/) is a hosted Model Context Protocol (MCP) server for preparing, pricing, reviewing, paying for, and sending real physical letters, postcards, designed letters, and printed greeting cards from ChatGPT, Claude, and other compatible AI assistants.

This public repository contains the integration documentation and registry metadata for the hosted PieterPost MCP server.

## Server

- MCP server URL: [pieterpost.com/mcp/setup/](https://pieterpost.com/mcp/setup/)
- Human docs: [PieterPost MCP documentation](https://pieterpost.com/api/docs/mcp)
- Markdown docs: [PieterPost MCP documentation in Markdown](https://pieterpost.com/api/docs/mcp.md)
- OAuth issuer: `https://pieterpost.com/mcp/oauth`

## What It Does

PieterPost gives MCP clients a safe postal outbox. Agents can design letters and printed greeting cards with PNG previews, draft letters and postcards, quote prices, create review links, create hosted payment links, upload assets, use Address Book contacts, and check order status.

For normal use, agents should create a PieterPost review or payment link. PieterPost sends the mail only after the user reviews and pays.

For greeting cards, use `list_card_options`, `create_card_design`, `get_card_design`, `get_card_preview`, and `update_card_design`. Upload a supplied photo with `upload_asset`, then use its asset ID in the design. After each create or update, call `get_card_preview` for page 0, then page 1, to inspect the actual card images. The private editor link lets the user refine and order the card. Card drafts do not create a paid order. Explain fallback-font and print warnings before ordering.

For designed letters (fonts, colours, photos, illustrations, extra pages, personal fields like `{{first_name}}`), use `list_letter_options`, `create_letter_design`, `get_letter_design`, and `update_letter_design`. Pick the postal layout for the recipient's country. Results list print issues per page, including clashes with other countries' address windows; these block ordering. The private editor link lets the user add recipients and order the letter.

The guest server at `https://pieterpost.com/mcp/public/` needs no account or authentication. It includes the five card tools, the four letter design tools, and nine public mail tools. Account tools and saved contacts use the OAuth server above.

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

## Cursor and Grok Bot plugin

This repository also contains a Cursor plugin manifest at `.cursor-plugin/plugin.json`.
The plugin connects to the public Streamable HTTP server at `https://pieterpost.com/mcp/public/`.
It provides 18 tools and needs no account, API key, or sign-in. Users review and pay on PieterPost before printing and posting.

For review, connect to the public server and test the tools with synthetic data. Use `mode=test` for mail operations and a fresh UUID idempotency key for each new operation. Check the result before retrying an operation. Do not pay or submit a live order during testing.

## Documentation

- [Setup](docs/setup.md)
- [OAuth and permissions](docs/oauth.md)
- [Tools](docs/tools.md)
- [Safe sending flow](docs/safe-sending.md)

## Contact

For questions, contact `pieter@pieterpost.com`.
