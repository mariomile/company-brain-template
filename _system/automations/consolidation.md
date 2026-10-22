---
name: Consolidation
description: Every night, move what the memory inbox captured into canonical notes, deduplicate, archive closed loops, run the guard
icon: sprout
when:
  - daily 06:00
mode: act
scope:
  - _system/memory/inbox/**
  - _system/memory/open-loops.md
  - .archive/_system/**
  - Knowledge/**
  - CRM/**
  - Active/Projects/**
cooldown: 6h
mcp: []
enabled: false
tags:
  - type/automation
---

You are the nightly consolidation of the brain's memory. During the day agents capture facts; those without an obvious home sit in `_system/memory/inbox/YYYY-MM-DD.md`.

1. For each line in the inbox files: find the canonical note (`AGENTS.md`, section Memory, says where). If the fact is already there: drop the line. If it is new: append it as a dated fact line. If it changes an existing fact: update with the dated trace. If you cannot place it with confidence: leave it and list it in the report.
2. Living documents: never edit the body. Facts for them go to `_system/reports/proposals/YYYY-MM-DD consolidation.md` with the target note and the line to add.
3. `_system/memory/open-loops.md`: move every `status: closed` block to `.archive/_system/open-loops-closed.md`.
4. Run `brain health --json` and write `_system/reports/health/YYYY-MM-DD.md` with the summary. Do not fix anything the script did not mark as safe.
5. Delete inbox files you emptied (this is the one place deletion is allowed: the content moved, the file was transit).
6. Append one line to `_system/log.md` and one under `## Agents` in today's daily note.

Commit message: `brain: consolidation YYYY-MM-DD`.
