---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/deep-exploration/README"
doc_type: "readme"
doc_status: "active"
title: "Deep Exploration Spec"
description: "Public specification layer for structured exploration workflows."
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:deep-exploration"
  - "visibility:public"
  - "type:readme"
---
# Deep Exploration Spec

Public specification layer for structured exploration workflows.

## Contains

- exploration-day workflow patterns
- output quality gates
- reusable exploration agent guidance
- queue-management conventions
- distillation and execution-hook practices

## Standard Sequence

1. Orientation (questions + constraints)
2. Broad scan (surprises and counter-signals)
3. Model formation (abstractions/diagrams)
4. Probe (experiments)
5. Distillation (execution hooks)

## Outcome Requirement

Each exploration cycle should yield reusable artifacts, not just notes.

Private exploration artifacts live in:
- `<private-repo>/deep-exploration/`
