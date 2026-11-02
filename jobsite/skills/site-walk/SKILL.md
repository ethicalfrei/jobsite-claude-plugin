---
name: site-walk
description: Turn a walk of the job into punch items and safety observations in Jobsite, one by one, each previewed first and undoable. Use for "punch walk", "add these to the punch list", "log a safety observation", "guardrail missing on level 3".
---

# Site walk: punch and safety observations

1. Find the job with `list_jobs` if it isn't clear. Take what the person reports, one item at a time, and sort
   each into one of two kinds:
   - **Something to fix before closeout** (a ding, a missing cover plate, a paint touch-up): a punch item.
   - **Something about safety** (a hazard, a near miss, an unsafe act, or a safe act worth recognizing): a
     safety observation. If someone was actually hurt, stop and use the `incident-first-24h` skill instead.
2. For a punch item, call `create_punch_item` with `dry_run: true`: the description in the person's words, the
   location, and the severity (life-safety only when it truly is). To assign a crew member, find them with
   `list_workers`. If they name a subcontractor, say the item will be created unassigned with a link: assigning
   a sub emails them, and that is a person's step in Jobsite.
3. For an observation, call `log_safety_observation` with `dry_run: true` and the observation type, what was
   seen and where. A hazard, near miss or unsafe act goes to the safety lead to triage; a safe act is recorded
   as recognized.
4. Read the preview back in one line and make the item for real when the person agrees. Batch the confirmation
   when they list several ("add all five?").
5. End with a list of what was made, each with its link and write id. Photos are added on each item in
   Jobsite. If one is wrong, call `undo_write` with its write id; it works while nobody has worked the item.

Never invent an item the person didn't say. If a location or job is ambiguous, ask.
