---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/writing/shareable/AGENT-shareable"
doc_type: "agent_spec"
doc_status: "active"
title: "AGENT-shareable"
description: "Rules for drafting public-safe markdown pieces that can be shared as gists,"
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:writing"
  - "visibility:public"
  - "type:agent_spec"
---
# AGENT-shareable

Use this directory for public-safe markdown drafts that may later be shared as
gists, posts, or reference notes.

## Rules

- Keep each piece self-contained and readable outside repo context.
- Prefer one clear argument per file.
- Avoid private identifiers, local paths, and unpublished sensitive context.
- When a piece references system architecture, use `<private-repo>` placeholders
  instead of naming a real private repository.
- Draft locally first. Treat publication as a separate step.

## Output Shape

- Start with a strong title.
- Open with the core problem in plain language.
- Explain the system design, not just the vibe.
- End with a practical takeaway or operating principle.
