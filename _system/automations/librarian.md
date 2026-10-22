---
name: Librarian
description: Every Monday, rebuild the indices and fix what is mechanical; count the rest
icon: library
when:
  - weekly Mon 08:00
mode: act
scope:
  - _system/indices/**
  - _system/reports/health/**
  - _system/memory/agents/brain-librarian.md
agent: brain-librarian
cooldown: 6h
mcp: []
enabled: false
tags:
  - type/automation
---

The instructions are in `_system/agents/brain-librarian/AGENT.md`. The scope is deliberately narrow: indices and the health report. Tag fixes in note frontmatter happen only in an interactive session or after the brain owner widens the scope by decision.
