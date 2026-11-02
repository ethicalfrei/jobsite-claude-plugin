---
name: safety-week
description: A start-of-week safety brief from Jobsite — open safety items, certifications about to lapse, compliance picture and Safety Index levers. Use for "Monday safety brief", "safety meeting prep" or "who's about to lapse".
---

# Weekly safety brief

1. Call `get_attention_brief` and keep the safety items (inspections, incidents, observations, certifications), ordered by urgency.
2. Call `list_expiring_certs` for the next 14 days and group people by what lapses.
3. Call `get_compliance_stats` for the overall picture.
4. Call `get_safety_index` and name the two levers that would move it most.
5. Offer a toolbox talk for the week's biggest hazard: preview it with `send_toolbox_talk` using `dry_run: true`, and only send it to the crew when the person says so.

One screen, every item linked. Training answers come from Jobsite's training records — say "per Jobsite's training records", never that someone is "certified".
