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

## Canonical Store Set

- `decisions.jsonl`
- `commitments.jsonl`
- `status_changes.jsonl`
- `people.jsonl`
- `patterns.jsonl`

Private memory records live in:
- `<private-repo>/memory/`
