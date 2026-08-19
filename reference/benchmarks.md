# Outbound benchmarks & guardrails

Use these to set expectations and to read `analyze_performance` output. LinkedNav's
expert tools grade against the same floors/targets, so your commentary should match
what the tool returns — never contradict a tool result with a guessed number.

## Connection-outreach funnel (LinkedNav benchmarks)

| Rate | Floor (fix it) | Target (healthy) | Strong |
|------|----------------|------------------|--------|
| **Accept rate** (invites → connections) | 15% | 25% | 35%+ |
| **Reply rate** (connections → replies) | 10% | 18% | 28%+ |
| **Opportunity rate** (replies → real opportunities) | 3% | 8% | 15%+ |

How to read them:
- **Low accept rate** → targeting or connect note. Tighten the ICP, or make the note
  shorter and more relevant (or test note-less connects).
- **Low reply rate** → the first message or timing. Lead with them, not you; make the
  ask a question, not a pitch.
- **Low opportunity rate** → the offer/goal fit, or reply handling. Revisit positioning
  and the goal link; check the inbox isn't going cold.

## Safe sending volume (protect the account)

- New / cold LinkedIn senders: start **~15–20 invites/day**, ramp slowly.
- Warmed, healthy senders: up to ~**25–40/day** depending on account age and history.
- `create_campaign` defaults `sendsPerDay` to 20 — a sane starting point.
- Prefer quality over volume: a tight ICP at 20/day beats a loose one at 100/day, and
  keeps accept rate (and the account) healthy.

## Message limits (hard constraints)

- **Connect note:** ≤ 300 characters. Shorter usually accepts better. Note-less is a
  valid test (`connectWithNote: false`).
- **Messages / replies:** keep well under the 2,000-char send limit; 400–600 chars reads better.
- **Language:** match the prospect's; set `outreachLanguage` on the campaign/setup.

## Cadence (default sequence spacing)

A reasonable default the Copywriter and Launch Operator assume unless told otherwise:

| Step | When | Purpose |
|------|------|---------|
| Connect note | Day 0 | Get accepted |
| First message | On accept (or +1 day) | Open a conversation, no pitch |
| Follow-up 1 | +3 days | Add value / a reason to reply |
| Follow-up 2 | +5 days | Different angle |
| Follow-up 3 | +7 days | Graceful last touch / breakup |

## Segments worth watching

`analyze_performance` breaks results down by `jobTitle`, `industry`, and `icpScore`.
When a segment vastly out- or under-performs, that's your steering signal: double down
on the winners in `prioritize_campaign_leads`, cut or re-message the losers.
