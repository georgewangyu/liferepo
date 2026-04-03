---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/AGENT"
doc_type: "agent_spec"
doc_status: "active"
title: "Rules for AI Assistants"
description: "This repository is the public, reusable agent framework layer."
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:AGENT.md"
  - "visibility:public"
  - "type:agent_spec"
---
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
- Cross-domain operating policy belongs in `docs/ASSISTANT_OPERATING_MANUAL.md`.
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
- Runtime private execution quirks should live in `<private-repo>/PRIVATE_RUNTIME.md`.
- Keep only a public template in this repo (`templates/SOUL.template.md`).
- Keep only a public runtime template in this repo (`templates/PRIVATE_RUNTIME.template.md`).
- Daily workflow style preferences can be loaded from `<private-repo>/journal/PRIVATE-journal.md`.
- Runtime tools should resolve private state via pointer config:
  - env: `LIFEREPO_PRIVATE_ROOT` (preferred)
  - env: `PRIVATE_REPO_ROOT` (fallback)
- For first-run setup, bootstrap with:
  `python3 ../georgeskills/scripts/bootstrap_private_repo.py --name <your-private-repo> --create`
- Detailed rules: `docs/PRIVATE_REPO_POINTER_CONTRACT.md`.

## Quality Bar

- Prefer small, reversible changes.
- Keep docs concise and pointer-based.
- Explicitly document tradeoffs for non-obvious decisions.
- Treat commit-format and hook rules in `docs/ASSISTANT_OPERATING_MANUAL.md` as
  mandatory.

## Public Publication Guard

- Treat `liferepo` as eventually public.
- Before commit or push, staged changes must pass the repo's public-safety
  validation in `.githooks/public-safety-check.py`.
- That validation is meant to catch obvious publication mistakes in staged
  additions: local identity strings derived from git/home config, non-placeholder
  email addresses, absolute local filesystem paths, and common secret material.
- If a change intentionally needs a real identifier, stop and get explicit human
  confirmation before committing.

## Document Header Contract

- Every markdown document must start with YAML frontmatter.
- New docs must include at minimum:
  - `doc_schema`
  - `doc_id`
  - `doc_type`
  - `doc_status`
  - `title`
  - `description`
  - `doc_tags`
  - `memory_eligible`
  - `memory_priority`
- Runtime usage statistics such as access count and last accessed timestamp must
  not be stored in doc headers; keep those in the memory access index/log.
