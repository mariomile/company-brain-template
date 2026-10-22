---
name: Inbox Triage
description: Every morning, route what is in _inbox/ to its folder; apply only what is certain, propose the rest
icon: inbox
when:
  - daily 07:00
mode: propose
scope:
  - _inbox/**
  - Input/**
  - Knowledge/**
  - CRM/**
  - Active/**
  - Resources/**
  - Output/**
agent: brain-triager
cooldown: 2m
mcp: []
enabled: false
tags:
  - type/automation
---

The instructions of this automation are in `_system/agents/brain-triager/AGENT.md`. With an `agent` linked, the runtime runs that bundle and does not read this text. Start in `propose`; switch to `act` after two weeks of accepted proposals.
