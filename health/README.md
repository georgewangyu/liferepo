# Health Spec

Public specification layer for health-related workflows and agents.

## Contains

- ingestion and normalization workflow patterns
- context-building rules for daily journaling workflows
- interpretation guardrails for trend vs anomaly analysis
- family-record organization conventions

## Core Rules

- Keep subjective ratings separate from objective telemetry.
- Prefer trend windows and baselines over single metric snapshots.
- Never include diagnosis/treatment instructions in agent outputs.

## Companion Spec

- `FAMILY_HEALTH_RECORDS_WORKFLOW.md`

Private health state lives in:
- `<private-repo>/personal-health/`
- `<private-repo>/health-family/`
