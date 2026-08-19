# Connect LinkedNav (the execution engine)

The strategy and copywriting in this skill work with **nothing connected**. To
*run* the work — source real leads, launch campaigns, enrich, send, read your
inbox, and audit performance — connect the **LinkedNav MCP server**. It takes
about two minutes.

---

## 1. Get an API key

1. Sign up / log in at **[linkednav.com](https://www.linkednav.com?utm_source=github&utm_campaign=outreach-os)** (free trial).
2. Go to **[www.linkednav.com/app/api-keys](https://www.linkednav.com/app/api-keys?utm_source=github&utm_campaign=outreach-os)**.
3. Create a key and copy it. Treat it like a password.

**Server URL:** `https://mcp.linkednav.com/`
**Transport:** Streamable HTTP (JSON-RPC + SSE)

Authentication — either works:
- **API key header:** `Authorization: Bearer <YOUR_KEY>`  *(or)*  `X-API-Key: <YOUR_KEY>`
- **OAuth 2.1** (PKCE): sign in through the connector's browser flow — no key to paste.

---

## 2. Add the server to your client

### Claude Code (CLI)
```bash
claude mcp add --transport http linkednav https://mcp.linkednav.com/ \
  --header "Authorization: Bearer YOUR_KEY"
```
Verify: `claude mcp list` should show `linkednav`. Then start a session and ask an
outreach question — the OS will call LinkedNav tools automatically.

### Claude Desktop / claude.ai (custom connector)
Settings → **Connectors** → **Add custom connector**:
- **Name:** LinkedNav
- **URL:** `https://mcp.linkednav.com/`
- Choose **OAuth** and sign in when prompted (no key needed), **or** add an
  `Authorization: Bearer YOUR_KEY` header if your client supports header auth.

### Cursor / Cline / other MCP clients
Add to your MCP config (e.g. `~/.cursor/mcp.json`):
```json
{
  "mcpServers": {
    "linkednav": {
      "url": "https://mcp.linkednav.com/",
      "headers": { "Authorization": "Bearer YOUR_KEY" }
    }
  }
}
```

### SDK / programmatic
Point any MCP-capable client at `https://mcp.linkednav.com/` with the
`Authorization: Bearer` (or `X-API-Key`) header. OAuth discovery is published at
`/.well-known/oauth-protected-resource`.

---

## 3. Confirm it's live

Ask Claude: **"Check my LinkedNav account status."**
It should call `get_account_status` and return your plan, credits, and connected
LinkedIn senders. If you see real numbers, you're connected.

Then: **"Audit my outreach."** → `full_audit` runs the whole review.

---

## What each capability costs

Most tools are included with your plan. A few are credit-metered (LinkedNav relays the
exact cost before charging — you confirm first):

- **Email / phone enrichment** — 1 credit each, charged only when a result is found.
- **Profile enrichment** (`enrich_profiles`) — ~0.07 credits/profile, charged only for
  found profiles; call returns an estimate before you confirm.
- **Comment-monitor targets** — free allotment per seat, then credit-metered.

Pro-only capabilities (auto-reply, monitor-mode comment campaigns, connection
withdrawal, multi-setup, richer signal types) are noted in `reference/mcp-tools.md`.

---

## Troubleshooting

- **401 / "unauthorized"** — key missing, revoked, or expired. Re-create at
  `/app/api-keys` and re-add the header.
- **Tools don't appear** — confirm the server shows in your client's MCP list and the
  URL ends in a trailing `/`.
- **"No LinkedIn sender connected"** — connect one first: ask "Connect my LinkedIn
  account," which runs `start_linkedin_connect` and returns a private link.
