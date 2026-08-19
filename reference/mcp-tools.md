# LinkedNav MCP — tool reference (canonical)

**This is the source of truth for tool names and parameters.** Roles must call only
tools listed here, with only these parameters. Do not invent tools, rename them, or
add parameters. If a capability isn't here, say so rather than guessing.

Server: `https://mcp.linkednav.com/` · Auth: `Authorization: Bearer <key>` or `X-API-Key`
· See `CONNECT.md`. All tools run in the authenticated user's scope and respect their
active AI setup. `Pro` marks Pro-plan-only tools.

Convention: **R** = read-only, **W** = write/side-effect, **W!** = destructive (confirm first).

---

## Expert tools (prefer these for decisions — one call, full analysis)

| Tool | R/W | Key params | Returns |
|------|-----|-----------|---------|
| `full_audit` | R | `days?` (7–90, def 30) | Merged prioritized `fixPlan` across delivery, setup, performance, pipeline |
| `audit_setup` | R | — | 0–100 setup score + graded gaps (what/why/how/action) |
| `analyze_performance` | R | `campaignId?`, `days?` (7–90) | Funnel rates vs benchmarks, weekly trend, segments, best prompt, bottleneck, recs |
| `analyze_pipeline` | R | `limit?` (def 10), `days?` (def 90) | People ranked by conversion likelihood: opportunities, waitingOnYou, goingQuiet, warmBench |
| `diagnose_campaign` | R | `campaignId?` | Status-aware doctor: blockers, warnings, next send, fix |
| `generate_message_templates` | R | `campaignId?`, `promptId?`, `useExistingAsBaseline?` | Full sequence draft + exact `update_prompt` call (does **not** save) |

---

## Setup / config

| Tool | R/W | Key params |
|------|-----|-----------|
| `get_ai_setups` | R | `status?` (completed\|draft\|all), `includeDetails?` |
| `get_ai_setup` | R | `setupId?` (omit = active) |
| `create_ai_setup` | W | `name?`, `company?`, `websiteUrl?` (triggers AI analysis), `businessContext?`, `campaignSettings?`, `idealCustomerProfile?`, `signalAgents?` — Free/Std: 1 setup, Pro: 3 |
| `update_ai_setup` | W | same shape as create (all optional) |
| `select_ai_setup` | W | `setupId` (activate for future calls) |
| `generate_ai_setup_icp` | W | `setupId`, `regenerate?` |
| `delete_ai_setup` | W! | `setupId` |

`businessContext`: businessName, coreValueProposition, keyProducts[], uniqueDifferentiators,
benefits, features, pricingInfo, problemsSolved, uniqueValue.
`idealCustomerProfile`: targetIndustries[], headcounts[], regions[], functions[], seniorities[], jobTitles[].
`campaignSettings`: goal, goalLink, outreachLanguage.

---

## Campaigns (connection outreach)

| Tool | R/W | Key params |
|------|-----|-----------|
| `get_campaigns` | R | `status?`, `limit?`, `sort?` |
| `get_campaign` | R | `campaignId` |
| `get_campaigns_summary` | R | — |
| `create_campaign` | W | `name` (req), `goal?`, `goalLink?`, `outreachLanguage?`, `sendsPerDay?` (1–100, def 20) |
| `update_campaign` | W | `campaignId`, `name?`, `goal?`, `goalLink?`, `promptId?`, `linkedinConnectionId?`, `scheduleSend?` {perDay,timeEST,daysOfWeek}, `connectWithNote?`, `autoReplyEnabled?` (Pro), `autoWelcomeMessageEnabled?` (Std/Pro) |
| `activate_campaign` | W | `campaignId`, `linkedinConnectionId?` — validates prospects, prompt, goal link, payment, sender; returns `blockers[]` if not ready |
| `pause_campaign` | W | `campaignId`, `reason?` |
| `duplicate_campaign` | W | `campaignId`, `name?`, `copyContacts?` |
| `delete_campaign` | W! | `campaignId` |

### Campaign leads
| Tool | R/W | Key params |
|------|-----|-----------|
| `add_lead_to_campaign` | W | `campaignId`, `contactId?` or `{profileUrl, firstName, …}` |
| `add_leads_bulk_to_campaign` | W | `campaignId`, `contactIds[]` (≤1000) |
| `link_list_to_campaign` | W | `campaignId`, `listId` |
| `remove_leads_from_campaign` | W | `campaignId`, `contactIds[]` |
| `prioritize_campaign_leads` | W | `campaignId`, `priorityRank[]` (contactIds in order) |

---

## Comment / engagement campaigns

| Tool | R/W | Key params |
|------|-----|-----------|
| `create_comment_campaign` | W | `name`, `sourceMode` (posts\|monitor), `goal?`, `goalLink?`, `outreachLanguage?` |
| `add_post_targets` | W | `campaignId`, `postUrls[]` |
| `add_monitor_targets` | W | `campaignId`, `profileUrls[]` (profiles/companies to watch) |
| `remove_post_targets` / `remove_monitor_targets` | W | `campaignId`, urls[] |
| `retry_post_target` | W | `campaignId`, `postUrl` |
| `set_post_target_watcher` | W | `campaignId`, `postUrl`, `enabled` |
| `update_comment_settings` | W | `campaignId`, `template?`, `maxComments?`, `sourceMode?`, `scrapeReactions?`/`maxReactions?` (Pro) |

---

## Contacts, lists, prompts

| Tool | R/W | Key params |
|------|-----|-----------|
| `get_contacts` | R | `search?`, `campaignId?`, `listId?`, `intentScoreMin/Max?`, `isConnected?`, `isOpportunity?`, `needsFollowUp?`, `limit?`, `skip?` |
| `get_contact` | R | `contactId` |
| `get_contacts_summary` | R | — |
| `update_contact` | W | `contactId`, name/jobTitle/company/email/phone/location?, `icpScore?` (0–10), `notes?`, `isOpportunity?` |
| `create_contact` / `create_lead` | W | `profileUrl` (req), firstName/lastName/company/jobTitle/location/email/phone? |
| `create_leads_bulk` | W | `leads[]` (≤1000, each {profileUrl, …}) |
| `delete_contact` / `bulk_delete_contacts` | W! | `contactId` / `contactIds[]` |
| `bulk_move_contacts` | W | `contactIds[]` (≤500), `listId` |
| `get_lists` / `get_list_contacts` | R | — / `listId`, `search?`, `limit?` |
| `create_list` / `update_list` | W | `name` / `listId`, `name?`, `description?` |
| `delete_list` | W! | `listId` (contacts kept) |
| `get_prompts` / `get_prompt` | R | — / `promptId` |
| `create_prompt` | W | `name`, `connectMessage?` (≤300), `firstMessage?`, `followUp1-3?`, `replyGuidance?` |
| `update_prompt` | W | `promptId`, same fields |
| `delete_prompt` | W! | `promptId` |

---

## Signal agents (lead sourcing) & discovery

| Tool | R/W | Key params |
|------|-----|-----------|
| `run_intent_agent` | W | `searchTypes?[]` — triggers a run; returns `runId` |
| `run_influencer_agent` / `run_competitor_agent` | W | — ; returns `runId` |
| `get_agent_run_status` | R | `runId` (poll: queued\|running\|completed\|failed) |
| `get_signal_leads` (aka `get_signal_agent_results`) | R | `agents?[]`, `intentScoreMin/Max?`, `postUrl?`, `limit?`, `skip?` |
| `delete_signal_leads` / `clear_signal_agent_results` | W / W! | `agent?`, `leadUrls?[]` / `agent` |
| `track_influencer` | W | `profileHandle?` or `profileUrl?` |
| `track_competitor` | W | `companyHandle?` or `companyUrl?` |
| `untrack_influencer` / `untrack_competitor` | W | `profileUrl` / `companyUrl` |
| `find_competitors` / `find_influencers` | W | `description` (AI discovery; returns `runId`) |
| `get_discovery_status` | R | `runId` |
| `get_signal_agent_settings` | R | — |
| `set_signal_agent_auto_run` | W | `agent` (influencer\|competitor\|intent), `enabled` |
| `set_signal_agent_auto_add` | W | `agent`, `enabled`, `destinations?[]` (Pro) |
| `set_signal_agent_scrape_settings` | W | `agent` (influencer\|competitor), `scrapeComments?`, `maxComments?`, `scrapeReactions?`, `maxReactions?`, `postedLimit?` (1h\|24h\|week\|month) |
| `set_intent_agent_search_settings` | W | `searchTypes?[]`, `regions?[]`, `headcounts?[]`, `industryFocus?[]`, `jobTitles?[]`, `seniorities?[]` |

Intent `searchTypes`: people-just-moved-jobs, people-just-posted, hiring-signals,
funding-signals, leadership-changes, job-opportunities (Pro), account-activity (Pro).

---

## Social listening

| Tool | R/W | Key params |
|------|-----|-----------|
| `get_social_listening_posts` | R | `limit?`, `minBuyerIntentScore?`, `minBusinessRelevanceScore?`, `sortBy?` |
| `get_social_listening_qualifying_posts` | R | `limit?`, `minIntentScore?`, `minRelevanceScore?` |
| `get_social_listening_engagers` | R | `postUrl?`, `limit?` |
| `get_social_listening_stats` | R | — |
| `get_social_listening_auto_import` | R | — |
| `set_social_listening_auto_import` | W | `enabled`, `autoImportListId?`, `minBuyerIntentScore?`, `minBusinessRelevanceScore?` |
| `trigger_social_listening_auto_import` | W | — ; returns `taskId` |
| `get_social_listening_auto_import_task` | R | `taskId` |

---

## Enrichment

| Tool | R/W | Cost | Key params |
|------|-----|------|-----------|
| `enrich_contact_email` / `enrich_contacts_email_bulk` | W | 1 cr/found | `contactId` / `contactIds[]` (≤500) |
| `enrich_contact_phone` / `enrich_contacts_phone_bulk` | W | 1 cr/found | `contactId` / `contactIds[]` |
| `enrich_profiles` | W | ~0.07 cr/found | `linkedinUrls[]` (≤5000), `confirm?` — call `confirm:false` first for an estimate, relay it, then `confirm:true` |
| `get_enriched_profiles` | R | — | `linkedinUrls?[]`, `missingFields?[]`, `limit?` |
| `get_enrichment_status` / `get_phone_enrichment_status` | R | — | `jobId?` |

---

## Inbox (Unibox) & AI reply/comment approvals

| Tool | R/W | Key params |
|------|-----|-----------|
| `get_unibox` | R | `search?`, `status?` (replied\|unreplied\|all), `includeThreads?`, `limit?` |
| `get_unibox_unread_count` | R | — |
| `sync_unibox` | W | `force?` (pull latest from LinkedIn) |
| `send_unibox_reply` | W | `conversationUrl`, `message` (≤2000) |
| `mark_unibox_thread_read` | W | `conversationUrl` |
| `get_unibox_task_status` | R | `taskId` |
| `get_pending_replies` / `get_pending_replies_count` | R | `status?`, `needsApproval?`, `limit?` |
| `update_pending_reply` | W | `replyId`, `message?` |
| `approve_pending_reply` / `deny_pending_reply` | W | `replyId` |
| `regenerate_pending_reply` / `retry_pending_reply` | W | `replyId`, (`message?`) |
| `get_pending_comments` / `..._count` | R | `status?`, `limit?` |
| `update_/approve_/deny_/retry_pending_comment` | W | `commentId`, (`comment?`) |

---

## LinkedIn sender connection

| Tool | R/W | Key params |
|------|-----|-----------|
| `start_linkedin_connect` | W | `label?`, `country?` — mints a private 2h link for the user to enter cookie/credentials |
| `start_linkedin_update` | W | `connectionId` |
| `get_linkedin_accounts` | R | — |
| `get_linkedin_connection` | R | `connectionId` |
| `get_linkedin_2fa_status` | R | `connectionId?` (health + blockers + fix suggestions) |
| `validate_linkedin_connection` | R | `connectionId?` |
| `reconnect_and_check_linkedin_2fa` | W | `connectionId?` (live login; may resume paused campaigns) |
| `connect_linkedin_with_cookie` / `..._with_credentials` | W | see catalog — prefer `start_linkedin_connect` (privacy-first link) |
| `update_linkedin_cookie` / `refresh_linkedin_cookie` | W | `connectionId`, … |
| `register_/remove_linkedin_totp_seed`, `get_linkedin_totp_code` | W/R | `connectionId?`, `totpSecret?` |

**Prefer `start_linkedin_connect`** — it returns a private link so the user enters
credentials themselves. Don't ask the user to paste a cookie or password into chat.

---

## Account, analytics, tasks

| Tool | R/W | Key params |
|------|-----|-----------|
| `get_account_status` | R | — (plan, credits, limits, LinkedIn senders) |
| `get_billing_summary` | R | — |
| `get_integration_status` | R | — |
| `get_dashboard_summary` | R | — |
| `get_performance_analytics` | R | `rankBy` (connections\|replies\|opportunities\|icp8plus\|icpScore), `groupBy?`, `limit?` |
| `get_tasks` | R | `status?`, `taskType?`, `limit?` |
| `cancel_task` / `retry_task` | W | `taskId` |
| `get_scheduled_sends` | R | `campaignId?`, `limit?` |
| `update_scheduled_send_status` | W | `scheduledSendId`, `status` |
| `preview_withdraw_connections` | R (Pro) | `campaignId?`, `daysOld?` |
| `withdraw_connections` | W! (Pro) | `campaignId?`, `daysOld?`, `confirmWithdraw` (must be true) |

---

## Async job pattern

Several tools kick off background work and return a `runId`/`jobId`/`taskId`. Don't
claim completion — poll the matching status tool and relay what it returns:

- signal agents → `get_agent_run_status`
- discovery → `get_discovery_status`
- enrichment → `get_enrichment_status` / `get_phone_enrichment_status`
- social listening import → `get_social_listening_auto_import_task`
- unibox sync → `get_unibox_task_status`
- generic tasks → `get_tasks`
