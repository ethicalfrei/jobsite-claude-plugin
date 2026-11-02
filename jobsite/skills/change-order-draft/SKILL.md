---
name: change-order-draft
description: Draft a change order (PCO or COR) in Jobsite from a field change — the reason, the schedule impact and the cost lines — for a person to review and send. Use for "write up a change order", "the owner added a door", "PCO for the extra footing".
---

# Change order draft

1. Find the job with `list_jobs`. Ask what changed and why, who asked for it, the days it adds (or saves), and
   the cost lines: a description, the dollars (negative for a credit) and the cost code as Jobsite shows it
   ("09 21 16"). Don't invent prices; if a line has no number yet, ask for it or leave that line out.
2. To check the job's money first, call `get_financial_summary`; `list_change_orders` shows the change orders
   it already has, so you don't draft a duplicate.
3. Call `draft_change_order` with `dry_run: true`. The job's one owner contract is used unless the person names
   a subcontract. Read back the title, total, days and lines.
4. When the person agrees, call it for real and give the change order's number, link and write id.
5. If it's wrong, call `undo_write` with that write id. That voids the draft while it is still a draft.

It stays a draft: nothing is submitted, approved or sent to the owner or GC, and no budget or contract value
changes. A person reviews and sends it from Jobsite. A supplier PO's change order is drafted in Jobsite.
