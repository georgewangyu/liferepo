# liferepo

Public repository for reusable agent documentation, conventions, and templates.

This repository is intentionally separated from private personal operations.
Private journaling and personal records live in a separate private repository
(`private-repo`, name chosen by each user).

## What Belongs Here

- Agent bootstrap and policy patterns (`AGENTS.md`, `AGENT.md`, `AGENT-*.md`)
- Reusable documentation frameworks
- Prompt quality frameworks and review checklists
- Public-safe templates and examples

## What Does Not Belong Here

- Personal journals or reflections
- Health, finance, housing, or private family data
- Company-confidential material
- API credentials, tokens, or secrets

## Structure

```
liferepo/
├── AGENTS.md          # Bootstrap loader
├── AGENT.md           # Core repository rules
├── SOUL.md            # Collaboration style baseline
├── IMPROVEMENTS.md    # Public framework backlog
├── agents/            # Canonical agent catalog (career, writing, social, etc.)
├── docs/              # Policies, architecture, and split decisions
├── journal/           # Public journal agent/workflow specifications
├── memory/            # Public memory schema and agent specifications
├── health/            # Public health workflow/agent specifications
├── deep-exploration/  # Public exploration workflow/agent specifications
├── resume/            # Public resume-agent workflow specifications
└── templates/         # Starter templates for new agent areas
```

## Relationship to Skills

Execution-heavy scripts and modular automation belong in `georgeskills`.
This keeps `liferepo` focused on public framework documentation instead of
environment-specific operational scripts.

`agents/` contains additional reusable agent domains that were previously mixed
into private repos (for example business, communications, social media,
knowledge, principles, and job-hunting workflows).

## Private Repo Bootstrap

Each user should keep private state in a separate sibling repository (name is
user choice, for example `my-private-repo`).

1. Run bootstrap (from `liferepo/`):
   `python3 ../georgeskills/scripts/bootstrap_private_repo.py --name my-private-repo --create`
2. Confirm `liferepo/.liferepo/local/private_repo.json` exists.
3. Confirm `<private-repo>/.liferepo-private.json` exists.
4. Optionally export `LIFEREPO_PRIVATE_ROOT` in shell profile.

Notes:
- `private_repo_name` is the canonical setting for portability.
- Bootstrap writes name-only config for standard sibling layouts.
- `private_repo_path` can be added as an optional local override.

Boundary details and ownership rules are defined in:
- `docs/BOUNDARY_CONTRACT.md`
- `docs/PRIVATE_REPO_POINTER_CONTRACT.md`
