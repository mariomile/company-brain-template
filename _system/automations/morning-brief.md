---
name: Morning Brief
description: Every weekday morning, what is on today, what is open, what is stale
icon: sun
when:
  - daily 07:30
mode: report
cooldown: 30m
mcp: []
enabled: false
tags:
  - type/automation
---

Prepare today's brief for the team, in the brain's language, readable on a phone: short lines, lists, at most 40 lines. Write it to `_system/reports/briefs/YYYY-MM-DD.md` and, if a daily note exists for today, append one line under `## Agents`.

1. **Today:** meetings on the calendar if a calendar source is connected; for each, one line of context from the project note and the last minutes in `Input/Meetings/`. If no calendar is connected, say so in one line.
2. **Open:** loops in `_system/memory/open-loops.md` with `resurface` today or past, and `due` within 3 days, grouped by owner.
3. **Stale:** living documents past `review_due`, with owner (the plugin's `brain stale` gives the list).
4. **To process:** meetings synced yesterday without minutes, files in `_inbox/`, `_system/memory/inbox/` not empty.
5. **Priorities:** the top three from `_system/agent/NOW.md`, one line each.

If a source is unavailable, say so in one line. Never invent.
