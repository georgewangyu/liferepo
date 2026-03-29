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
- Cross-domain public agent specs should live under `agents/`.
- Every new top-level area must include:
  - `README.md`
  - `AGENT-<area>.md`
  - `IMPROVEMENTS.md`
- If top-level structure changes, update the root `README.md` structure section
  in the same change.

## Modularity Rules

- Skills and execution-heavy automations should be packaged as modular skills
  in `georgeskills` (or separate repos).
- Keep this repo focused on guidance, conventions, templates, and examples.
- If a script is included here, it must be public-safe and generic.
- Use the same domain folder names across repos (`journal`, `memory`, etc.)
  for clarity, but keep one canonical home per artifact.

## Private Repo Pointer Contract

- Do not hardcode personal repo names in public docs.
- Use `<private-repo>` as the documentation placeholder.
- Prefer name-based local pointer config (`private_repo_name`) over raw paths.
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
