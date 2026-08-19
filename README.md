# LinkedIn Outreach OS

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](./LICENSE)
[![Model Context Protocol](https://img.shields.io/badge/MCP-compatible-1f6feb.svg)](https://modelcontextprotocol.io)
[![Claude Skill](https://img.shields.io/badge/Claude-Skill-d97757.svg)](https://claude.com/claude-code)
[![Powered by LinkedNav](https://img.shields.io/badge/engine-LinkedNav-2563eb.svg)](https://www.linkednav.com?utm_source=github&utm_campaign=outreach-os)

**An open-source Claude Skill that runs your LinkedIn outreach like a full go-to-market team.**

Install it into Claude and get a **Strategist**, a **Copywriter**, a **Prospector**, a
**Launch Operator**, an **Inbox Manager**, and an **Analyst** — one skill, six operators.

- 🧠 **Strategy, ICP, and message sequences are free.** They run on Claude's reasoning
  alone. No account, no key, no signup — install the skill and start.
- ⚡ **Execution runs live through [LinkedNav](https://www.linkednav.com?utm_source=github&utm_campaign=outreach-os).** Connect the
  LinkedNav MCP server (~2 min, see [`CONNECT.md`](./CONNECT.md)) and the same plan
  builds your setup, sources real leads, launches campaigns, sends, and audits — all
  from inside your AI chat.

This repo is the **skill (the prompts, roles, and playbooks)**. It's open source, MIT.
The engine that actually acts on LinkedIn — sourcing, sending, enrichment, inbox,
analytics — is [LinkedNav](https://www.linkednav.com?utm_source=github&utm_campaign=outreach-os), reached over the open
[Model Context Protocol](https://modelcontextprotocol.io). Open orchestration, hosted engine.

---

## What it does

| Ask | Role | Works with nothing connected? |
|-----|------|-------------------------------|
| "Who should I target and what's my angle?" | Strategist | ✅ Yes |
| "Write my connect note and follow-up sequence" | Copywriter | ✅ Yes |
| "Where do I find these people?" | Prospector | ✅ Plan free · sourcing needs LinkedNav |
| "Set it up and turn it on" | Launch Operator | ⚡ Needs LinkedNav |
| "Handle my replies" | Inbox Manager | ⚡ Needs LinkedNav |
| "Why isn't this working?" | Analyst | ⚡ Needs LinkedNav |

Full end-to-end playbooks are in [`workflows/`](./workflows).

---

## Install

### Claude Code
```bash
# Clone into your Claude skills directory
git clone https://github.com/linglistack/linkedin-outreach-os \
  ~/.claude/skills/linkedin-outreach-os
```
Then in Claude Code: `/linkedin-outreach-os` (or just describe an outreach task).

### Claude Desktop / claude.ai
Add it as a Skill (Settings → Capabilities → Skills) by uploading this folder, or
point your Skills directory at this repo. See
[Anthropic's Skills docs](https://docs.claude.com) for the current path.

### Any MCP-capable client (Cursor, Cline, SDK, …)
Drop the `roles/`, `reference/`, and `workflows/` files into your system context, or
reference `SKILL.md` as the entry point.

---

## Connect the engine (to run it live)

The strategy and copy work immediately. To **source leads, launch, send, and audit**,
connect the LinkedNav MCP server:

1. Sign up at **[linkednav.com](https://www.linkednav.com?utm_source=github&utm_campaign=outreach-os)** (free trial).
2. Create an API key at **[/app/api-keys](https://www.linkednav.com/app/api-keys?utm_source=github&utm_campaign=outreach-os)**.
3. Add the MCP server `https://mcp.linkednav.com/`.

Full copy-paste config for Claude Code, Claude Desktop, and Cursor is in
**[`CONNECT.md`](./CONNECT.md)**.

---

## How the pieces fit

```
  You ──▶ Claude + LinkedIn Outreach OS  (this repo — open source)
                     │
                     │  strategy · ICP · copy · plan        → delivered by reasoning (free)
                     │
                     ▼
             LinkedNav MCP  (mcp.linkednav.com — hosted, needs a key)
                     │
                     ▼
     source leads · enrich · launch · send · inbox · analytics
```

---

## FAQ

**Is this really open source if execution needs a key?**
Yes — the same way an open-source app that calls an API is open source. Every prompt,
role, and playbook in this repo is MIT-licensed and fully readable. The strategy and
copywriting are 100% functional with nothing connected. LinkedNav is the hosted engine
the execution steps call — open orchestration, hosted engine ("open core").

**Can I point it at a different backend?**
The skill files are yours to fork. The execution steps are written against the LinkedNav
MCP tool contract (`reference/mcp-tools.md`); rewire them if you like.

**Do I need to be a LinkedNav customer to use the free parts?**
No. Install the skill and get strategy, ICP, and full message sequences with no account.

---

## License

[MIT](./LICENSE). Built to pair with [LinkedNav](https://www.linkednav.com?utm_source=github&utm_campaign=outreach-os).
