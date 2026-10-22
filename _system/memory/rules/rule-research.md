---
tags:
  - type/memory
rule: research
created: {{today}}
---
# Rule: research

**Trigger:** research, analysis, synthesis, reading a URL or a document.

## Order of sources

1. **The brain.** `brain search`-style lookup: the indices first, then `rg` on content, then follow wikilinks from the hits. Living documents and decisions outrank inputs; newer `last_verified` outranks older.
2. **Connected sources** (mail, chat, tickets, meeting tools, analytics), only if the brain does not answer and only the ones this session exposes.
3. **The web**, for external facts, with recent and authoritative sources.

## Output

- Answer first, in one to three lines. Then the details.
- Every claim carries its source: `[[note]]` for the brain, "email from X on DD/MM", "ticket #N", a URL for the web.
- Two sources contradict: show both, say which wins and why (specificity, verification date, authority), and write the conflict into the more canonical note as a dated line.
- Close with **Gaps**: what the brain does not know about this question, what is stale, what was web-only. A gap that matters becomes an open loop or a proposal.

## After

- An answer that took external sources and will be needed again becomes a note: `Input/Research/` for the material, `Knowledge/<Domain>/` for the distilled concept, linked both ways.
- A decision or commitment that surfaced and is not recorded: propose recording it.
