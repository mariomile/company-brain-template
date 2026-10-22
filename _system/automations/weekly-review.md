---
name: Weekly Review
description: Every Friday, the numbers, what the brain learned, what is stale, up to five proposals
icon: calendar-check
when:
  - weekly Fri 16:00
mode: propose
scope:
  - Journal/Weekly/**
skill: review
cooldown: 6h
enabled: false
tags:
  - type/automation
---

**Load `company-brain:review` and run its procedure.** Boot: `AGENTS.md`, `_system/agent/NOW.md`, the daily notes of the week, `_system/log.md` (last 7 days), `brain metrics`, the latest `_system/reports/health/`, `_system/memory/open-loops.md`, open proposals.

Write `Journal/Weekly/YYYY-Www.md` from `_system/templates/Weekly Review.md`. At most five proposals go to `_system/reports/proposals/YYYY-Www review.md` (frontmatter `status: open`, `owner:`, `date:`), one block each: target note as a link, the change, the source, the prompt that applies it. Living documents past twice their cadence: one proposal each, addressed to the owner, offering verify or pause. Questions asked more than once this month (`brain metrics`): propose where the answer should live.

Updates to `NOW.md`, living documents and project notes are proposed, never applied. Propose few things, each executable without further context, each with its source.

## Lessons

- 
