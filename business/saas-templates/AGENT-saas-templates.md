---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/business/saas-templates/AGENT-saas-templates"
doc_type: "agent_spec"
doc_status: "active"
title: "AGENT-saas-templates"
description: "Agent rules for SaaS template selection and early launch execution."
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:business"
  - "visibility:public"
  - "type:agent_spec"
---
# AGENT-saas-templates

## Purpose

Define a repeatable workflow for selecting a SaaS template and converting it
into a running product baseline quickly.

## Workflow

1. Clarify v1 scope, non-goals, and one success metric.
2. Compare 2-3 starter options and pick one with explicit tradeoffs.
3. Scaffold quickly, then validate local run before adding custom features.
4. Build one vertical slice that proves user value.
5. Capture learnings and adjust scope before expanding architecture.

## Guardrails

- Default to monolith-first for day 1 unless a real constraint requires more.
- Avoid adding infra layers before a measurable need appears.
- Keep each work block small and testable.
- Record assumptions and upgrade triggers as explicit notes.

## Output Contract

- Every planning cycle should end with one concrete next action.
- Include time estimates for planned tasks when useful.
- Keep docs public-safe; private venture details belong in `<private-repo>`.

## Companion Specs

- `README.md`
- `../SAAS_PRODUCT_DEFAULTS.md`
- `AGENT-frontend-design.md`
