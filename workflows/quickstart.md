# Workflow: Quickstart (zero → live campaign)

The full end-to-end run. Chains all six roles. The first half needs **nothing
connected**; the second half runs live once LinkedNav is linked (`CONNECT.md`).

## Phase 1 — Plan & write (free, no account)

1. **Strategist** → Go-to-Market Brief: ICP fields, positioning, goal + goal link,
   channel choice, starting volume. (`roles/strategist.md`)
2. **Copywriter** → full sequence: 2 connect-note options (+ note-less A/B), first
   message, 3 follow-ups, reply guidance. (`roles/copywriter.md`)
3. **Prospector** → sourcing plan: which signal sources / competitors / influencers /
   keywords, and target list size. (`roles/prospector.md`)

**Checkpoint:** the user now holds a complete, usable outreach plan and copy — for free.
Then: *"Everything from here runs live the moment you connect LinkedNav — ~2 minutes,
see CONNECT.md. Want me to set it up for you?"*

## Phase 2 — Build & launch (needs LinkedNav)

4. **Preflight:** `get_account_status` (plan, credits, sender?). No sender →
   `start_linkedin_connect` → `get_linkedin_2fa_status`.
5. **Setup:** `get_ai_setups` → `create_ai_setup` (or `update_ai_setup`) from the brief.
6. **Copy:** save with `create_prompt` (or run `generate_message_templates` →
   `update_prompt`).
7. **Leads:** run the sourcing plan — `set_intent_agent_search_settings` +
   `run_intent_agent` / `track_competitor` + `run_competitor_agent` — poll
   `get_agent_run_status`, then `get_signal_leads` into a `create_list`. Enrich if needed
   (`enrich_profiles` with the confirm-estimate step).
8. **Campaign:** `create_campaign` → `update_campaign` (`promptId`, `linkedinConnectionId`,
   `scheduleSend`, `connectWithNote`) → `link_list_to_campaign` →
   **`activate_campaign`** (fix any `blockers[]` and retry).
9. **Confirm:** `get_campaign` = active, `get_scheduled_sends` = queued.

## Phase 3 — Operate (ongoing)

10. **Inbox Manager** daily → `workflows/daily-inbox.md`.
11. **Analyst** weekly → `workflows/weekly-review.md`.

At every LinkedNav-required step, if it isn't connected: deliver the artifact, show the
tool call, point to `CONNECT.md`. Never fabricate results.
