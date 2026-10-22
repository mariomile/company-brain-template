---
tags:
  - type/memory
rule: writing-notes
created: {{today}}
---
# Rule: writing notes in the brain

**Trigger:** every time you write text in the brain or create a file.

## Frontmatter

- Every note: `tags` with 1 to 4 tags from `_system/_tags.md`, including `type/*`.
- The type's properties from `_system/object-schema.md`; nothing else in frontmatter.
- Living documents and project notes: `owner`, `review_due`, `last_verified`.
- Wikilinks in frontmatter are quoted: `up: "[[Note]]"`.
- Normalize on touch: when you edit a note with a non-canonical frontmatter, fix the shape; never run bulk passes.

## Body

- Wikilink on the **first mention** of a person, company, project, decision or concept, inline, never in a trailer list. `[[Note|different text]]` when the text differs from the file name.
- Facts: one per line, source and date at the end: `- <fact> [source: <note or URL or "chat YYYY-MM-DD">; since: YYYY-MM-DD]`.
- A changed fact: `<new> (since YYYY-MM-DD; before: <old>)`, same line, replaced.
- A status that updates: one line, replaced; never one line per check.
- Entity notes (people, companies, projects): **current truth above, timeline below.** The top sections say what is true now; `## Timeline` lists dated events, newest first.
- No em-dashes. Short sentences. Bullets over paragraphs.
- Never rewrite or remove text a person wrote. Add, or update with a dated trace.

## Naming

- Spaces, not hyphens (`Onboarding Redesign.md`). Hyphens only inside proper names.
- Dated notes start with the date: `2026-10-14 Weekly product sync.md`.
- Daily: `Journal/Daily/YYYY-MM-DD.md`. Weekly: `Journal/Weekly/YYYY-Www.md`.

## When you create a file

Open your reply with the link, before the analysis:

```
📄 **Created:** [[path/file]]: what it contains
```

Several files: a list in the same form. Then append one line to `_system/log.md`.
