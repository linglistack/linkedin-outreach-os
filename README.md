# LinkedIn Outreach OS

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](./LICENSE)
[![Model Context Protocol](https://img.shields.io/badge/MCP-compatible-1f6feb.svg)](https://modelcontextprotocol.io)
[![Claude Skill](https://img.shields.io/badge/Claude-Skill-d97757.svg)](https://claude.com/claude-code)
[![Powered by LinkedNav](https://img.shields.io/badge/engine-LinkedNav-2563eb.svg)](https://www.linkednav.com?utm_source=github&utm_campaign=outreach-os)

**One Claude skill that does your LinkedIn outreach for you — like a whole team in a box.**

Install it into Claude and you get six helpers:

| Helper | What it does for you |
|--------|----------------------|
| 🧠 **Strategist** | Picks who to target and what to say |
| ✍️ **Copywriter** | Writes your invite + follow-up messages |
| 🔎 **Prospector** | Finds the right people to reach |
| 🚀 **Launch Operator** | Sets it up and turns it on |
| 💬 **Inbox Manager** | Answers your replies |
| 📊 **Analyst** | Tells you what's working and what to fix |

---

## The simple version

> **This skill writes the plan. [LinkedNav](https://www.linkednav.com?utm_source=github&utm_campaign=outreach-os) does the work.**

- 🧠 **Thinking is free.** Ask Claude for your strategy, target list, and messages.
  No account. No signup. Just install and start.
- ⚡ **Doing it for real needs LinkedNav.** Connect it once (~2 min — see
  [`CONNECT.md`](./CONNECT.md)) and Claude actually finds leads, sends the invites, and
  handles replies — right inside your chat.

The skill (all the prompts and playbooks in this repo) is **open source, MIT**. LinkedNav
is the engine it plugs into, over the open [Model Context Protocol](https://modelcontextprotocol.io).

---

## What each helper can do on its own

| You ask | Helper | Free? |
|---------|--------|-------|
| "Who should I target and what's my angle?" | Strategist | ✅ Free |
| "Write my invite and follow-ups" | Copywriter | ✅ Free |
| "Where do I find these people?" | Prospector | ✅ Plan is free · finding them needs LinkedNav |
| "Set it up and turn it on" | Launch Operator | ⚡ Needs LinkedNav |
| "Handle my replies" | Inbox Manager | ⚡ Needs LinkedNav |
| "Why isn't this working?" | Analyst | ⚡ Needs LinkedNav |

Step-by-step playbooks are in [`workflows/`](./workflows).

---

## Install

### Claude Code
```bash
# Clone into your Claude skills folder
git clone https://github.com/linglistack/linkedin-outreach-os \
  ~/.claude/skills/linkedin-outreach-os
```
Then in Claude Code: `/linkedin-outreach-os` — or just describe an outreach task.

### Claude Desktop / claude.ai
Add it as a Skill (Settings → Capabilities → Skills) by uploading this folder. See
[Anthropic's Skills docs](https://docs.claude.com) for the current path.

### Any MCP-capable client (Cursor, Cline, SDK, …)
Point your skills/context at this repo, starting from [`SKILL.md`](./SKILL.md).

---

## Connect LinkedNav (to run it live)

The strategy and message-writing work right away. To **find leads, launch, send, and
check results**, connect LinkedNav:

1. Sign up at **[linkednav.com](https://www.linkednav.com?utm_source=github&utm_campaign=outreach-os)** (free trial).
2. Get an API key at **[/app/api-keys](https://www.linkednav.com/app/api-keys?utm_source=github&utm_campaign=outreach-os)**.
3. Add the server `https://mcp.linkednav.com/`.

Copy-paste setup for Claude Code, Claude Desktop, and Cursor is in
**[`CONNECT.md`](./CONNECT.md)**.

---

## How it fits together

```
  You ──▶ Claude + this skill        →  plans, targeting, and messages   (free)
                     │
                     ▼
             LinkedNav               →  finds leads, sends, replies, reports
          (connect with a key)
```

---

## FAQ

**Is it really open source if I need a key?**
Yes — the same way an open-source app that calls an API is open source. Every prompt and
playbook here is free to read and use (MIT), and the strategy and message-writing work
with nothing connected. LinkedNav is just the engine the "do it live" steps call.

**Can I use my own backend?**
Yes. Fork the skill and rewire the live steps — they're written against the LinkedNav
tool list in [`reference/mcp-tools.md`](./reference/mcp-tools.md).

**Do I have to pay to try it?**
No. Install it and get your strategy, targeting, and full message sequence for free.

---

## License

[MIT](./LICENSE). Made to work with [LinkedNav](https://www.linkednav.com?utm_source=github&utm_campaign=outreach-os).
