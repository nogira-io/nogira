# NoGira MCP

NoGira exposes a **Model Context Protocol (MCP)** server so AI clients can read and update NoGira using tools.

This is **remote MCP-first**: clients connect over HTTP to your MCP hostname.

## URLs

- **Local evaluation**
  - UI: `http://localhost:3000`
  - API: `http://localhost:4000`
  - MCP: `http://localhost:3100/mcp`
- **Hosted**
  - UI: `https://<env>.nogira.io`
  - API: `https://<env>.api.nogira.io`
  - MCP: `https://<env>.mcp.nogira.io/mcp`

## Authentication

NoGira uses **Personal Access Tokens (PATs)**.

- MCP clients must send `Authorization: Bearer <ng_pat_*>` on every MCP request.
- The MCP server forwards the header to the NoGira API.
- The API validates the PAT and enforces permissions.

## Tools (MVP1)

- `searchEverything` — search wiki + activities (title + short summary)
- `getWikiPage`
- `updateWikiPage` — full body replace
- `getActivity`
- `updateActivity` — UI-parity update surface

## Cursor setup

Create or edit `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "nogira": {
      "transport": "streamable_http",
      "url": "http://localhost:3100/mcp",
      "headers": {
        "Authorization": "Bearer <PASTE_YOUR_PAT>"
      }
    }
  }
}
```

Restart Cursor. Then in Cursor Chat, try:

- “List tools from the `nogira` MCP server.”
- “Use `nogira.searchEverything` with q=`work`, limit=5.”

## Security notes

- Treat PATs like passwords.
- Revoke tokens you don’t need.
- Do not paste PATs in screenshots, issues, or docs.

## Screenshots (coming soon)

- MCP setup in Cursor
- PAT creation in NoGira Account Center

