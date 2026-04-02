---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/AGENTS"
doc_type: "agent_spec"
doc_status: "active"
title: "Codex Session Bootstrap"
description: "This file is a pointer-style bootstrap. Keep it short."
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:AGENTS.md"
  - "visibility:public"
  - "type:agent_spec"
---
# Codex Session Bootstrap

This file is a pointer-style bootstrap. Keep it short.
Substantive rules live in `AGENT.md` and local `AGENT-*.md` files.

## Required Startup Context

At the start of every new session in this repository, read in order:

1. `AGENT.md`
2. `docs/ASSISTANT_OPERATING_MANUAL.md`
3. `README.md`
4. If configured, load `<private-repo>/SOUL.md` via `.liferepo/local/private_repo.json`.
5. If configured, load `<private-repo>/PRIVATE_RUNTIME.md`.
6. If configured and running journal workflows, load `<private-repo>/journal/PRIVATE-journal.md`.
7. If no private repo is configured yet, use:
   - `templates/SOUL.template.md`
   - `templates/PRIVATE_RUNTIME.template.md`

Treat `docs/ASSISTANT_OPERATING_MANUAL.md` as required runtime policy, not
reference material. Commit-format rules in that file are mandatory for every
commit.
Apply its low-risk auto-commit policy during the session, especially for docs,
notes, summaries, and similar reversible repo-memory changes. Do not wait for
an extra user nudge to commit that category of work locally.

## Directory-Specific Context

When working in a subdirectory:

1. Read the nearest `AGENT-*.md` (or local `AGENT.md`).
2. Read the local `README.md`.
3. Load only task-relevant docs.

## Priority

If instructions conflict:

1. User instructions in chat
2. More specific local docs
3. Root-level repository docs
