# CLAUDE.md: Claude adapter for the {{company}} brain

The universal contract is `AGENTS.md`, imported below. This file holds only what
is specific to Claude Code, Cowork and Exo; it duplicates no structure, memory
rule or precedence.

## Entry point

- **With the `company-brain` plugin installed:** the session-start hook injects
  the `using-company-brain` skill and a briefing (stale documents, inbox,
  loops due). Do not re-read what it injected. Load just-in-time only the rule
  whose trigger matches, the specialist you were asked to be, and the note of
  the project you work on.
- **Without the plugin (cold boot):** run the boot in `AGENTS.md`.
- **Inside Exo:** the kernel (`SOUL`, `ORG`, `NOW`) is pre-injected. The
  surface is Exo; keep that identity.

## Boundaries

- `.claude/` is a runtime surface: change it only when a person asks.
- Files in `.claude/agents/` are adapters. The canonical agent lives in
  `_system/agents/<slug>/`; never duplicate its prompt, memory or policy.
- Subagents do not call each other unless the bundle's `can_call` allows it.
  The coordinator synthesizes.

## Tooling

- Prefer Obsidian-aware tools when available: they preserve wikilinks, tags and
  frontmatter. Otherwise plain file tools are fine; the guard hook enforces the
  root, archive, read-only and secrets rules on every write.
- Search: the plugin's `brain` script for structure, `rg` for content.

@AGENTS.md
