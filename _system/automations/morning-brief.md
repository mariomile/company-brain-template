---
name: Morning Brief
description: Every weekday morning, what is on today, what is open, what is stale
icon: sun
when:
  - weekdays 07:30
mode: report
scope: []
skill: brief
cooldown: 30m
enabled: false
tags:
  - type/automation
---

**Load `company-brain:brief` and run its procedure.** Write the brief to `_system/reports/briefs/YYYY-MM-DD.md`, in the brain's language, readable on a phone: short lines, at most 40.

1. **Today:** meetings on the calendar if a calendar source is connected; one line of context each from the project note and the last minutes. No calendar connected: say so in one line.
2. **Open:** loops in `_system/memory/open-loops.md` resurfacing today or due within 3 days, grouped by owner.
3. **Stale:** living documents past `review_due`, with owner (`brain stale`).
4. **Waiting for a person:** proposals in `_system/reports/proposals/` with `status: open`, decisions `proposed`, files in `_inbox/`, meetings synced yesterday without minutes.
5. **Priorities:** the top three from `_system/agent/NOW.md`.

If a source is unavailable, say so in one line. Never invent.

## Lessons

- 
