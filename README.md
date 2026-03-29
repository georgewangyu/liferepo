# liferepo

Public repository for reusable agent documentation, conventions, and templates.

Private data and personal overlays live in a separate private repo
(`<private-repo>`, user-defined name).

## Monorepo Philosophy (Multi-Repo Execution)

The original monorepo philosophy still applies. We now execute it as a logical
monorepo split across repositories by sensitivity:

1. Keep architecture/workflow context close to where work happens.
2. Keep domain names consistent across repos (`journal`, `memory`, etc.).
3. Keep bootstrap context deterministic.
4. Split by data sensitivity, not by ownership.

Repository roles:
- `liferepo`: public canonical docs and agent specs.
- `georgeskills`: modular executable tooling.
- `<private-repo>`: private state, records, and personal overlays.

## What Belongs Here

- Public-safe agent specs and workflows
- Shared governance docs and templates
- Prompt quality/reference material

## What Does Not Belong Here

- Personal journals and private records
- Company-confidential data
- Credentials/tokens/secrets

## Folder Structure (Flat by Domain)

All agent domains now live at repo root for clarity.

```text
liferepo/
  AGENTS.md
  AGENT.md
  SOUL.md
  IMPROVEMENTS.md
  business/
  career/
  communications/
  data-ownership/
  deep-exploration/
  docs/
  health/
  housing/
  journal/
  knowledge/
  memory/
  principles/
  resume/
  social-media/
  templates/
  writing/
```

## Domain Pattern

Each domain should generally include:

- `AGENT-<domain>.md`
- `README.md`
- `IMPROVEMENTS.md`

## Relationship to Skills

Execution-heavy scripts stay in `georgeskills`. This repo remains documentation
first.

## Private Repo Bootstrap

From `liferepo/`:

`python3 ../georgeskills/scripts/bootstrap_private_repo.py --name my-private-repo --create`

Then confirm:

1. `liferepo/.liferepo/local/private_repo.json`
2. `<private-repo>/.liferepo-private.json`

Boundary/pointer rules:
- `docs/BOUNDARY_CONTRACT.md`
- `docs/PRIVATE_REPO_POINTER_CONTRACT.md`
