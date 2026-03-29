---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/memory/AGENT-memory"
doc_type: "memory_doc"
doc_status: "active"
title: "AGENT-memory"
description: "Define how agents extract, review, and maintain structured memory records from"
memory_eligible: true
memory_priority: "high"
doc_tags:
  - "domain:memory"
  - "visibility:public"
  - "type:memory_doc"
---
# AGENT-memory

## Purpose

Define how agents extract, review, and maintain structured memory records from
private narrative sources.

## Core Model

- Narrative files are the human source of truth.
- `memory/*.jsonl` is a structured overlay for retrieval.
- Candidate extraction and reviewed promotion are separate steps.
- Source docs keep static metadata in YAML frontmatter; runtime access metrics
  live in separate memory index/log files.

## Canonical Stores

Default high-value stores:

- `decisions.jsonl`
- `commitments.jsonl`
- `status_changes.jsonl`
- `people.jsonl`
- `patterns.jsonl`

## Record Quality Rules

1. Every record requires `source_ref`.
2. Use precise but concise titles and summaries.
3. Prefer day-level dates unless timestamp granularity matters.
4. Use `durability` intentionally (`ephemeral`, `active`, `durable`).
5. Use `status` intentionally (`candidate`, `accepted`, `stale`, `superseded`).
6. When replacing a record, set `supersedes` instead of silently deleting.

## Workflow Contract

1. Extract candidates from source artifacts into `<private-repo>/memory/candidates/`.
2. Review candidates for evidence quality and duplication.
3. Promote accepted records into canonical stores.
4. Run validation checks for required fields and broken references.
5. Keep dynamic retrieval stats in:
   - `<private-repo>/memory/doc_access_index.json`
   - `<private-repo>/memory/doc_access_log.jsonl`

## Anti-Patterns

- Copying full prose summaries into memory stores.
- Creating records without provenance.
- Treating weak inference as confirmed fact.
- Leaving conflicting active records unresolved.

## Repository Boundary

- Public schema/process spec: `liferepo/memory/`
- Tooling: `georgeskills/skills/memory-ops/`
- Canonical memory data: `<private-repo>/memory/`
