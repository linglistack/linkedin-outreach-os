# Connect LinkedNav

On its own, the skill can plan your outreach and write your messages for free. Connect
LinkedNav and Claude can actually do it for you: find the right people, send the invites
and messages, read your replies, and show you how it's going. This takes about two minutes.

## 1. Get your key

1. Sign up or log in at [linkednav.com](https://www.linkednav.com?utm_source=github&utm_campaign=outreach-os) (there's a free trial).
2. Open [linkednav.com/app/api-keys](https://www.linkednav.com/app/api-keys?utm_source=github&utm_campaign=outreach-os).
3. Create a key and copy it. Keep it private, like a password.

## 2. Add LinkedNav to your app

Pick the app you use. Paste your key where it says `YOUR_KEY`.

### Claude Code
```bash
claude mcp add --transport http linkednav https://mcp.linkednav.com/ \
  --header "Authorization: Bearer YOUR_KEY"
```
To check it worked, run `claude mcp list`. You should see `linkednav`.

### Claude Desktop or claude.ai
1. Go to Settings, then Connectors, then Add custom connector.
2. Name it `LinkedNav`.
3. URL: `https://mcp.linkednav.com/`
4. Choose to sign in with your browser (no key to paste), or add a header
   `Authorization: Bearer YOUR_KEY` if your app asks for one.

### Cursor, Cline, or another MCP app
Add this to your MCP settings file (for Cursor that's `~/.cursor/mcp.json`):
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

## 3. Check it's working

Ask Claude: **"Check my LinkedNav account."**
If it shows your plan and credits, you're connected.

Then try: **"Audit my outreach."** Claude runs a full review of your account and tells you
what to fix first.

## What it costs

Most things are included in your plan. A few extras use credits, and Claude always shows
you the price before it charges:

- Finding someone's email or phone: 1 credit each, and only when it actually finds one.
- Filling in profile details like job, company, and location: about 0.07 credits per
  profile found. Claude shows you the total and waits for your yes.

A few features need the Pro plan (things like auto-replies and some lead sources). Claude
will tell you if something needs Pro.

## If something goes wrong

- **"Not authorized" or a login error.** Your key is missing or expired. Make a new one
  at [linkednav.com/app/api-keys](https://www.linkednav.com/app/api-keys?utm_source=github&utm_campaign=outreach-os) and add it again.
- **Claude doesn't see the tools.** Make sure LinkedNav shows up in your app's connector
  list, and that the address ends in a slash: `https://mcp.linkednav.com/`.
- **"No LinkedIn account connected."** Connect one first. Just ask Claude, "Connect my
  LinkedIn account," and it gives you a private, secure link to do it. You never paste a
  password into the chat.

## For the technically curious

- The server speaks the Model Context Protocol over HTTP.
- Sign in with an API key (`Authorization: Bearer` or `X-API-Key` header) or with OAuth.
- Everything runs inside your own account, using your own LinkedIn login.
