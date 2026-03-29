# Private Repo Setup

This checklist defines first-run setup for `<private-repo>` after cloning
`liferepo` + `georgeskills`.

## Core Bootstrap (Required)

From `liferepo/`:

```bash
python3 ../georgeskills/scripts/bootstrap_private_repo.py \
  --name my-private-repo \
  --create
```

This creates:

- `liferepo/.liferepo/local/private_repo.json`
- `<private-repo>/.liferepo-private.json`
- `<private-repo>/SOUL.md` (copied from `templates/SOUL.template.md` if missing)
- `<private-repo>/PRIVATE_RUNTIME.md` (copied from
  `templates/PRIVATE_RUNTIME.template.md` if missing)

## Interactive Quick Start

For a guided first-run setup, use:

```bash
python3 ../georgeskills/scripts/bootstrap_private_repo.py \
  --name my-private-repo \
  --create \
  --interactive
```

Or explicit flags:

```bash
python3 ../georgeskills/scripts/bootstrap_private_repo.py \
  --name my-private-repo \
  --create \
  --init-journal \
  --init-resume \
  --init-exports
```

Module outputs:

- `--init-journal`: creates `<private-repo>/journal/` folders for summaries,
  sprints, and reflections.
- `--init-resume`: creates `<private-repo>/Resume/` starter structure.
- `--init-exports`: creates `<private-repo>/scripts/exports/` starter structure
  for Apple Notes + Gmail + Google Calendar integrations.

## Integration Prerequisites (Optional)

These are optional and only needed if you want ingestion automation.

### Email Export (Gmail API)

- Create a Google Cloud project.
- Enable Gmail API.
- Download OAuth client credentials.
- Place credentials in `<private-repo>/scripts/exports/email/credentials.json`.
- Run auth flow via your local export script wrapper.

### Calendar Export (Google Calendar API)

- Enable Google Calendar API in the same or separate Google Cloud project.
- Place OAuth credentials at
  `<private-repo>/scripts/exports/calendar/credentials.json`.
- Run auth flow via your local export script wrapper.

### Apple Notes Export (macOS)

- Grant Terminal automation access to Notes in macOS Privacy settings.
- Use `<private-repo>/scripts/exports/apple-notes/` script wrappers.

## Runtime Rule

When a private repo is configured, `<private-repo>/SOUL.md` is the runtime
personality source of truth.

`liferepo/templates/SOUL.template.md` is only the starter template.
