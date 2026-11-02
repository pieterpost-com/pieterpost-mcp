# Tools

PieterPost MCP exposes tools for letter and printed greeting card design, postal workflows, account context, payment links, and Address Book contacts.

## Documentation Tools

- `search`: Search PieterPost API and MCP docs.
- `fetch`: Fetch a specific PieterPost document or account context item.

## Mail Tools

- `prepare_letter`: Validate, price, and save an unpaid letter (plain text, PDFs, or images), with standard or registered delivery, including US Certified Mail.
- `prepare_postcard`: Validate, price, and save an unpaid postcard, optionally with a square custom front.
- `quote_order`: Price a letter or postcard before sending.
- `create_compose_link`: Create a PieterPost review link with prepared recipient and message data.
- `create_payment_link`: Create a hosted payment link for a prepared letter or postcard.
- `create_checkout_link`: Compatibility checkout link tool.
- `get_order`: Check order status.
- `upload_asset`: Upload supported assets, such as postcard front images, letter attachments, letter stamp images, or photos for cards and designed letters.

## Printed Greeting Card Tools

- `list_card_options`: List starter designs, formats, paper, techniques, fonts, and illustrations.
- `create_card_design`: Create a private card draft from a starter or blank design, with PNG previews.
- `get_card_design`: Read the current design and version, including editor changes.
- `update_card_design`: Apply edits with the latest `baseVersion`; a version conflict returns the current design.

These four tools work on both the guest and OAuth servers. For a supplied card photo, use `upload_asset` with `kind=postcard-image`; card photos can have any aspect ratio. Use the returned `assetId` in `add_image`.

Check `characterIssues`, `printIssues`, and `design.card.techniqueIssues`. Explain characters printed in the fallback font, and fix blocking issues before ordering. Share the PNG previews and private `editorUrl` only with the user. The user refines and orders the card in the editor. No print PDF is returned, and creating a draft does not order, pay, print, or send a card.

## Letter Design Tools

- `list_letter_options`: List starter letters, postal layouts (page size, address window, postal zones, and the recipient countries each is printed for), personal fields, fonts, and illustrations (marked photo or illustration).
- `create_letter_design`: Create a private letter draft from a starter or blank letter in a postal layout, with PNG previews.
- `get_letter_design`: Read the current design and version, including editor changes. Element texts come back in full.
- `update_letter_design`: Apply edits with the latest `baseVersion`, including `set_layout`, `add_page`, and `delete_page`; a version conflict returns the current design.

These four tools work on both the guest and OAuth servers and share the card tools' drafts, previews, and image handling. Text may hold personal fields such as `{{first_name}}`, filled in per recipient. Page 0's preview shows a grey sample address in the address window.

Fix every blocking entry in `printIssues` (edge clearance, address window, postal zones) and in `design.printIssuesInOtherLayouts`, which checks the layouts recipients in other countries get at checkout. Low-resolution images come back as non-blocking `image_dpi` warnings. Share the PNG previews and private `editorUrl` only with the user, who adds recipients and orders the letter in the editor. Creating a draft does not order, pay, print, or send a letter.

## Address Book Tools

- `list_address_book_contacts`: Search saved contacts.
- `get_address_book_contact`: Fetch one saved contact.
- `create_address_book_contact`: Create a contact when authorized.
- `update_address_book_contact`: Update a contact when authorized.
- `delete_address_book_contact`: Delete a contact when authorized.

## Developer Tools

- `get_wallet`: Check API credit wallet balance.
- `create_credit_topup`: Create a wallet top-up checkout.
- `list_topups`: List top-ups.
- `get_topup`: Check a top-up.
- `create_direct_order`: Send directly with API credits. Use only for trusted workflows and explicit live-send confirmation.
- `list_api_keys`: List API keys.
- `create_api_key`: Create an API key.
- `revoke_api_key`: Revoke an API key.

## Payload Notes

Address input should be structured. Provide a recipient name plus `addressLines`, or structured fields such as `streetAddress`, `postalCode`, `city`, `state`, and `country`.

Custom postcard front images must be square, with a 1:1 aspect ratio.
