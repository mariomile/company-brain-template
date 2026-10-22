---
tags:
  - type/memory
rule: structure-stability
created: {{today}}
---
# Rule: structure stability

**Trigger:** you are about to create, move, rename or remove a folder; add or rename a tag namespace or a `type/*` value; add a frontmatter property; add or change a rule or an automation.

## The test

Structure changes are **decisions**, because every one of them costs every future session. Before touching structure:

1. Is there a decision record in `Decisions/` that says so? If not, write one (`type/decision`, `domain/knowledge`) and stop. The brain owner accepts it.
2. Does the change replace something, or add a container? Adding without removing fails the anti-pattern test in the Blueprint section 7.
3. Dry-run first: list every path, link, view filter and script that the change rewrites. Wikilinks by bare name survive moves; path links and `inFolder()` filters do not.

## Never

- A new folder at the root. The root allowlist is in `_system/brain.config.json`; the guard hook refuses anything else.
- Deleting: archive into `.archive/<same relative path>`.
- Bulk frontmatter rewrites with a YAML parser: unquoted wikilinks break. Insert raw lines.
- A tag namespace that encodes state, stage or an entity name.

## Subfolders inside a project

Free, within `Active/Projects/<Name>/`. They are the project's business and need no decision.
