# Installing the CielStay MCP server (for AI agents)

CielStay's MCP server is hosted. There is nothing to clone, build or run, and no API key.

- Transport: Streamable HTTP
- URL: `https://mcp.cielstay.com/mcp`
- Authentication: none

Add it to the client's MCP configuration as a remote server with that URL, for example:

```json
{ "mcpServers": { "cielstay": { "url": "https://mcp.cielstay.com/mcp" } } }
```

To check the connection, call the `health_check` tool; it should report the server and API as healthy. Then try
`search_vacation_rentals` with a query such as "cabin near Zion National Park for 6 people".

Two tools act rather than read: `contact_host` (sends the traveller's first message to a host) and `book_stay` (holds
dates at a "Book now" home until the traveller confirms by email). Both act only when the user asks.
