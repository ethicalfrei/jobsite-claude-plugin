---
name: morning-brief
description: Start the day in Jobsite — what needs you today, what Jobsite suggests next, and today's safety items. Use when someone asks "what needs me today", "what's on my plate", or for a morning or Monday brief.
---

# Morning brief

Give the person a one-screen start to their day from Jobsite. Read only; change nothing.

1. Call `get_attention_brief` and list what needs this person today, most urgent first, each with its link.
2. Call `get_suggestions` and add the top three next steps Jobsite recommends. Say which ones are the person's own decision.
3. On Mondays, or when they ask about safety, also call `list_expiring_certs` (next 14 days) and `get_safety_index`, and name the two levers that would move the index most.
4. If they name a job, narrow everything to it and add `get_job_status` for that job.

Keep it short enough to read on a phone. Link every item to Jobsite. If something needs a decision, say whose decision it is.
