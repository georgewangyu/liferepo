# Daily Summary Data Ingestion

Companion to `DAILY_SUMMARY_WORKFLOW.md`.

## Goal

Provide reliable context streams (health, notes, email, calendar, optional
transactions/location) before daily-summary interviews.

## Priority Order

1. Health context
2. Notes/email/calendar context
3. Optional location/transaction context

## Health Ingestion Strategy

Recommended first path:

- file-based automation export -> normalized daily CSV -> interview context

Required outputs:

- canonical daily health metrics table in the configured private health-records root
- interview context view for target date

Preferred private layout for new setups:

- source records: `<private-repo>/health-data/source-records/`
- canonical records: `<private-repo>/health-data/records/`

Legacy private layouts may still exist and are supported by the private wrappers
and `georgeskills` health tooling.

Typical command flow:

```bash
python3 <private-repo>/scripts/journal/import_health_auto_export_google_drive.py --write
python3 <private-repo>/scripts/journal/print_health_interview_context.py --date YYYY-MM-DD
```

Fallback importers may exist (CSV/XML bridges), but should not be the default
for new setups.

## Notes / Email / Calendar Ingestion

Run exporters prior to interview:

```bash
python3 <private-repo>/scripts/exports/apple-notes/export_apple_notes.py
python3 <private-repo>/scripts/exports/email/export_emails_gmail_api.py
python3 <private-repo>/scripts/exports/calendar/export_calendar_google.py
```

Then extract target-date context for interview prompts.

## Optional Location Context

If configured:

```bash
python3 <private-repo>/scripts/journal/print_location_interview_context.py --date YYYY-MM-DD
```

## Data Quality Rules

- Prefer summarized, normalized daily metrics over raw source dumps.
- Keep raw payload archives in private state for replay/debug.
- Track missing data and parser mismatches explicitly.

## Privacy Rules

- All raw exports remain in `<private-repo>`.
- Public repos keep only schema/workflow docs and safe examples.
