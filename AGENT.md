# Rules for AI Assistants

This repository is the public, reusable agent framework layer.

## Scope

- Keep this repo focused on reusable agent documentation and templates.
- Do not add personal journals, private company docs, health/finance records,
  credentials, or customer/confidential data.
- If content is personal or sensitive, it belongs in the private data repo
  (configured per user), not here.

## Structure Rules

- Root `AGENTS.md` is a bootstrap entrypoint, not a policy dump.
- Area-specific rules belong in `AGENT-*.md` files near the work.
- All domain specs live at repository root (flat-by-domain).
- Every domain area should include:
  - `README.md`
  - `AGENT-<domain>.md`
  - `IMPROVEMENTS.md`
- If domain structure changes, update root `README.md` in the same change.

## Modularity Rules

- Skills and execution-heavy automations should be packaged as modular skills
  in `georgeskills` (or separate repos).
- Keep this repo focused on guidance, conventions, templates, and examples.
- If a script is included here, it must be public-safe and generic.
- Keep domain folder names consistent across repos for clarity.

## Private Repo Pointer Contract

- Do not hardcode personal repo names in public docs.
- Use `<private-repo>` as the documentation placeholder.
- Prefer name-based local pointer config (`private_repo_name`) over raw paths.
- Runtime personality/voice source of truth is `<private-repo>/SOUL.md`.
- Keep only a public template in this repo (`templates/SOUL.template.md`).
- Runtime tools should resolve private state via pointer config:
  - env: `LIFEREPO_PRIVATE_ROOT` (preferred)
  - env: `PRIVATE_REPO_ROOT` (fallback)
  - env: `GEORGEREPO_ROOT` (legacy compatibility)
- For first-run setup, bootstrap with:
  `python3 ../georgeskills/scripts/bootstrap_private_repo.py --name <your-private-repo> --create`
- Detailed rules: `docs/PRIVATE_REPO_POINTER_CONTRACT.md`.

## Quality Bar

- Prefer small, reversible changes.
- Keep docs concise and pointer-based.
- Explicitly document tradeoffs for non-obvious decisions.
