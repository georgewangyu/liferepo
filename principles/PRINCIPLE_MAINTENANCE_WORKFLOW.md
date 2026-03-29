---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/principles/PRINCIPLE_MAINTENANCE_WORKFLOW"
doc_type: "workflow_spec"
doc_status: "active"
title: "Principle Maintenance Workflow"
description: "Reusable workflow for adding, reviewing, and evolving principles."
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:principles"
  - "visibility:public"
  - "type:workflow_spec"
---
# Principle Maintenance Workflow

Reusable workflow for adding, reviewing, and evolving principles.

## Add Flow

1. Determine domain for candidate principle.
2. Check for overlap with existing principles.
3. Add concise statement + date + examples.
4. Record source context.

## Modify Flow

1. Update `last modified` date.
2. Record change rationale in evolution history.
3. Preserve prior meaning if principle changed significantly.

## Review Flow

1. Detect duplicates or conflicts.
2. Identify stale principles not reflected in current behavior.
3. Propose merge/split/deprecation actions.

## Candidate Extraction

When mining notes/journals for principles:

1. Extract candidate statements.
2. Attach source references.
3. Present for review before codifying.

## Output Contract

For each maintenance pass, provide:

- added principles
- modified principles
- deprecated/superseded principles
- open questions requiring owner decision
