---
name: dispatch-wrap
description: End-of-day dispatch review for home services — today's exceptions, tomorrow's open urgent calls, and overdue customer invoices. Use for "wrap up dispatch", "what's late today", "who owes us".
---

# Dispatch wrap-up

1. Call `service_dispatch_board` for the day and list the exceptions: unassigned, late, held bookings and no-access visits.
2. For each exception, call `service_get_call` and say what the office should do next.
3. Call `service_dispatch_board` for tomorrow and point out urgent calls that are still unscheduled. If the person wants, assign technicians with `service_assign_technicians` or book a visit with `service_schedule_visit` — preview with `dry_run: true` first.
4. Call `service_receivables_overview` and list invoices more than 30 days past due.

Estimates, visit notices and invoices are sent to customers by a person from Jobsite; this skill never sends anything.
