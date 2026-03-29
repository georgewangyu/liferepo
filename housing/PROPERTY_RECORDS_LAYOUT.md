---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/housing/PROPERTY_RECORDS_LAYOUT"
doc_type: "housing_doc"
doc_status: "active"
title: "Property Records Layout"
description: "Reusable folder strategy for private housing records."
memory_eligible: true
memory_priority: "medium"
doc_tags:
  - "domain:housing"
  - "visibility:public"
  - "type:housing_doc"
---
# Property Records Layout

Reusable folder strategy for private housing records.

## Recommended Structure

```text
housing/
  <location>/
    <property-id>/
      purchase-or-lease/
      legal/
      finance/
      rentals/
      tax/
      media/
      misc/
  mortgage-approval/
    identity/
    employment/
    tax/
    paystubs/
    lender-correspondence/
```

## Design Rules

- Keep one folder per property with stable naming.
- Group by document purpose rather than file type.
- Keep private identity and financial records in explicitly marked folders.
- Preserve original source docs; store transformed analysis separately.

## Analysis Pairing

When running property analysis, create an analysis note that references source
documents by filename/date rather than duplicating sensitive source content.
