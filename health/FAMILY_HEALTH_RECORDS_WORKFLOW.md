---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/health/FAMILY_HEALTH_RECORDS_WORKFLOW"
doc_type: "workflow_spec"
doc_status: "active"
title: "Family Health Records Workflow"
description: "Maintain private family-health records in a structure that is searchable,"
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:health"
  - "visibility:public"
  - "type:workflow_spec"
---
# Family Health Records Workflow

## Goal

Maintain private family-health records in a structure that is searchable,
auditable, and safe.

## Recommended Structure

```text
<private-repo>/people/
  <person-a>/
    health/
      records/
      appointments/
      plans/
  <person-b>/
    health/
      records/
      appointments/
      plans/
```

For newer setups, keep canonical daily metric tables separate from the
per-person family record tree:

```text
<private-repo>/health-data/
  source-records/
  records/
```

The per-person `health/` tree is the right place for person-specific records,
appointments, and plans.

## File Naming

- Use `YYYY-MM-DD_description.ext` where possible.
- Keep source files immutable; add summary notes separately.

## Operating Steps

1. Identify the correct person folder.
2. Place artifact in the correct type folder inside `health/`
   (`records`, `appointments`, `plans`).
3. For appointment notes, capture:
   - reason
   - key findings
   - next steps
4. For plans, include:
   - current state
   - action items
   - review date
5. Update local index/README if structure changes.

## Privacy

- Family-health data is private by default.
- Never copy private records into `liferepo`.
