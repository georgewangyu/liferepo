# Family Health Records Workflow

## Goal

Maintain private family-health records in a structure that is searchable,
auditable, and safe.

## Recommended Structure

```text
<private-repo>/health-family/
  <person-a>/
    records/
    appointments/
    plans/
  <person-b>/
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

The family-health tree is still the right place for person-specific records,
appointments, and plans.

## File Naming

- Use `YYYY-MM-DD_description.ext` where possible.
- Keep source files immutable; add summary notes separately.

## Operating Steps

1. Identify the correct person folder.
2. Place artifact in correct type folder (`records`, `appointments`, `plans`).
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
