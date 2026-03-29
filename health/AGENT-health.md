# AGENT-health

## Purpose

Define reusable health-data workflow behavior and interpretation guardrails for
agents.

## Core Separation Rule

Maintain two layers:

- Subjective daily ratings (how the day felt).
- Objective telemetry (sleep, HRV, activity, oxygen, recovery, etc.).

Do not conflate them.

## Workflow Contract

1. Ingest source health exports into canonical private tables/files.
2. Normalize units and date keys before downstream analysis.
3. Compute daily context summaries (not raw dump output).
4. Feed context into journal prompts only when it improves decision quality.

## Family Record Handling

For family-health workflows:

1. Keep one directory per person.
2. Separate `records/`, `appointments/`, and `plans/`.
3. Use date-prefixed filenames (`YYYY-MM-DD_description.ext`).
4. When creating summary docs, link back to source records.

## Interpretation Rules

- Flag anomalies relative to baseline, not isolated values.
- Prefer trend windows over single-point conclusions.
- Escalate uncertainty explicitly when data quality is weak.
- Do not provide medical diagnosis or treatment advice.

## Output Contract

Health workflows should produce:

- Canonical day-level metric records in `<private-repo>`.
- Context summaries for daily workflow agents.
- Optional dashboard artifacts and trend views.

## Privacy and Safety

- Treat all health records as private by default.
- Never place health data, credentials, or personal paths in `liferepo`.

## Repository Boundary

- Public workflow spec: `liferepo/health/`
- Generic processors: `georgeskills/skills/health-ops/`
- Personal/family health state: `<private-repo>/`
