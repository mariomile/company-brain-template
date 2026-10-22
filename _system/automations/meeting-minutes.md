---
name: Meeting Minutes
description: Every evening, turn synced meetings without minutes into minutes, decisions and actions
icon: file-text
when:
  - weekdays 18:30
mode: propose
scope:
  - Input/Meetings/*.md
  - Decisions/**
  - Active/Projects/**
  - _system/memory/open-loops.md
skill: meeting
cooldown: 1h
enabled: false
tags:
  - type/automation
---

**Load `company-brain:meeting` and run its procedure.** Boot: `AGENTS.md`, `_system/indices/project-index.md`, then per meeting the project note and the last minutes of the same project.

- Candidates: transcripts in the synced folders (`readonly` in `_system/brain.config.json`) from the last 2 days that no `Input/Meetings/*.md` cites in `source:`. At most 10, oldest first; say how many remain.
- `propose`: the minutes, the decision records and the action lines go to `_system/reports/proposals/YYYY-MM-DD minutes.md` (frontmatter `status: open`, `owner:` the meeting's project owner, `date:`), ready to apply.
- `act`: minutes in `Input/Meetings/`, decisions in `Decisions/` with `status: proposed`, actions in the project note's tasks, commitments across sessions in open loops; update the project's Now and Timeline.
- `project:` unclear: `to verify`, named in the report.

A decision is something that changes what people do; an opinion is not. An action without an owner is a wish. Write what was said, attributed; never fill a silence in the transcript with what would have made sense. One meeting, one note.

## Lessons

- 
