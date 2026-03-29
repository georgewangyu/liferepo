---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/data-ownership/EXPORT_RUNBOOK"
doc_type: "data-ownership_doc"
doc_status: "active"
title: "Export Runbook"
description: "Reusable runbook for adding a new personal-data export source."
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:data-ownership"
  - "visibility:public"
  - "type:data-ownership_doc"
---
# Export Runbook

Reusable runbook for adding a new personal-data export source.

## Lifecycle

1. Research API/export options.
2. Implement setup steps.
3. Build exporter script.
4. Test with narrow sample.
5. Add automation schedule.
6. Add verification checks.
7. Document operations + known limits.

## Export Script Checklist

- incremental mode supported
- explicit timestamp or checkpoint state
- structured output format
- retry/error behavior documented
- credentials loaded from local secure config

## Verification Checklist

- script exits cleanly
- output location and file naming are correct
- duplicate prevention works
- newest records are present
- summary/log output is actionable

## Security Checklist

- no credentials in git
- no raw private data in public repos
- sensitive sources flagged for stricter retention and access control
