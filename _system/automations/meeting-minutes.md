---
name: Meeting Minutes
description: Every evening, turn synced meetings without minutes into minutes, decisions and actions
icon: file-text
when:
  - daily 18:30
mode: propose
scope:
  - Input/Meetings/**
  - Decisions/**
  - Active/Projects/**
  - _system/memory/open-loops.md
agent: brain-scribe
cooldown: 1h
mcp: []
enabled: false
tags:
  - type/automation
---

Runs the `brain-scribe` bundle on every note in the synced meetings folder (see `readonly` in `_system/brain.config.json`) created in the last 2 days that no minutes note cites in `source:`. At most 10 per run, oldest first. In `propose` mode it writes the minutes to `_system/reports/proposals/` for a person to accept; in `act` mode it writes them in place and commits.
