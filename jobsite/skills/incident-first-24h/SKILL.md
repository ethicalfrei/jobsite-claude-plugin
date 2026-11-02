---
name: incident-first-24h
description: Walk an injury or near miss through Jobsite's OSHA 1904 recordability check, with the rule text and any report-to-OSHA deadline, then record it in Jobsite with its photos — a first report for a near miss or first-aid case, or a confirmed filing for anything more. Use when someone describes a jobsite injury, asks "is this recordable" or "do I have to report this to OSHA".
---

# Incident: the first 24 hours

1. Get what happened, to whom (role, not name), and the treatment given. If something is missing, ask.
2. Call `osha_recordability_check` with those facts. If it returns questions, ask them one at a time and call it again with the answers.
3. When it decides, give the proposed OSHA 300 classification, the exact rule text it rests on, and any report-to-OSHA deadline with the time left. Lead with the deadline if there is one.
4. If they ask about a rule it cites, quote it with `search_law_corpus`.
5. Check `list_incidents` so you don't record the same event twice.
6. **A near miss or a first-aid case:** offer to record the first report. Call `report_incident` with
   `dry_run: true` (what happened, where, the worker if one was involved, and the care given), read it back,
   and record it when the person agrees. For when it happened, give how many minutes ago ("an hour ago" is
   60), or leave the time out if it just happened; don't make up a clock time. If they showed you photos of the
   scene or the injury, pass them in photos (the image itself, never a link). Give its link and write id. A
   person finishes it in Jobsite with witnesses and the investigation. `undo_write` removes it, with its photos,
   while nobody has touched it.
7. **Anything beyond first aid** (medical treatment, days away, restricted duty, hospitalization, a death): lead
   with the report-to-OSHA deadline if there is one, then offer to file it with `report_serious_incident`.
   - Ask first whether the worker was admitted to a hospital as an in-patient, and whether there was an
     amputation or loss of an eye; pass the recordability answers you already have.
   - Its first call files nothing: it returns every consequence filing has in Jobsite (the refresher training
     assigned and its due date, a training hold at serious, the recordability outcome, any OSHA deadline) and a
     confirm token. Tell the person all of it, in plain words, and ask whether to file.
   - Only on their yes, call it again with the same arguments and confirm set to that token. If anything changes
     (the severity, the worker, a photo), it gives a new statement to read back first.
   - It can't be undone from here, it never reports to OSHA for them, and the OSHA classification is set on the
     incident in Jobsite by someone who manages incidents. Give its link.

Jobsite makes the determination from the regulation. Never guess a classification yourself and never present this as legal advice.
