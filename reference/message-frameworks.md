# Message frameworks

Copywriting reference for the **Copywriter** role. These produce the sequence that the
`generate_message_templates` expert tool and `create_prompt` / `update_prompt` store.

## The one rule

**Lead with them, not you.** Every message should read like it was written for one
person. The prospect should feel seen before they feel sold to.

## Connect note (≤ 300 chars)

Goal: get accepted, not to pitch. Options that work:
- **Reason-to-connect:** one specific, true observation about them + a light reason.
  > "Saw your team's hiring for 3 SDRs — scaling outbound is exactly the mess we help
  > with. Would love to connect."
- **Shared context:** mutual group, event, content they posted.
- **No note at all** (`connectWithNote: false`) — often a higher accept rate. Test it.

Avoid: "I'd love to add you to my network," feature lists, links, anything generic.

## First message (on accept)

Open a conversation. **Do not pitch.** Frameworks:
- **Observation → question:** name why you reached out, then ask one easy question.
- **PS (Problem–Solution) soft-open:** name the problem you suspect they have, ask if
  it's real for them — no solution yet.

> "Thanks for connecting, {first}. Curious — how are you handling {problem} today?
> Ask because {one line of relevance}."

## Follow-ups (3, spaced — see benchmarks.md)

Each one is a *new reason to reply*, not "just bumping this":
1. **Value:** share a relevant resource, result, or insight. No ask.
2. **New angle:** reframe the problem, or a proof point (a peer/competitor result).
3. **Breakup:** graceful last touch. "I'll stop here — if {problem} ever gets loud,
   my door's open." Breakups often get the most replies.

## Reply guidance (how the AI/inbox handles responses)

Store this so replies stay on-brand:
- Tone (e.g. warm, concise, peer-to-peer — no corporate speak).
- The single goal / next step (book a call? send the goal link? qualify?).
- What to do on: interested / not now / not the right person / objection.
- Hard rules: never over-promise, never send more than one link, always end with a
  question when the goal is a meeting.

## Personalization tokens

LinkedNav fills these from contact data — use them, don't hardcode names:
`{first}` `{firstName}` `{company}` `{jobTitle}` `{location}`. Write so the message
still reads well if a token is empty.

## Quality bar (self-check before saving)

- Could this have been sent to 500 people unchanged? → too generic, rewrite.
- Is the first line about them? → it must be.
- Is there exactly one ask (or zero)? → trim the rest.
- Under the char limits? → connect note ≤300, messages short.
- Does it sound like a human typed it on their phone? → good.
