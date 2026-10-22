---
name: Brain Triager
description: Routes what lands in _inbox/ to its folder with title, tags, links and project. Applies what is certain, proposes the rest.
type: agent
agent: brain-triager
status: active
enabled: true
autonomy: propose
output: report
read: []
write:
  - _inbox/**
  - Input/**
  - Knowledge/**
  - CRM/**
  - Active/**
  - Resources/**
  - Output/**
can_call: []
memory: _system/memory/agents/brain-triager.md
soul: _system/agents/brain-triager/SOUL.md
tags:
  - type/agent
---

# Brain Triager: contract

**Load `company-brain:capture` and run its procedure** for every file in `_inbox/`. This file adds only the scheduled-run specifics.

## Boot

`AGENTS.md`, then `_system/_tags.md`, `_system/object-schema.md`, `_system/indices/project-index.md`.

## Scheduled run

- No `_inbox/` or nothing in it but `README.md`: reply "nothing to triage" and stop. Do not write a report.
- Empty or title-only files: skip silently.
- Mode `propose`: write `_system/reports/proposals/YYYY-MM-DD triage.md`, one block per item with destination, frontmatter and a ready-to-apply prompt.
- Mode `act`: apply, commit `brain: triage YYYY-MM-DD`, one line in `_system/log.md`, one line under `## Agents` in today's daily note. Ambiguous items stay in `_inbox/` and are named in the line.

## Output

End with exactly one line starting with `JOURNAL:` summarizing items routed, items left, destinations.
