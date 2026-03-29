---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/docs/REPO_SPLIT_POLICY"
doc_type: "docs_doc"
doc_status: "active"
title: "Repository Split Policy"
description: "This workspace uses three repositories with explicit boundaries:"
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:docs"
  - "visibility:public"
  - "type:docs_doc"
---
# Repository Split Policy

This workspace uses three repositories with explicit boundaries:

- `liferepo` (public): reusable agent framework docs/templates
- `georgeskills` (tools): modular skills and reusable scripts
- `<private-repo>` (private): personal operations and sensitive records

The detailed multi-repo contract is documented in:
- `docs/BOUNDARY_CONTRACT.md`

## Classification Rules

Put content in `liferepo` only if all are true:

1. It is reusable and not tied to private data.
2. It contains no personal, medical, financial, legal, or confidential details.
3. It is safe for public commit history.

If any condition fails, place it in `<private-repo>`.
If content is reusable tooling (but not public-safe docs), place it in
`georgeskills`.

## Publishing Checklist

- Run a secret scan before publishing.
- Grep for private markers (`notes-private`, `journal/summaries`, `token`).
- Confirm no accidental binary exports or raw private dumps are present.
