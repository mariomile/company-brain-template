# Brain log

Append-only. One line per operation that changed the brain, written by the plugin script and by automations. Greppable: `grep "^## \[" _system/log.md | tail -20`.

Format: `## [YYYY-MM-DD HH:MM] <op> | <title> | <actor>` followed by optional indented lines.
Ops: `init` `capture` `meeting` `decision` `promote` `verify` `triage` `review` `health` `index` `archive` `revert`.

## [{{today}} 09:00] init | brain created from the template | human
## [2026-10-22 08:35] index | regenerated 5 index file(s) | brain-script
## [2026-10-22 08:39] index | regenerated 1 index file(s) | brain-script
## [2026-10-22 18:26] new | decision: Decisions/2026-10-22 Test decision.md | brain-script
## [2026-10-22 18:26] new | project: Active/Projects/Test Project/Test Project.md | brain-script
## [2026-10-22 18:26] new | person: CRM/People/Test Person.md | brain-script
## [2026-10-22 18:26] verify | Knowledge/Company/Product.md verified by [[Ben Okafor]], next review 2027-01-20 | Ben Okafor
## [2026-10-22 18:26] index | regenerated 4 index file(s) | brain-script
## [2026-10-22 18:26] capture | unit test | test
## [2026-10-22 18:26] new | project: Active/Projects/Cadence Project/Cadence Project.md | brain-script
## [2026-10-22 18:26] new | concept: Knowledge/Product/Foo Bar.md | brain-script
## [2026-10-22 18:26] new | decision: Decisions/2026-03-04 No project.md | brain-script
## [2026-10-22 18:26] new | person: CRM/People/No Company.md | brain-script
## [2026-10-22 18:26] ask | what did we decide on pricing? | agent | answered
## [2026-10-22 18:26] ask | What did we decide on pricing | agent | gap
## [2026-10-22 18:26] archive | 14 sample note(s) moved to .archive/ | brain-script
## [2026-10-22 18:27] new | decision: Decisions/2026-10-22 Test decision.md | brain-script
## [2026-10-22 18:27] new | project: Active/Projects/Test Project/Test Project.md | brain-script
## [2026-10-22 18:27] new | person: CRM/People/Test Person.md | brain-script
## [2026-10-22 18:27] verify | Knowledge/Company/Product.md verified by [[Ben Okafor]], next review 2027-01-20 | Ben Okafor
## [2026-10-22 18:27] index | regenerated 4 index file(s) | brain-script
## [2026-10-22 18:27] capture | unit test | test
## [2026-10-22 18:27] new | project: Active/Projects/Cadence Project/Cadence Project.md | brain-script
## [2026-10-22 18:27] new | concept: Knowledge/Product/Foo Bar.md | brain-script
## [2026-10-22 18:27] new | decision: Decisions/2026-03-04 No project.md | brain-script
## [2026-10-22 18:27] new | person: CRM/People/No Company.md | brain-script
## [2026-10-22 18:27] ask | what did we decide on pricing? | agent | answered
## [2026-10-22 18:27] ask | What did we decide on pricing | agent | gap
