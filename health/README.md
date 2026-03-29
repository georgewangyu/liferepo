---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/health/README"
doc_type: "readme"
doc_status: "active"
title: "Health Spec"
description: "Public specification layer for health-related workflows and agents."
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:health"
  - "visibility:public"
  - "type:readme"
---
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
- `APPLE_HEALTH_ONBOARDING.md`

Private health state lives in:
- preferred source-records root: `<private-repo>/health-data/source-records/`
- preferred canonical-records root: `<private-repo>/health-data/records/`

Legacy private layouts may still include:
- `<private-repo>/personal-health/`
- `<private-repo>/health-family/`
