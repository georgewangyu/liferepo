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
