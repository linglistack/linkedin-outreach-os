# LinkedIn Outreach OS

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](./LICENSE)
[![Claude Skill](https://img.shields.io/badge/Claude-Skill-d97757.svg)](https://claude.com/claude-code)
[![Powered by LinkedNav](https://img.shields.io/badge/engine-LinkedNav-2563eb.svg)](https://www.linkednav.com?utm_source=github&utm_campaign=outreach-os)

**Get customers from LinkedIn without spending hours on it.**

Add this free skill to Claude and you can talk to it like your own outreach assistant.
Tell it what you sell. It works out who to reach, writes the messages, finds those people,
sends the invites, and even handles the replies.

You do the talking. It does the work.

## Why you'd want this

LinkedIn is full of people who could become your customers. The hard part is actually
reaching them. You have to find the right people, write messages they won't ignore,
remember to follow up, and keep track of everyone. It eats hours, and most people quit
before it pays off.

This skill turns Claude into a small outreach team that does all of it for you:

- Works out who your best customers are and what to say to them
- Writes your connection note and follow-up messages
- Finds real people who fit, including ones already showing they're ready to buy
- Sends the invites and messages for you, at a safe daily pace
- Reads your replies and points out who's worth a call
- Shows you what's working so every week gets better

The payoff: more of the right conversations, and more customers, in a few minutes a day
instead of hours.

## Start in 2 minutes

**1. Add the skill (free).**

*Using Claude Code?* Clone it into your skills folder:
```bash
git clone https://github.com/linglistack/linkedin-outreach-os \
  ~/.claude/skills/linkedin-outreach-os
```
Start a new session and it's ready. Type `/linkedin-outreach-os`, or just describe an outreach task.

*Using Claude Desktop or claude.ai?* These take a single **`.zip`** file, not a folder:
1. Download [**linkedin-outreach-os.zip**](https://github.com/linglistack/linkedin-outreach-os/releases/latest/download/linkedin-outreach-os.zip).
2. In Claude, open **Settings > Skills** (some versions put it under **Settings > Features**), and turn on Skills if it asks.
3. Upload the `.zip`.

Custom skills need a paid Claude plan (Pro, Max, Team, or Enterprise).

**2. Ask Claude about your outreach.** For example:
> "I sell bookkeeping to small law firms. Who should I target on LinkedIn, and what
> should my first message say?"

You'll get a full plan and ready-to-send messages back. This part is free and needs no account.

**3. Connect LinkedNav to make it real.**

When you want Claude to actually find the people and send everything for you, connect
LinkedNav (there's a free trial):

1. Sign up at [linkednav.com](https://www.linkednav.com?utm_source=github&utm_campaign=outreach-os)
2. Grab your key at [linkednav.com/app/api-keys](https://www.linkednav.com/app/api-keys?utm_source=github&utm_campaign=outreach-os)
3. Add the server `https://mcp.linkednav.com/`

The exact copy-paste setup for Claude Code, Claude Desktop, and Cursor is in
[CONNECT.md](./CONNECT.md). It takes about two minutes.

That's it. Now Claude runs your LinkedIn outreach for you.

## Things you can say to it

- "Who should I target, and what's my angle?"
- "Write my invite and follow-up messages."
- "Find people who might want what I sell."
- "Set up my campaign and turn it on."
- "What replies came in, and what should I say back?"
- "How's it going, and what should I fix?"

The first two work with nothing connected. The rest happen for real once LinkedNav is on.

## Free or paid?

The skill is free and open source. The thinking part, your strategy and your messages,
works with nothing connected. To actually find leads and send messages, you connect
LinkedNav, the engine that does the real work on LinkedIn. Think of this repo as a free
recipe, and LinkedNav as the kitchen that cooks it for you.

You can read every prompt in here, change it, or point it at your own tools if you'd rather.

## Questions people ask

**Do I have to pay to try it?**
No. Add the skill and get your targeting, strategy, and full message sequence for free.

**I've never done LinkedIn outreach. Can I still use it?**
That's exactly who it's for. Tell it what you sell in plain words and it walks you through the rest.

**Is it really open source if sending needs a key?**
Yes, the same way an open-source app that uses an API is still open source. Everything
here is free to read and use. LinkedNav is just the engine the "do it for real" steps call.

## License

MIT. Built to work with [LinkedNav](https://www.linkednav.com?utm_source=github&utm_campaign=outreach-os).
