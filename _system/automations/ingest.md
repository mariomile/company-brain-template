---
name: Ingest
description: Every evening, pull what is new from the connected sources into Input/, then hand it to triage and minutes
icon: download
when:
  - weekdays 19:00
mode: propose
scope:
  - Input/**
  - _system/sources.md
skill: ingest
cooldown: 1h
enabled: false
tags:
  - type/automation
---

**Load `company-brain:ingest` and run its procedure** for every source in `_system/sources.md` with `status: active`.

- Pull only what changed since the source's `last_sync`. A source whose connector is not available in this run: skip it and name it.
- `propose`: write `_system/reports/proposals/YYYY-MM-DD ingest.md` (frontmatter `status: open`, `owner:` the source owner, `date:`) listing what would land where, ready to apply.
- `act`: write raw material to the source's destination, update `last_sync`, list what needs minutes or triage.

Never pull from a source the table does not list. Never copy content marked confidential at the source into a folder with a wider audience.

## Lessons

- 
