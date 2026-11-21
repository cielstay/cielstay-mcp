# CielStay MCP server

**CielStay** is a free search index of vacation rentals and longer-stay homes from independent hosts and property
managers: more than 100,000 homes in over 100 countries and territories, each with every place it can be booked, including the
host's own booking site. CielStay takes no bookings, no payments and no commissions; it sends the guest to the host.

This repository describes CielStay's public MCP server, so AI assistants can search CielStay directly. The server is
hosted by CielStay. There's nothing to install or run, and no account or API key is needed.

**Server URL:** `https://mcp.cielstay.com/mcp` (Streamable HTTP, no authentication)

## Connect

**Claude (claude.ai and the desktop app).** Settings → Connectors → Add custom connector, then paste the server URL.
Once CielStay is listed in Claude's connector directory, you'll also find it there.

**Claude Code.**

```sh
claude mcp add --transport http cielstay https://mcp.cielstay.com/mcp
```

**ChatGPT.** CielStay's ChatGPT app isn't listed yet. Accounts with developer mode can add the server URL as a custom
connector (Settings → Apps & Connectors → Advanced → Developer mode). Without a connector, ChatGPT can still find
CielStay homes when you ask it to search the web, for example: "Search the web for homes on cielstay.com near Zion for
6 people."

**Gemini (web and app).** Add a custom connector with the server URL, then mention @CielStay in a chat. Steps:
[cielstay.com/docs/api#gemini](https://www.cielstay.com/docs/api#gemini).

**Gemini CLI.**

```sh
gemini extensions install https://github.com/cielstay/cielstay-mcp
```

**Cursor.** In `.cursor/mcp.json` (or Cursor Settings → MCP):

```json
{ "mcpServers": { "cielstay": { "url": "https://mcp.cielstay.com/mcp" } } }
```

**VS Code.** In `.vscode/mcp.json`:

```json
{ "servers": { "cielstay": { "type": "http", "url": "https://mcp.cielstay.com/mcp" } } }
```

Any other MCP client that supports Streamable HTTP can use the same URL.

## Tools

| Tool | What it does |
|---|---|
| `search_vacation_rentals` | Searches homes from a description of the trip (place, dates, party, what matters), with photos, size, a price guide and every booking link CielStay holds. |
| `refine_search` | Adjusts an earlier search from a follow-up such as "closer to the beach" or "bigger". |
| `get_listing_details` | Full details for one home: description, amenities, house rules, location, booking links, and the host's live total for given dates where their booking site supports it. |
| `get_property` | Every unit at a multi-unit property (a small hotel, a glamping site, a building) that shares one booking site. |
| `find_direct_booking` | Looks up a named home, or a link to it on another booking site, and lists every way to book it, including the host's own site. |
| `contact_host` | Sends the traveller's first message to the host (questions, dates, a monthly stay). Free. |
| `book_stay` | At a home whose host offers "Book now": holds the dates for 30 minutes until the traveller confirms by email; payment is between the traveller and the host. |
| `health_check` | Confirms the server and CielStay's API are up. |

`contact_host` and `book_stay` are the two tools that act. Both act only when you ask. The rest only read.

## Example prompts

- "Find a cabin near Zion National Park for 6 people with a hot tub."
- "Beach houses on 30A in Florida for 8, any with a pool?"
- "A quiet apartment in Lisbon for a month this spring, with a workspace."
- "Can I book this home directly with the host?" (with a link to a listing)

## Prices and data

Prices are a guide: CielStay shows an estimate for each home and channel, and the host's own site has the final total.
Listing information comes from hosts' and managers' public booking sites; hosts can claim, correct or remove a listing
at [cielstay.com/opt-out](https://www.cielstay.com/opt-out).

## More

- API and connection docs: [cielstay.com/docs/api](https://www.cielstay.com/docs/api)
- For AI systems: [cielstay.com/llms.txt](https://www.cielstay.com/llms.txt)
- Our crawler: [cielstay.com/bot](https://www.cielstay.com/bot)
- Privacy: [cielstay.com/privacy](https://www.cielstay.com/privacy) · Terms: [cielstay.com/terms](https://www.cielstay.com/terms)
- Contact: [inquiries@cielstay.com](mailto:inquiries@cielstay.com)

The files in this repository are under the MIT licence (see LICENSE). The CielStay service and its data are covered by
CielStay's [Terms](https://www.cielstay.com/terms).

© Ciel Group LLC
