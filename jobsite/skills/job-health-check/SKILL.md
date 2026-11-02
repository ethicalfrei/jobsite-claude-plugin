---
name: job-health-check
description: One job's health in Jobsite — status, money, open RFIs, submittals and punch, and what needs a decision this week. Use for "how's the Main St job", "job status", "where are we on budget".
---

# Job health check

1. Find the job with `list_jobs`, then call `get_job_status`.
2. Call `get_financial_summary` for it: budget against cost, change orders, and what's owed both ways.
3. Call `list_rfis`, `list_submittals` and `list_punch` for the job and count what's overdue.
4. End with the three things that most need a decision this week, each linked to Jobsite.

Read only; change nothing.
