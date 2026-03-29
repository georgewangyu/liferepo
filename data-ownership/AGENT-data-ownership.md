# AGENT-data-ownership

## Purpose

Define reusable workflows for owning, exporting, and structuring personal data.

## Strategy

Use: research -> setup -> script -> test -> automate -> document.

## Export Requirements

- Incremental sync support.
- Standard formats (`md`, `json`, `csv`, `pdf` when needed).
- Clear error handling and timestamp logging.
- Credentials handled outside version control.
- Verification checks after each export run.

## Storage Rules

- Raw exports and personal data stay in `<private-repo>`.
- Public repos only keep schemas, templates, and safe examples.

## Operations

1. Prioritize one source at a time.
2. Create/validate setup docs before automation.
3. Add verification checks after each export run.
4. Track migration status and next action.

## Documentation Rules

- Keep setup docs close to each exporter.
- Maintain a migration status table with next action per source.
- Document troubleshooting steps after each non-trivial fix.

## Companion Spec

- `EXPORT_RUNBOOK.md`
