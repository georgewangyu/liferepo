---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/journal/SPRINT_RETRO_WORKFLOW"
doc_type: "workflow_spec"
doc_status: "active"
title: "Agent: Sprint Retrospective Builder"
description: "Generate a sprint retrospective for a fixed sprint window (commonly 2 weeks),"
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:journal"
  - "visibility:public"
  - "type:workflow_spec"
---
# Agent: Sprint Retrospective Builder

## Goal

Generate a sprint retrospective for a fixed sprint window (commonly 2 weeks),
using daily summaries + metrics + sprint plan.

## Inputs

- sprint file in `<private-repo>/journal/sprints/`
- daily summaries within sprint date range
- daily metrics and optional sprint metrics CSV
- optional reflections from sprint window

Public reference example:

- `journal/examples/sprints/2026-Q2_Sprint-01_2026-04-06_to_2026-04-19.md`

## Data Collection

1. Read sprint goals/planned backlog.
2. Read all daily summaries in sprint date range.
3. Compute sprint-level metrics:
   - days tracked
   - deep sprint count
   - light block count
   - completion rate
   - domain mix
4. Compare week 1 vs week 2 trend for energy/focus/productivity.

## Domain Allocation Review

Use consistent domain categories:

- `Job/Interview/Skills`
- `Content`
- `Personal Project`
- `Business/Corp`

If a quarterly plan exists, compare actual domain mix vs target ranges.

## Reflection Interview

Ask:

1. Overall sprint rating (1-5).
2. Which goals were completed / missed.
3. Biggest win.
4. Biggest challenge.
5. Sprint rhythm sustainability.
6. Domain-mix quality (over/under allocation).
7. What to change next sprint.

## Output Sections

- Sprint Overview
- Goal Achievement
- Metrics Summary
- Domain Allocation Review
- Top Wins
- Recurring Friction
- Key Decisions
- Adjustments for Next Sprint

## Quality Rules

- Include evidence for major claims.
- Separate structural issues from one-off bad days.
- End with concrete changes for next sprint plan.
