---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/memory/README"
doc_type: "memory_doc"
doc_status: "active"
title: "Memory Spec"
description: "Public specification layer for structured memory schemas and workflows."
memory_eligible: true
memory_priority: "high"
doc_tags:
  - "domain:memory"
  - "visibility:public"
  - "type:memory_doc"
---
# Memory Spec

Public specification layer for structured memory schemas and workflows.

## Contains

- memory model and lifecycle rules
- extraction/review/promote process definitions
- reusable memory-agent guidance

## Recommended Operating Loop

1. Extract candidates from private narrative sources.
2. Review candidates for evidence quality and duplication risk.
3. Promote accepted records into canonical stores.
4. Validate schema and provenance fields.

## Metadata + Access Index

- Source markdown docs should carry static routing metadata in YAML frontmatter
  (for example `doc_type`, `doc_tags`, `memory_eligible`).
- Dynamic usage metadata must live outside docs in the private memory access
  index/log:
  - `memory/doc_access_index.json`
  - `memory/doc_access_log.jsonl`

## Candidate Sources

- Daily summaries remain the primary extraction source.
- Memory-eligible markdown docs changed on the target day are a secondary
  extraction source.

## Canonical Store Set

- `decisions.jsonl`
- `commitments.jsonl`
- `status_changes.jsonl`
- `people.jsonl`
- `patterns.jsonl`

Private memory records live in:
- `<private-repo>/memory/`
