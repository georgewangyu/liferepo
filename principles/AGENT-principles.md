---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/principles/AGENT-principles"
doc_type: "agent_spec"
doc_status: "active"
title: "AGENT-principles"
description: "Define reusable rules for maintaining decision principles over time."
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:principles"
  - "visibility:public"
  - "type:agent_spec"
---
# AGENT-principles

## Purpose

Define reusable rules for maintaining decision principles over time.

## Authoring Rules

1. Each principle must be concise and testable.
2. Track domain, date added, and examples.
3. Avoid duplicates; merge overlaps intentionally.
4. Use consistent date formatting (`YYYY-MM-DD`).

## Update Rules

- Keep modification history when meaning changes.
- Record why a principle evolved.
- Mark superseded principles instead of silent deletion.

## Integration

- Link principles to concrete decisions or recurring patterns.
- Feed principle updates back into workflows that depend on them.

## Extraction Rules

- When extracting principles from notes, propose candidates first.
- Preserve source context and examples before formalizing.
- Require explicit confirmation before adding high-impact principles.

## Companion Spec

- `PRINCIPLE_MAINTENANCE_WORKFLOW.md`
