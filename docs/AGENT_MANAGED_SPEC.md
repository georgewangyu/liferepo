---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/docs/AGENT_MANAGED_SPEC"
doc_type: "docs_doc"
doc_status: "active"
title: "agent-managed: Living Knowledge Wiki"
description: "Spec for the agent-managed/ directory in the private repo — a canonical synthesis layer maintained by the AI."
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:knowledge"
  - "visibility:public"
  - "type:docs_doc"
---
# agent-managed: Living Knowledge Wiki

## What it is

`agent-managed/` is a directory in your private repo where the AI maintains
a living knowledge wiki. It is distinct from `journal/` (chronological record)
and `memory/` (compact structured facts). It occupies the middle layer:
synthesized, cross-session understanding of recurring topics.

Think of it as an encyclopedia that compounds over time. Each session that
produces durable insight updates the relevant topic pages. Future sessions read
the wiki instead of re-reading months of journal entries.

## Location

```
<private-repo>/agent-managed/
  topics/         ← one markdown file per topic
  indexes/        ← cross-reference indexes across topics
  _candidates/    ← pending items from recent extraction runs
  log.md          ← audit log of extraction and update activity
  README.md
```

This directory lives in your **private repo**, not in `liferepo`. The data is
derived from private journal and conversation content. Only this spec lives
here.

## When to update

Update a topic page when a session produces synthesis that should become the
default understanding of a topic for future reads.

Do not update for:
- routine chronological logging — that goes in `journal/`
- raw source capture — keep that in `notes-private/`
- tiny isolated facts — those go in `memory/`

## Topic page structure

Each topic page should include:

```markdown
## Summary
One paragraph: what this topic is about and why it matters.

## Current Understanding
The best current synthesis. Written actively, not as a bullet list of events.
Updated each time new insight meaningfully changes the picture.

## Important Evidence
Concrete source references that support the current understanding.

## Open Questions
What remains unresolved or uncertain.

## Source Map
Links to journal entries, summaries, or notes that informed this page.
```

## How the AI uses it

1. **End-of-day workflow**: after finalizing the daily summary, the AI reads
   `log.md` and the day's highlights, identifies which canonical topics were
   touched, and rewrites their `Current Understanding` sections to reflect
   today's new context.

2. **Session startup**: when working in a domain, the AI can read the
   relevant topic page to recover cross-session synthesis without re-reading
   raw history.

3. **Synthesis mandate**: the AI should not rely purely on automated extraction
   scripts to append naive bullets. It is explicitly authorized to rewrite
   `Current Understanding` sections using semantic comprehension — the wiki
   should read like a curated encyclopedia, not a list of log entries.

## Automation support

A helper script in the private repo runs extraction from recent summaries:

```bash
python3 scripts/knowledge/refresh_agent_managed.py --date YYYY-MM-DD --apply-safe
```

This script appends candidates to `_candidates/` and updates `log.md`. The AI
then reviews candidates and promotes them into the canonical topic pages.

## Quality rules

- Prefer updating an existing page over creating near-duplicates.
- Keep claims tied to concrete source files.
- Write for future reuse, not for narrating the current session.
- Pages should be readable by both humans and agents.
