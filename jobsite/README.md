# Jobsite for Claude

Run your construction or home-services company by talking to Claude. This plugin connects Claude to
[Jobsite](https://jobsitecerts.com) and adds ready-made workflows for the things you do every day: the
morning brief, the weekly safety meeting, an injury's first 24 hours, entering a vendor invoice, pay-run
prep, dispatch wrap-up, a job health check, a field brief from the drawings and specs, a punch and safety
walk, a change order draft, and the daily log with schedule progress.

You ask as yourself, behind your own Jobsite permissions. Claude reads your company's live data and
drafts work for you to finish in Jobsite.

## What's inside

- **The Jobsite connector** (`.mcp.json`): `https://jobsitecerts.com/api/mcp`. You sign in to Jobsite
  and approve the connection the first time you use it (OAuth). No API key or password is stored in the
  plugin.
- **Skills** (`skills/`):

  | Skill | Ask it like |
  |---|---|
  | `morning-brief` | "What needs me today?" |
  | `safety-week` | "Monday safety brief" |
  | `incident-first-24h` | "A laborer cut his hand on rebar and got stitches — is it recordable?" |
  | `invoice-to-bill` | *(share a photo of an invoice)* "Enter this bill." |
  | `pay-run-prep` | "What's due this week and what's on hold?" |
  | `dispatch-wrap` | "Wrap up dispatch for today." |
  | `job-health-check` | "How's the Main St job?" |
  | `field-brief` | "I'm on Main St doing concrete — what do the drawings and specs say?" |
  | `site-walk` | "Punch walk on Elm St: drywall ding by the unit 4 door, guardrail missing on level 3." |
  | `change-order-draft` | "Draft a PCO: the owner added a door in unit 2, $1,850, two days." |
  | `end-of-day-log` | "Write up today's daily log for the Elm St job — framing on level 2 is done." |

## What it will and won't do

- Every change can be previewed first (`dry_run`) and most can be undone (`undo_write`).
- Drafts (bills, estimates, daily logs, change orders, first incident reports) are finished by a person
  in Jobsite. A change order is never submitted or sent from Claude.
- It never pays anyone, runs or releases a pay run, sends anything to a customer, vendor or GC, deletes
  workers, changes permission roles, or overrides certifications.
- Compliance answers (OSHA recordability, who is cleared for a task) are computed by Jobsite from the
  regulation and your training records, not guessed by the model.

## Install

**Claude Code / Cowork**

```
/plugin marketplace add ethicalfrei/jobsite-claude-plugin
/plugin install jobsite@jobsite
```

Then run `/mcp` and sign in to Jobsite when asked. Requires a Jobsite plan that includes integrations.

**Claude (web, desktop and phone):** add the Jobsite connector from Claude's connectors directory, or as
a custom connector with the URL `https://jobsitecerts.com/api/mcp`. Setup guide:
[jobsitecerts.com/mcp](https://jobsitecerts.com/mcp).

## Data handling

This plugin sends data to exactly one place: **Jobsite** (`https://jobsitecerts.com`), through the
connector above, only when Claude calls a Jobsite tool on your behalf. What it sends is the tool's
input (for example, the invoice details Claude read or the question you asked); what comes back is your
company's Jobsite data that your account may see. The skills themselves are instructions only; they
contain no code and send nothing on their own.

- Privacy policy: <https://jobsitecerts.com/privacy>
- Security: <https://jobsitecerts.com/security>
- Support: <support@jobsitecerts.com>

## License

MIT — see [LICENSE](LICENSE).
