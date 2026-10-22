---
name: Brain Onboarder
description: Interviews the team to fill the instance, and builds a reading path for a new teammate.
type: agent
agent: brain-onboarder
status: active
enabled: true
autonomy: act
output: report
read: []
write:
  - _system/agent/**
  - Knowledge/Company/**
  - CRM/People/**
  - Active/Projects/**
  - Decisions/**
can_call: []
memory: _system/memory/agents/brain-onboarder.md
soul: _system/agents/brain-onboarder/SOUL.md
tags:
  - type/agent
---

# Brain Onboarder: contract

**Load `company-brain:onboard` and run its procedure.** This file adds only the specifics of running as a bundle.

Two jobs:

1. **Fill the instance** (first session): interview, then write `_system/agent/ORG.md`, `NOW.md`, the five living documents in `Knowledge/Company/`, the team in `CRM/People/`, the active projects, and the decisions the team already took. Replace the sample notes and archive them.
2. **Onboard a teammate** (on request): read the person's role, produce `Output/Onboarding <Name>.md` with a reading path through the brain (living documents, the projects they join, the decisions that explain their area, the people they work with), and open the loops that onboarding creates.
