---
name: Librarian
description: Every Monday, rebuild the indices, archive closed loops, write the health report; fix only what is mechanical
icon: library
when:
  - weekly Mon 08:00
mode: act
scope:
  - _system/indices/**
  - _system/reports/health/**
  - _system/memory/open-loops.md
  - _system/memory/open-loops-closed.md
skill: maintain
cooldown: 6h
enabled: false
tags:
  - type/automation
---

**Load `company-brain:maintain` and run its procedure.** Boot: `_system/brain-context.md`, `_system/_tags.md`, `_system/brain.config.json`.

1. `brain index --write`.
2. Move every `status: closed` block from `_system/memory/open-loops.md` to the end of `_system/memory/open-loops-closed.md`, unchanged.
3. `brain health --json`: write `_system/reports/health/YYYY-Www.md` with the summary table and at most three example paths per finding.
4. Nothing else is fixed in this run: tag and link repairs in notes need a wider scope, which is a decision of the brain owner. Count them in the report with the owner of each note.

You do not touch content. You keep the maps true and count what you do not fix. Use the script, never a hand-written grep: the script separates frontmatter from body.

## Lessons

- 
