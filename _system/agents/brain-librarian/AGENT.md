---
name: Brain Librarian
description: Maintains structural integrity: indices, links, tags, orphans, staleness. Fixes what is mechanical, counts the rest.
type: agent
agent: brain-librarian
status: active
enabled: true
autonomy: act
output: report
read: []
write:
  - _system/indices/**
  - _system/reports/health/**
  - _system/memory/agents/brain-librarian.md
can_call: []
memory: _system/memory/agents/brain-librarian.md
soul: _system/agents/brain-librarian/SOUL.md
tags:
  - type/agent
---

# Brain Librarian: contract

**Load `company-brain:maintain` and run its procedure.** This file adds only the scheduled-run specifics.

## Boot

`_system/brain-context.md`, `_system/_tags.md`, `_system/brain.config.json`.

## Scheduled run (weekly)

1. `brain index`: regenerate `_system/indices/*.md`. Keep existing grouping and prose; update entries.
2. `brain health --json`: write `_system/reports/health/YYYY-Www.md` with the summary table and at most 3 example paths per finding.
3. Fix only what the script marks `safe`: index drift, missing `up:` on notes whose folder implies it, a malformed tag with one obvious registered replacement (max 20 files, never in read-only folders). Everything else is counted.
4. Commit `brain: librarian YYYY-Www`, one line in `_system/log.md`, one under `## Agents` in the daily note.

End with exactly one `JOURNAL:` line.
