---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/journal/DAILY_SUMMARY_WORKFLOW"
doc_type: "workflow_spec"
doc_status: "active"
title: "Agent: Daily Summary Builder"
description: "Maintain one daily summary per date:"
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:journal"
  - "visibility:public"
  - "type:workflow_spec"
---
# Agent: Daily Summary Builder

## Goal

Maintain one daily summary per date:

```text
<private-repo>/journal/summaries/YYYY/MM/YYYY-MM-DD_Summary.md
```

Use an incremental-throughout-day model, then finalize with an end-of-day
interview.

Companion ingestion spec:
- `DAILY_SUMMARY_WORKFLOW_DATA_INGESTION.md`

## Two-Phase Model

## Phase 1: Incremental Capture

During normal chat/work, append relevant facts as rough bullets:

- wins and outcomes
- blockers/challenges
- decisions
- people interactions
- health/energy context
- priorities and unfinished work

Do not block on polish during this phase.

## Phase 2: End-of-Day Finalization

Finalize by running:

1. data freshness checks
2. metrics capture
3. reflection interview
4. synthesis and cleanup

## Morning Cue Protocol

If user starts with `morning`, `start of day`, or similar:

```bash
python3 <private-repo>/scripts/journal/morning_brief.py --date YYYY-MM-DD
```

If brief reports `watch`/`alert`, surface that before sprint planning.

## Private Overlay Hook

If present, load:

```text
<private-repo>/journal/PRIVATE-journal.md
```

before applying narrator tone or private style preferences.

## Data Inputs (Before Interview)

Use these when available:

- Apple Notes export context
- email export context
- calendar context
- health context
- optional location context
- same-day git history context

Recommended helper commands:

```bash
python3 <private-repo>/scripts/exports/apple-notes/export_apple_notes.py
python3 <private-repo>/scripts/exports/email/export_emails_gmail_api.py
python3 <private-repo>/scripts/exports/calendar/export_calendar_google.py

python3 <private-repo>/scripts/journal/print_health_interview_context.py --date YYYY-MM-DD
python3 <private-repo>/scripts/journal/print_email_interview_context.py --date YYYY-MM-DD
python3 <private-repo>/scripts/journal/print_location_interview_context.py --date YYYY-MM-DD
```

## Interview Order

Ask in this order:

1. Daily metrics:
   - Energy (1-5)
   - Mood (1-5)
   - Focus (1-5)
   - Productivity (1-5)
2. Optional meal check-in:
   - lunch summary
   - post-lunch crash yes/no
3. Reflection prompts:
   - deep sprint review
   - one challenge
   - one win
   - notable people interactions
   - key decisions
   - top priorities for tomorrow
   - mood sentence and why

## Sprint Check-in (Recommended)

For each day, capture:

- morning sprint (hardest/most important)
- work-hour sprints
- evening sprints
- light blocks

Track domain tags:

- `Job/Interview/Skills`
- `Content`
- `Personal Project`
- `Business/Corp`

## Output Contract

Write/update:

```text
<private-repo>/journal/summaries/YYYY/MM/YYYY-MM-DD_Summary.md
```

Public reference example:

```text
journal/examples/summaries/2026/03/2026-03-24_Summary.md
```

Minimum sections:

- Today at a Glance
- Daily Metrics
- Sprints Today
- Highlights
- Challenges
- Key Decisions
- People / Relationships
- Tomorrow Priorities

## Status Header

Use YAML frontmatter.

Daily summaries must include the standard doc header contract
(`doc_schema`, `doc_id`, `doc_type`, `doc_status`, `title`, `description`,
`doc_tags`, `memory_eligible`, `memory_priority`) plus `summary_status`.

Example:

```yaml
doc_schema: "doc-frontmatter-v1"
doc_id: "<private-repo>/journal/summaries/2026/03/2026-03-28_Summary"
doc_type: "daily_summary"
doc_status: "active"
title: "Daily Summary — 2026-03-28"
description: "One-line summary of the day."
doc_tags:
  - "domain:journal"
  - "visibility:private"
  - "type:daily_summary"
memory_eligible: true
memory_priority: "high"
summary_status: planned | partial | completed
```

Definitions:

- `planned`: summary file initialized, interview/finalization not yet run
- `partial`: meaningful content captured, still materially incomplete
- `completed`: workflow completed with best available data

## Quality Rules

- Keep summaries specific and retrieval-friendly.
- Separate objective telemetry from subjective ratings.
- Avoid duplicating raw export dumps in the summary body.
- Keep personal style preferences in private overlays, not public spec.
