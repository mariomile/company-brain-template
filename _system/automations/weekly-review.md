---
name: Weekly Review
description: Every Friday, the numbers, what the brain learned, what is stale, up to 5 proposals
icon: calendar-check
when:
  - weekly Fri 16:00
mode: propose
scope:
  - Journal/Weekly/**
  - _system/reports/proposals/**
agent: brain-curator
cooldown: 6h
mcp: []
enabled: false
tags:
  - type/automation
---

The instructions are in `_system/agents/brain-curator/AGENT.md`. The only writes are the weekly note and the proposals file. Updates to `NOW.md`, living documents and project notes are proposed, never applied by this run.
