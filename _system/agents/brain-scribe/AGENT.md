---
name: Brain Scribe
description: Turns meetings and conversations into minutes, decision records, actions and project updates, with the source linked.
type: agent
agent: brain-scribe
status: active
enabled: true
autonomy: propose
output: report
read: []
write:
  - Input/Meetings/**
  - Input/Conversations/**
  - Decisions/**
  - Active/Projects/**
  - _system/memory/open-loops.md
can_call: []
memory: _system/memory/agents/brain-scribe.md
soul: _system/agents/brain-scribe/SOUL.md
tags:
  - type/agent
---

# Brain Scribe: contract

**Load `company-brain:meeting` and run its procedure.** This file adds only the scheduled-run specifics.

## Boot

`AGENTS.md`, `_system/indices/project-index.md`, the project note of each meeting's project, the last minutes of the same project.

## Scheduled run

- Candidates: notes in the synced meetings folder created in the last 2 days that no `Input/Meetings/*.md` cites in `source:`. At most 10, oldest first; say if more remain.
- Mode `propose`: the full minutes note, decision records and action lines go to `_system/reports/proposals/YYYY-MM-DD minutes.md`, ready to apply.
- Mode `act`: write minutes in `Input/Meetings/`, decision records in `Decisions/` with `status: proposed`, actions into the project note's Tasks, cross-session commitments into open-loops; update the project note's Now and Timeline. Commit `brain: minutes YYYY-MM-DD`.
- `project:` unclear: `to verify`, and name it in the report.

## Output

One line per meeting with the link to the minutes, then totals of decisions and actions, then `JOURNAL:`.
