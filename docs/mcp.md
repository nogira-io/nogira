# NoGira MCP

NoGira exposes a **Model Context Protocol (MCP)** server so AI clients can read and update NoGira using tools.

This is **remote MCP-first**: clients connect over HTTP to your MCP hostname.

> **NG-716:** URL `?pat=` auth is a temporary bridge for headerless clients (e.g. ChatGPT). Prefer `Authorization: Bearer` when the client supports it.

## URLs

| Service | Pattern |
|---------|---------|
| **UI** | `https://<tenant>.<domain>` |
| **API** | `https://<tenant>.api.<domain>` |
| **MCP** | `https://<tenant>.mcp.<domain>/mcp` |

- **Local evaluation**
  - UI: `http://localhost:3003`
  - API: `http://localhost:4003`
  - MCP: `http://localhost:3100/mcp`
- **NoGira deployment** (example: `<domain>=nogira.io`, `<tenant>=uat`)
  - UI: `https://uat.nogira.io`
  - API: `https://uat.api.nogira.io`
  - MCP: `https://uat.mcp.nogira.io/mcp`
- **Customer self-hosted** — operator chooses `<mcp-host>` (e.g. `mcp.company.com`, `acme.mcp.company.com`)

## Authentication

NoGira uses **Personal Access Tokens (PATs)**.

**Preferred (Cursor, VS Code, etc.):**

- Send `Authorization: Bearer <ng_pat_*>` on each MCP request.

**Headerless fallback (ChatGPT, etc.):**

- Embed PAT in the MCP URL: `https://<mcp-host>/mcp?pat=<ng_pat_*>`
- If both header and `?pat=` are sent, **header wins**.

The MCP server forwards auth to the NoGira API. The API validates the PAT and enforces permissions.

## Tools (MVP1)

- `searchEverything` — search wiki + activities (title + short summary)
- `getWikiPage`
- `updateWikiPage` — full body replace
- `getActivity`
- `updateActivity` — UI-parity update surface

## Cursor setup (header auth)

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

## ChatGPT setup (URL `?pat=`)

```json
{
  "mcpServers": {
    "nogira": {
      "transport": "streamable_http",
      "url": "https://<tenant>.mcp.<domain>/mcp?pat=<PASTE_YOUR_PAT>"
    }
  }
}
```

## Security notes

- Treat PATs like passwords.
- Revoke tokens you don’t need.
- Do not paste PATs in screenshots, issues, or docs.
- Configure reverse proxies so access logs do **not** record `pat` query values.

## Screenshots

![Personal Access Tokens and MCP in Cursor](../assets/nogira-mcp.gif)

*Create a PAT under **Manage Account → Personal Access Tokens**, then point Cursor (or another MCP client) at `http://localhost:3100/mcp` with `Authorization: Bearer <ng_pat_*>`.*

Do not paste real PATs in screenshots, issues, or docs.
