---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/journal/AGENT-journal"
doc_type: "agent_spec"
doc_status: "active"
title: "AGENT-journal"
description: "Define reusable journaling behavior for agents, including interview flow,"
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:journal"
  - "visibility:public"
  - "type:agent_spec"
---
# AGENT-journal

## Purpose

Define reusable journaling behavior for agents, including interview flow,
workflow order, and output contracts.

## Triggers

Treat these as journal workflow cues:

- `morning`, `start of day`, `daily workflow`, `daily summary`
- `monthly summary`, `month recap`
- `retro`, `sprint retro`

## Core Workflow Rules

1. Always establish target date first (`YYYY-MM-DD`).
2. Run data/context prep before interview prompts.
3. Separate objective context from subjective reflection.
4. Generate artifacts into `<private-repo>/journal/`, not `liferepo`.

## Daily Summary Contract

Daily flow should produce:

1. Workflow status check (already started vs not started).
2. Context blocks (calendar/notes/health/location/email if available).
3. Interview responses:
   - highlights
   - blockers
   - decisions
   - tomorrow plan
   - subjective ratings (energy, mood, focus, productivity)
4. A final daily summary artifact in `<private-repo>/journal/summaries/`.

Daily summary markdown must include standard doc frontmatter plus
`summary_status`.

## Monthly and Retro Contracts

- Monthly summaries aggregate outcomes across daily summaries.
- Sprint retros identify repeat patterns, not one-off anomalies.
- Distill concrete process changes into next-sprint action items.

## Style and Quality Rules

- Keep summaries factual, specific, and retrieval-friendly.
- Use concrete references over abstract phrasing.
- Preserve human voice while avoiding private details in public specs.

## Repository Boundary

- Public specification: `liferepo/journal/`
- Modular tooling: `georgeskills/skills/journal-ops/`
- Private data/artifacts: `<private-repo>/journal/`

## Required Companion Specs

- `DAILY_SUMMARY_WORKFLOW.md`
- `DAILY_SUMMARY_WORKFLOW_DATA_INGESTION.md`
- `MONTHLY_SUMMARY_WORKFLOW.md`
- `SPRINT_RETRO_WORKFLOW.md`
