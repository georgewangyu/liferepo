---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/README"
doc_type: "readme"
doc_status: "active"
title: "liferepo"
description: "Public agent framework and personal operating system specs."
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:README.md"
  - "visibility:public"
  - "type:readme"
---
# liferepo

A personal operating system for AI-assisted life management — public specs,
agent workflows, and reusable templates.

Your private data lives in a separate repo you own. This repo is the framework
that makes it all work.

---

## Philosophy

Most people's work and thinking exist in chat histories, scattered notes, and
context that evaporates between sessions. AI assistants are powerful but
stateless — every session starts cold unless you build something that keeps
state alive.

This system treats your life the same way good software treats a product:

- **Version-controlled context.** Everything important is a file. Files have
  history, diffs, and structure. AI can read them reliably.
- **Domain-driven organization.** Your life has recurring domains — health,
  career, journal, business, communications. Each gets its own folder with
  consistent structure. The AI learns your domains by reading folder structure,
  not by you re-explaining them every session.
- **Agent specs as contracts.** Every domain has an `AGENT-*.md` file that
  defines what an AI assistant should know and do in that area. These are
  not prompts — they are persistent behavioral contracts.
- **Public framework, private state.** The workflows, templates, and agent
  specs are generic and shareable. Your actual data — journals, health
  records, financial notes, personal overlays — lives in a private repo that
  only you control.
- **Executable skills, not just docs.** Heavy automation lives in a companion
  repo (`georgeskills`) as modular skills the AI can invoke. Docs and execution
  are separated so this repo stays clean and auditable.

The goal is a system where starting a new AI session feels like picking up
where you left off — not starting over.

---

## System Architecture

```
liferepo/               ← you are here (public framework)
georgeskills/           ← modular skills + executable tooling
<private-repo>/         ← your personal data, state, and overlays
```

Each layer has a distinct job:

| Layer | Role | Examples |
|---|---|---|
| `liferepo` | Public specs, agent contracts, templates, examples | `AGENT-journal.md`, `DAILY_SUMMARY_WORKFLOW.md`, `SOUL.template.md` |
| `georgeskills` | Executable skills, export scripts, automation | `x-check-ops`, `journal-ops`, `health-ops` |
| `<private-repo>` | Your private records, overlays, and state | `journal/summaries/`, `SOUL.md`, `notes-private/` |

**Rule**: information flows one way. Public specs reference private data via
`<private-repo>` placeholder. Private overlays extend public specs without
modifying them. Skills read private data but live in `georgeskills`, not in
your private repo.

---

## Folder Structure

Every domain follows the same pattern:

```
<domain>/
  README.md           ← what this domain contains and how it works
  AGENT-<domain>.md   ← behavioral contract for AI assistants
  IMPROVEMENTS.md     ← backlog and known gaps
  examples/           ← public-safe sample artifacts (optional)
```

Root layout:

```
liferepo/
  AGENTS.md                      ← session bootstrap entrypoint
  AGENT.md                       ← root-level rules for AI assistants
  README.md                      ← this file
  IMPROVEMENTS.md                ← repo-wide backlog

  business/                      ← SaaS templates, market research workflows
  career/                        ← job search, interviews, career planning
  communications/                ← email and calendar workflows
  data-ownership/                ← personal data export runbooks
  deep-exploration/              ← research and investigation workflows
  docs/                          ← governance, contracts, operating manual
  health/                        ← health data pipeline and Apple Health workflows
  housing/                       ← housing search and tracking
  journal/                       ← daily summary workflow, sprint system
  knowledge/                     ← knowledge base and synthesis workflows
  memory/                        ← agent memory specs and extraction contracts
  principles/                    ← operating principles and decision frameworks
  resume/                        ← resume review, ATS optimization, templates
  social-media/                  ← platform-specific content workflows
  templates/                     ← SOUL.template.md, PRIVATE_RUNTIME.template.md
  writing/                       ← writing style and voice specs
```

---

## How Agents Work in This System

### AGENTS.md (session bootstrap)

`AGENTS.md` is the first file an AI assistant reads at the start of a session.
It is intentionally short and pointer-style. It tells the assistant what to
load next and in what order.

For sessions in this repo, the load order is:

1. `AGENT.md` — root rules
2. `docs/ASSISTANT_OPERATING_MANUAL.md` — commit format and runtime policy
3. `README.md` — this file
4. `<private-repo>/SOUL.md` — your personal voice and identity (private)
5. `<private-repo>/PRIVATE_RUNTIME.md` — local environment quirks (private)

### AGENT-*.md (domain contracts)

Each domain has an `AGENT-<domain>.md` that defines:

- what the assistant should know about this domain
- what workflows to run for common triggers
- what output the assistant should produce
- where to write results

These files are written once and updated incrementally. They function like
persistent system prompts scoped to a domain — but versioned in git.

### SOUL.md (private, per-user)

`SOUL.md` lives in your private repo. It contains your personal context:
who you are, your goals, your voice preferences, and anything an assistant
needs to be useful to you specifically. A public template is at
`templates/SOUL.template.md`.

### agent-managed/

`agent-managed/` is a directory in your private repo where the AI maintains
a living knowledge wiki extracted from your journals and conversations. It
contains:

- `topics/` — synthesized notes per topic (e.g., "career", "health-patterns")
- `indexes/` — cross-reference indexes across topics
- `_candidates/` — pending items from recent sessions
- `log.md` — extraction audit log

This is not a manual notes folder. It is written by the AI, not by you. You
review and correct it. The AI compounds knowledge here over time so insights
from one month's journal entries are available in future sessions without
re-reading everything.

---

## Daily Summary System

The journal system is the core workflow. Each day gets one summary file:

```
<private-repo>/journal/summaries/YYYY/MM/YYYY-MM-DD_Summary.md
```

Summaries have a two-phase model:

- **Phase 1 — Incremental capture**: throughout the day, the AI appends
  wins, blockers, decisions, and notes to the day's file.
- **Phase 2 — End-of-day finalization**: a structured interview produces
  the final summary with metrics, sprint review, and tomorrow's priorities.

The morning brief script reads the current day's file plus health/calendar
context and surfaces anything that needs attention before you start:

```bash
python3 <private-repo>/scripts/journal/morning_brief.py --date YYYY-MM-DD
```

### Example: completed daily summary

See `journal/examples/summaries/2026/03/2026-03-24_Summary.md` for a
public-safe completed example.

```
## Today at a Glance
- Solid morning focus block before meetings.
- Workday shifted into coordination and review.
- One content draft shipped in the evening.

## Daily Metrics
| Metric       | Value |
|--------------|-------|
| Energy (1–5) | 3     |
| Mood (1–5)   | 3     |
| Focus (1–5)  | 4     |
| Productivity | 3     |

## Sprints Today
Morning sprint: system-design prep — [Job/Interview/Skills]
Work sprints: reliability triage + async design review — [Job/Interview/Skills]
Evening sprint: content draft — [Content]

## Key Decisions
- Protect one no-meeting morning block tomorrow.
- Timebox inbox to avoid spillover into deep-work windows.

## Tomorrow Priorities
- Two interview-prep loops (system design + behavioral).
- Batch and schedule two content posts.

## Narrator Notes
Morning was sharp, mid-day was noisy, evening was controlled.
The day worked because priorities were narrowed instead of expanded.
```

---

## Sprint System

Sprints are two-week planning periods. Each sprint has a planning file:

```
<private-repo>/journal/sprints/YYYY-QN_Sprint-NN_YYYY-MM-DD_to_YYYY-MM-DD.md
```

Sprints define:

- a theme and success criterion
- domain allocation targets (Job/Interview/Skills, Content, Personal Project, Business)
- specific sprint goals (3–6 maximum)
- a backlog by domain
- a mid-sprint check-in section
- a retrospective section at the end

See `journal/examples/sprints/` for a public-safe example.

---

## Setup

### Prerequisites

- macOS (Apple Silicon recommended for MLX features)
- Python 3.11+ (ARM64 for Apple Silicon: `/opt/homebrew/bin/python3`)
- Git
- An AI assistant that can read files (Claude Code, Cursor, OpenAI Codex)

### 1. Clone the public repos

```bash
git clone https://github.com/<user>/liferepo
git clone https://github.com/<user>/georgeskills
```

Place them as siblings in the same parent directory:

```
Workspace/
  liferepo/
  georgeskills/
  <your-private-repo>/    ← created in the next step
```

### 2. Enable git hooks

From `liferepo/`:

```bash
git config core.hooksPath .githooks
chmod +x .githooks/commit-msg .githooks/pre-commit
```

Do the same from `georgeskills/`.

The pre-commit hook in each repo runs a public-safety scan that blocks
accidental commits of local paths, email addresses, and credential strings.

### 3. Bootstrap your private repo

The bootstrap script creates your private repo and scaffolds its structure.
Run from `liferepo/`:

```bash
# Guided interactive setup (recommended for first-time users)
python3 ../georgeskills/scripts/bootstrap_private_repo.py \
  --name my-private-repo \
  --create \
  --interactive

# Or non-interactive with all modules
python3 ../georgeskills/scripts/bootstrap_private_repo.py \
  --name my-private-repo \
  --create \
  --init-journal \
  --init-resume \
  --init-exports
```

The interactive flow prompts you to draft `SOUL.md` and `PRIVATE_RUNTIME.md`
before scaffolding folders.

After bootstrapping, confirm these files exist:

```
liferepo/.liferepo/local/private_repo.json     ← pointer from liferepo to your private repo
<private-repo>/.liferepo-private.json          ← marker in your private repo
<private-repo>/SOUL.md                         ← your personal context
<private-repo>/PRIVATE_RUNTIME.md             ← local environment notes
```

### 4. Install georgeskills

From `georgeskills/`:

```bash
./scripts/sync-to-codex.sh
```

This symlinks all skills into `~/.codex/skills/` so your AI assistant can
load them by name.

### 5. Configure optional integrations

See `docs/PRIVATE_REPO_SETUP.md` for setup guides for:

- Gmail API (email export)
- Google Calendar API (calendar export)
- Apple Notes export (macOS automation)
- Health data pipeline (Apple Health)

### 6. Load the workspace in your AI assistant

Point your AI assistant at the workspace root. For Claude Code, a
`CLAUDE.md` at the workspace root auto-loads the routing rules. See
`docs/ASSISTANT_OPERATING_MANUAL.md` for session startup requirements.

---

## Resume System

The resume system lives in `resume/`. It provides:

- ATS optimization rules
- JD-tailoring decision workflow
- Bullet and summary rewrite prompt patterns
- Variant strategy by role family

Example output lives at `resume/examples/senior-swe/`:

```
resume/examples/senior-swe/
  Sample_Senior_SWE_Resume.tex    ← LaTeX source
  Sample_Senior_SWE_Resume.pdf    ← built output
```

The build workflow uses a local LaTeX install or Docker. See
`resume/DOCUMENT_CONVERSION_WORKFLOW.md`.

---

## Relationship to georgeskills

`liferepo` is documentation-first. Heavy execution logic lives in
`georgeskills`:

- export scripts (Gmail, Google Calendar, Apple Notes, X/Twitter)
- transcription pipeline (MLX Whisper for Apple Silicon)
- morning brief runner
- health context printer
- memory extraction scripts
- skill definitions for the AI assistant

See `georgeskills/README.md` for the full skill catalog and install guide.

---

## Private Repo Contract

- Public specs use `<private-repo>` as a placeholder. Never hardcode a
  personal repo name in this repo.
- Private overlays extend public specs without modifying them.
- The detailed boundary rules are in `docs/BOUNDARY_CONTRACT.md` and
  `docs/PRIVATE_REPO_POINTER_CONTRACT.md`.
- `SOUL.md` is intentionally private. The public template is at
  `templates/SOUL.template.md`.
