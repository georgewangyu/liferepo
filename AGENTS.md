# Codex Session Bootstrap

This file is a pointer-style bootstrap. Keep it short.
Substantive rules live in `AGENT.md` and local `AGENT-*.md` files.

## Required Startup Context

At the start of every new session in this repository, read in order:

1. `AGENT.md`
2. `README.md`
3. If configured, load `<private-repo>/SOUL.md` via `.liferepo/local/private_repo.json`.
4. If no private repo is configured yet, use `templates/SOUL.template.md`.

## Directory-Specific Context

When working in a subdirectory:

1. Read the nearest `AGENT-*.md` (or local `AGENT.md`).
2. Read the local `README.md`.
3. Load only task-relevant docs.

## Priority

If instructions conflict:

1. User instructions in chat
2. More specific local docs
3. Root-level repository docs
