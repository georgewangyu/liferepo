---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/health/APPLE_HEALTH_ONBOARDING"
doc_type: "health_doc"
doc_status: "active"
title: "Apple Health Onboarding"
description: "This guide explains how a new user sets up Apple Health ingestion for the"
memory_eligible: true
memory_priority: "medium"
doc_tags:
  - "domain:health"
  - "visibility:public"
  - "type:health_doc"
---
# Apple Health Onboarding

This guide explains how a new user sets up Apple Health ingestion for the
`liferepo` + `georgeskills` split.

## Summary

A new user cannot run the Apple Health workflow without setup first.

They need:

1. a configured private repo
2. at least one Apple Health export path
3. a canonical private destination for normalized health records

Recommended private layout for new setups:

```text
<private-repo>/
  health-data/
    source-records/
      apple_health_export/
      HealthAutoExport_YYYYMMDDHHMMSS/
    records/
      daily_health_metrics.csv
      health_auto_export_raw/
```

`georgeskills` prefers that layout, but still supports older private layouts
such as `people/george/health/records/` and `people/[person]/health/records/`.

## Step 1: Bootstrap the Private Repo

From `liferepo/`:

```bash
python3 ../georgeskills/scripts/bootstrap_private_repo.py --name my-private-repo --create
```

This creates the private-repo pointer config and marker files.

## Step 2: Choose an Ingestion Path

There are three supported ways to get Apple Health data into the system.

### Option A: Health Auto Export JSON

Best default when available.

Why:
- daily automation-friendly
- good fit for journal workflow prep
- preserves raw payloads for replay/debug

Typical sources:
- Google Drive export folder
- iCloud app Documents folder
- explicit JSON file path

Importer:

```bash
python3 <private-repo>/scripts/journal/import_health_auto_export_google_drive.py
```

### Option B: Apple Health `export.xml`

Best for full-history backfill and dashboard/trend generation.

Why:
- full historical dataset
- useful for rebuilding canonical daily records
- required by the richer health dashboard flow

Importer:

```bash
python3 <private-repo>/scripts/journal/import_apple_health_export_xml.py --date YYYY-MM-DD
```

Dashboard builder:

```bash
python3 <private-repo>/scripts/journal/build_health_dashboard.py
```

### Option C: Shortcut CSV

Useful when a user already has a Shortcut writing a simple daily CSV.

Why:
- lightweight
- easy to inspect manually
- lower fidelity than JSON/XML flows

Importer:

```bash
python3 <private-repo>/scripts/journal/import_health_shortcut_csv.py
```

## Step 3: Put Data in the Expected Place

Recommended new layout:

- Apple Health XML:
  `<private-repo>/health-data/source-records/apple_health_export/export.xml`
- Health Auto Export CSV/JSON:
  `<private-repo>/health-data/source-records/`
- Canonical normalized records:
  `<private-repo>/health-data/records/`

If the user wants a different layout, they can override it with environment
variables:

- `LIFEREPO_HEALTH_SOURCE_ROOT`
- `LIFEREPO_HEALTH_RECORDS_ROOT`

## Step 4: Run a First Import

### JSON path

```bash
python3 <private-repo>/scripts/journal/import_health_auto_export_google_drive.py --write
```

### XML path

```bash
python3 <private-repo>/scripts/journal/import_apple_health_export_xml.py --date YYYY-MM-DD
```

### Shortcut CSV path

```bash
python3 <private-repo>/scripts/journal/import_health_shortcut_csv.py --write
```

## Step 5: Confirm the Canonical Output Exists

The journal workflow expects a canonical daily health metrics CSV.

Preferred location:

```text
<private-repo>/health-data/records/daily_health_metrics.csv
```

This is what downstream context builders read.

## Step 6: Verify Journal Context

Check the per-day health context:

```bash
python3 <private-repo>/scripts/journal/print_health_interview_context.py --date YYYY-MM-DD
```

Or run the full prep flow:

```bash
python3 <private-repo>/scripts/journal/run_daily_workflow_prep.py --date YYYY-MM-DD
```

## What the Tooling Resolves Automatically

`georgeskills` health tooling resolves paths in this order:

1. `LIFEREPO_HEALTH_SOURCE_ROOT` / `LIFEREPO_HEALTH_RECORDS_ROOT`
2. preferred `health-data/...` layout
3. legacy private layouts if present

That means a new user should prefer the `health-data/` layout, while an older
private repo can continue to work without immediate file moves.

## Recommended New-User Path

For a brand-new setup:

1. bootstrap the private repo
2. create `health-data/source-records/` and `health-data/records/`
3. start with Health Auto Export JSON if available
4. add Apple Health `export.xml` if they want full-history dashboards
5. verify `daily_health_metrics.csv`
6. use `run_daily_workflow_prep.py` for day-to-day operation

## Non-Goals

This guide does not cover:

- medical interpretation
- App Store setup details for third-party exporters
- iOS Shortcut authoring beyond the expected CSV destination

It only defines the repository/tooling contract needed to make the workflow run.
