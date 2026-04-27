---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/career/us-visa/README"
doc_type: "readme"
doc_status: "active"
title: "US Visa Prep Workflow"
description: "Public-safe workflow guidance for organizing US visa preparation materials."
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:career"
  - "domain:immigration"
  - "visibility:public"
  - "type:readme"
---
# US Visa Prep Workflow

This folder defines where US visa preparation artifacts should live in the
split-repo model.

## Canonical Locations

- Personal files (passport scans, offer letters, transcripts, generated PDFs):
  `<private-repo>/immigration/us-visa/`
- Public specs/workflows:
  `liferepo/career/us-visa/`
- Reusable tooling (only if generic and non-personal):
  `georgeskills/skills/`

## Migration Rule

Do not commit personal visa documents to `liferepo` or `georgeskills`.
Only commit workflow instructions or reusable, sanitized templates here.
