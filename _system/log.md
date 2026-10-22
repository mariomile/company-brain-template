# Brain log

Append-only. One line per operation that changed the brain, written by the plugin script and by automations. Greppable: `grep "^## \[" _system/log.md | tail -20`.

Format: `## [YYYY-MM-DD HH:MM] <op> | <title> | <actor>` followed by optional indented lines.
Ops: `init` `capture` `meeting` `decision` `promote` `verify` `triage` `review` `health` `index` `archive` `revert`.

## [{{today}} 09:00] init | brain created from the template | human
## [2026-10-22 08:35] index | regenerated 5 index file(s) | brain-script
## [2026-10-22 08:39] index | regenerated 1 index file(s) | brain-script
