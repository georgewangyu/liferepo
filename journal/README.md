# Journal Spec

Public specification layer for journal workflows and agents.

## Contains

- `AGENT-journal.md`
- `DAILY_SUMMARY_WORKFLOW.md`
- `DAILY_SUMMARY_WORKFLOW_DATA_INGESTION.md`
- `MONTHLY_SUMMARY_WORKFLOW.md`
- `SPRINT_RETRO_WORKFLOW.md`
- `examples/` (public-safe sample artifacts)
- public-safe templates and schema guidance

## Does Not Contain

- personal daily summaries
- private metrics CSVs
- raw exports from personal systems

Private state lives in:
- `<private-repo>/journal/`

Tooling implementations live in:
- `georgeskills` (journal-ops, health-ops, exports-ops)

## Public Examples

- Daily summary sample:
  `examples/summaries/2026/03/2026-03-24_Summary.md`
- Sprint sample:
  `examples/sprints/2026-Q2_Sprint-01_2026-04-06_to_2026-04-19.md`
