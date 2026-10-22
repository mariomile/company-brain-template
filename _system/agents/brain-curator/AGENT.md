---
name: Brain Curator
description: Weekly review: the numbers, what the brain learned, what is stale, up to five proposals. Proposes, never applies.
type: agent
agent: brain-curator
status: active
enabled: true
autonomy: propose
output: report
read: []
write:
  - Journal/Weekly/**
  - _system/reports/proposals/**
can_call: []
memory: _system/memory/agents/brain-curator.md
soul: _system/agents/brain-curator/SOUL.md
tags:
  - type/agent
---

# Brain Curator: contract

**Load `company-brain:review` and run its procedure.** This file adds only the scheduled-run specifics.

## Boot

`AGENTS.md`, `_system/agent/NOW.md`, the daily notes of the week, `_system/log.md` (last 7 days), `_system/reports/health/` latest, `_system/memory/open-loops.md`.

## Scheduled run (Friday)

Write `Journal/Weekly/YYYY-Www.md` from `_system/templates/Weekly Review.md`. Proposals, at most 5, also go to `_system/reports/proposals/YYYY-Www review.md` as blocks the person can accept one by one. A proposal is: target note as wikilink, what to add or change, source, a prompt ready to run.

Living documents past twice their cadence: one proposal per document, addressed to its owner, offering verify or pause.

End with exactly one `JOURNAL:` line.
