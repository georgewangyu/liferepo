---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/deep-exploration/AGENT-deep-exploration"
doc_type: "agent_spec"
doc_status: "active"
title: "AGENT-deep-exploration"
description: "Define reusable exploration-day and exploration-sprint behavior so research time"
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:deep-exploration"
  - "visibility:public"
  - "type:agent_spec"
---
# AGENT-deep-exploration

## Purpose

Define reusable exploration-day and exploration-sprint behavior so research time
produces reusable artifacts instead of passive reading.

## Core Principles

1. Exploration is sprint-based, not endless browsing.
2. Every sprint should produce at least one artifact.
3. Exploration should be adjacent to current execution needs.
4. Memory consolidation breaks are part of the process.

## Sprint Structure

Use this sequence:

1. Orientation: define 3-5 guiding questions and constraints.
2. Broad scan: capture surprises and model-breaking signals.
3. Model formation: produce candidate abstractions/diagrams.
4. Probe: test assumptions with lightweight experiments.
5. Distill: write insights and execution hooks.

## Queue Management

- Keep exploration queue simple: open questions only.
- Add new question if not already in queue.
- For each exploration day, select only 1-2 queue items.
- Archive or close question when sufficiently answered.

## Artifact Requirement

Every exploration cycle must produce at least one:

- reusable mental model
- framework/checklist
- decision memo
- execution hook for next sprint

## Quality Gates

- Insights must be specific enough to apply.
- Claims should be linked to source evidence.
- Distillation should separate "known", "assumed", and "uncertain".
- Output should be explainable to another person without hidden context.

## Integration Rules

- Route validated insights to `knowledge/` or `principles/`.
- Route execution hooks into next sprint planning surfaces.
- Include exploration outcomes in daily/weekly retrospectives.

## Anti-Patterns

- Exploration without artifacts.
- Random topic hopping without adjacent relevance.
- Overlong exploration with no integration back to execution.

## Repository Boundary

- Public framework spec: `liferepo/deep-exploration/`
- Optional helper tooling: `georgeskills/skills/deep-exploration-ops/`
- Private outputs and notes: `<private-repo>/deep-exploration/`
