---
name: pay-run-prep
description: Get vendor bills ready for the next pay run — what's due, what's on hold and why, and what still needs approval. Use for "what do we owe", "pay run", "what's holding up this bill".
---

# Pay run prep

1. Call `ap_payables_overview`: summarize what's due by week, the bills on hold and why, and the bills still waiting on approval.
2. For each bill on hold or flagged as a possible duplicate, call `ap_get_bill` and say exactly what would clear it.
3. If one of the approvals is the person's own step, they can decide it with `ap_decide_approval` — it asks them every time and cannot be undone, so confirm the bill and the decision first.

This is preparation only. The connector cannot pay, schedule or export a payment, or release a pay run; that happens in Jobsite.
