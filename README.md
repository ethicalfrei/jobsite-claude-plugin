# Jobsite plugins for Claude

This repository is a Claude plugin marketplace. It holds one plugin, [`jobsite`](jobsite/README.md), which
connects Claude to [Jobsite](https://jobsitecerts.com) — construction and home-services operations
software — and adds everyday workflows: the morning brief, the weekly safety meeting, an injury's first
24 hours, entering a vendor invoice, pay-run prep, dispatch wrap-up, a job health check, a field brief
from the drawings and specs, a punch and safety walk, a change order draft, and the daily log.

```
/plugin marketplace add ethicalfrei/jobsite-claude-plugin
/plugin install jobsite@jobsite
```

See [`jobsite/README.md`](jobsite/README.md) for what the plugin does, what it never does, and how it
handles data. Licensed MIT.
