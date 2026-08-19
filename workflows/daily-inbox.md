# Workflow: Daily inbox (10 minutes)

Run by the **Inbox Manager**. Needs LinkedNav connected.

1. `sync_unibox` → `get_unibox_unread_count`. Nothing new? Done.
2. `get_unibox` (`status: 'unreplied'`, `includeThreads: true`). Triage: hot / warm /
   not-now / wrong-person / objection.
3. For each hot & warm thread: draft per `reference/message-frameworks.md` →
   `send_unibox_reply` → `mark_unibox_thread_read`.
4. Clear AI drafts: `get_pending_replies` (`needsApproval: true`) → read each →
   `approve_pending_reply` / `update_pending_reply` then approve / `deny` / `regenerate`.
   Comment campaigns: `get_pending_comments` → approve/deny.
5. Any real opportunity → `update_contact` (`isOpportunity: true`, `notes`).
6. Report: replies handled, drafts approved, new opportunities, anyone waiting on the user.

Rule: read before approving; every reply specific to its thread; relay real content only.
