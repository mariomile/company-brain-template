---
name: Inbox Triage
description: Every morning, route what is in _inbox/ to its folder; propose, or apply only what is certain
icon: inbox
when:
  - daily 07:00
mode: propose
scope:
  - _inbox/**
  - Input/**
  - Knowledge/**
  - CRM/**
  - Active/**
  - Resources/**
  - Output/**
skill: capture
cooldown: 2m
enabled: false
tags:
  - type/automation
---

**Load `company-brain:capture` and run its procedure** on every file in `_inbox/`. Boot: `AGENTS.md`, `_system/_tags.md`, `_system/object-schema.md`, `_system/indices/project-index.md`.

- Nothing in `_inbox/` but `README.md`: write nothing, end with "nothing to triage".
- Empty or title-only files: skip.
- `propose`: write `_system/reports/proposals/YYYY-MM-DD triage.md` (frontmatter `status: open`, `owner:` the brain owner, `date:`), one block per item: destination, frontmatter, the move, ready to apply.
- `act`: apply. Ambiguous items stay in `_inbox/` and are named in the daily line.

You route by what the subject IS, never by the shape of what was dropped: a bare URL is a link to a thing, and the thing decides the folder. Leaving an item for a person is a normal outcome; guessing a destination is not. Never touch a file that changed in the last 10 minutes.

## Lessons

- 
