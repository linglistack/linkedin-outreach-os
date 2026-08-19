# Workflow: Weekly review (15 minutes)

Run by the **Analyst**, then hand fixes to the right role. Needs LinkedNav connected.

1. **Whole picture:** `full_audit` (`days: 30`). Read the prioritized `fixPlan`.
2. **Funnel detail:** `analyze_performance` (`days: 30`). Compare accept / reply /
   opportunity rates to `reference/benchmarks.md`. Note the bottleneck, the best prompt,
   and the winning segment.
3. **Deals:** `analyze_pipeline`. Who's `waitingOnYou` (act today), `goingQuiet`
   (nudge — hand to Inbox Manager), `warmBench` (keep warm), `opportunities` (push).
4. **Rank 3 fixes** — each with the tool + role:
   - Low accept → **Strategist**/**Prospector** (tighten ICP) or **Copywriter** (connect note).
   - Low reply → **Copywriter** (`generate_message_templates` → `update_prompt`).
   - Low opportunity → **Strategist** (offer/goal) or **Inbox Manager** (reply handling).
   - Stalled campaign → **Launch Operator** (`diagnose_campaign`).
5. **Steer to winners:** `get_performance_analytics` (`rankBy`) → have Launch Operator
   `prioritize_campaign_leads` toward the best-fit segment; pause or re-message losers.
6. **Top up leads** if the list is running low → **Prospector**.

Rule: every number comes from a tool; output a ranked action list, not a data dump.
