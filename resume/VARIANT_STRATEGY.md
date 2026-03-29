---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/resume/VARIANT_STRATEGY"
doc_type: "resume_doc"
doc_status: "active"
title: "Resume Variant Strategy"
description: "Reusable strategy for maintaining multiple role-targeted resume variants"
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:resume"
  - "visibility:public"
  - "type:resume_doc"
---
# Resume Variant Strategy

Reusable strategy for maintaining multiple role-targeted resume variants
without uncontrolled duplication.

## Why Variants

Different role families emphasize different signals. One generic resume usually
underserves at least one audience.

## Common Variant Families

- `data_infra`: distributed systems, storage, reliability, performance.
- `ai_infra`: AI platform, developer tooling, experimentation systems.
- `product_backend`: product impact, iteration speed, cross-functional delivery.

## Variant Workflow

1. Map target role to variant family.
2. Reorder summary and top bullets for that family.
3. Adjust keywords and tooling language for JD alignment.
4. Preserve factual consistency across all variants.
5. Run ATS and hiring-manager review pass.

## Governance Rules

- Keep a small, intentional set of families.
- Avoid one-off variants unless justified by repeated target demand.
- Track why each variant exists and when it was last refreshed.

## Boundary

Keep user-specific company targeting notes and actual files in
`<private-repo>/Resume/`.
