---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/docs/BOUNDARY_CONTRACT"
doc_type: "docs_doc"
doc_status: "active"
title: "Boundary Contract"
description: "This workspace uses a strict three-repo model:"
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:docs"
  - "visibility:public"
  - "type:docs_doc"
---
# Boundary Contract

This workspace uses a strict three-repo model:

- `liferepo`: public specifications (agents, workflows, schemas, templates)
- `georgeskills`: modular execution tooling (skills + reusable scripts)
- `<private-repo>`: private state and records (personal data, raw artifacts, local ops)

## Ownership Matrix

| Domain | `liferepo` (spec) | `georgeskills` (tools) | `<private-repo>` (state) |
|---|---|---|---|
| Journal | agent/workflow docs, templates | ingestion/export/analysis scripts | summaries, reflections, private metrics |
| Memory | schema + operating rules | extract/validate/promote tools | canonical memory stores + candidates |
| Health | workflow + interpretation rules | generic health processors | health records and raw telemetry |
| Deep Exploration | frameworks + prompts | optional synthesis tooling | private exploration artifacts and notes |

## Decision Rule

Put an artifact in `liferepo` only if it is:

1. reusable beyond one person/context
2. free of private/sensitive content
3. safe for permanent public commit history

If any rule fails:

- Put code-like logic in `georgeskills`
- Put data/content in `<private-repo>`

## Duplication Policy

- Duplicate domain names across repos (for clarity), not content.
- Every artifact has one canonical home.
- Private repos may keep thin pointers to public specs, not copied spec docs.

## Migration Sequence

1. Move/define specs in `liferepo`
2. Move generic execution tools into `georgeskills`
3. Keep private state in `<private-repo>`
4. Replace old duplicated docs with pointers
