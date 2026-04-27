---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/knowledge/finance/README"
doc_type: "readme"
doc_status: "active"
title: "Finance Knowledge"
description: "Public-safe finance learning notes and conceptual frameworks."
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:knowledge"
  - "domain:finance"
  - "visibility:public"
  - "type:readme"
---
# Finance Knowledge

Public-safe finance learning notes and conceptual frameworks.

This directory is for **learning** (concepts, frameworks, and market structure
notes). It is intentionally separate from operational investing state.

## Boundaries

- `liferepo/knowledge/finance/`:
  reusable notes safe for public commit history
- `<private-repo>/finance/`:
  personal finance operations (plans, watchlists, positions, reviews, taxes)
- `georgeskills/`:
  reusable automation scripts when logic is generic enough to be shared

## Current Structure

- `concepts/`: dated finance learning logs and framework notes

## Migration Rule

When a note includes sensitive personal positions or account-level detail, store
the canonical version under `<private-repo>/finance/` and keep only a sanitized
or conceptual version here.
