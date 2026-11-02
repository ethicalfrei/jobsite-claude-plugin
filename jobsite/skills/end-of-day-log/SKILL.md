---
name: end-of-day-log
description: Turn a spoken or typed end-of-day recap (and photos) into the job's daily log narrative in Jobsite, for a person to review and sign, plus the day's schedule progress and safety observations. Use for "write up today", "daily log", "end of day report".
---

# End-of-day daily log

1. Ask which job and which day if it isn't clear. Gather what happened: work done, crews and trades on site, deliveries, inspections, delays and their causes, weather, and safety observations.
2. Call `draft_daily_log` with `dry_run: true`. It returns what it would do, not the text: whether it starts
   that day's log or redrafts it. If it says "Redraft", tell the person the log's current unsigned narrative
   will be replaced, and ask before going on.
3. When the person agrees, call it for real. Show them the narrative it returns, with the log's link and the
   write id, and ask whether it reads right.
4. If they don't like it, call `undo_write` with that write id. That puts the earlier narrative back.
5. Offer the two follow-ups the recap usually holds, each previewed with `dry_run: true` first:
   - **Schedule progress** ("framing on level 2 is done"): `update_schedule_task` with the job and the task
     name as the schedule shows it, and `mark` (`started` / `complete`) or a percent. If it moves dates, read
     back any later tasks the preview says would now overlap: those are cascaded in Jobsite's schedule, not
     here.
   - **Safety observations** from the day: `log_safety_observation`, one per observation.
   Make each one only when the person agrees, and give its link and write id.

The log stays unsigned. A person reviews and signs it in Jobsite.
