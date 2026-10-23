# CLAUDE.md: Claude adapter for the {{company}} brain

The universal contract is `AGENTS.md`, imported below. This file holds only what
is specific to Claude Code, Cowork and Exo; it duplicates no structure, memory
rule or precedence.

## Entry point

- **First session, or the briefing says `Setup: N step(s) left`:** offer
  `/company-brain:setup` before other work. It walks every step: where the
  brain lives (this machine or GitHub), onboarding, input sources, routines,
  owners, health. Re-running it skips what is done.
- **With the `company-brain` plugin installed:** the session-start hook injects
  the `using-company-brain` skill and a briefing (stale documents, inbox,
  loops due, proposals waiting). Do not re-read what it injected. Load
  just-in-time only the rule whose trigger matches, your automation file on a
  scheduled run, and the note of the project you work on.
- **Without the plugin (cold boot):** run the boot in `AGENTS.md`.
- **Inside Exo:** the kernel (`SOUL`, `ORG`, `NOW`) is pre-injected. The
  surface is Exo; keep that identity.

## Boundaries

- `.claude/` is a runtime surface: change it only when a person asks.
- The plugin's agents are adapters over its skills; a scheduled role is its
  automation file. Never copy a prompt, a policy or a memory into a second place.
- Subagents do not call each other. The coordinator synthesizes.

## Tooling

- Prefer Obsidian-aware tools when available: they preserve wikilinks, tags and
  frontmatter. Otherwise plain file tools are fine; the guard hook enforces the
  root, archive, read-only and secrets rules on every Write and Edit. It does
  not see shell commands: never use the shell to get around it.
- Search: the plugin's `brain` script for structure, `rg` for content.

@AGENTS.md
