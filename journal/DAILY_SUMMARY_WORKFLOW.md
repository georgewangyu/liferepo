---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/journal/DAILY_SUMMARY_WORKFLOW"
doc_type: "workflow_spec"
doc_status: "active"
title: "Agent: Daily Summary Builder"
description: "Maintain one daily summary per date:"
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:journal"
  - "visibility:public"
  - "type:workflow_spec"
---
# Agent: Daily Summary Builder

## Goal

Maintain one daily summary per date:

```text
<private-repo>/journal/summaries/YYYY/MM/YYYY-MM-DD_Summary.md
```

Use an incremental-throughout-day model, then finalize with an end-of-day
interview.

Deep sprint planning convention:
- The summary for a given date records what actually happened on that date.
- If the end-of-day retrospective produces concrete next-day priorities or
  sprint suggestions, write those into tomorrow's summary file, not only into
  today's `Tomorrow Priorities` section.
- A tomorrow file in `planned` state is a planning artifact first. It should
  contain concrete next-day priorities and a `Deep Sprint Plan` / equivalent
  sprint-planning section even before the day has happened.

Companion ingestion spec:
- `DAILY_SUMMARY_WORKFLOW_DATA_INGESTION.md`

## Two-Phase Model

## Phase 1: Incremental Capture

During normal chat/work, append relevant facts as rough bullets:

- wins and outcomes
- blockers/challenges
- decisions
- people interactions
- health/energy context
- notable purchases, receipts, or spending events when they help explain the day
- priorities and unfinished work

Do not block on polish during this phase.

## Phase 2: End-of-Day Finalization

Finalize by running:

1. data freshness checks
2. metrics capture
3. reflection interview
4. synthesis and cleanup

When prep data is available and a same-day summary file already exists, carry
forward the objective context into the summary before the interview instead of
leaving it only in terminal output. In practice that usually means updating
`Health Context`, `Location Context`, and other relevant objective sections
after prep succeeds.

## Morning Cue Protocol

If user starts with `morning`, `start of day`, or similar:

```bash
python3 <private-repo>/scripts/journal/morning_brief.py --date YYYY-MM-DD
```

If brief reports `watch`/`alert`, surface that before sprint planning.

## Private Overlay Hook

If present, load:

```text
<private-repo>/journal/PRIVATE-journal.md
```

before applying narrator tone or private style preferences.

## Data Inputs (Before Interview)

Use these when available:

- Apple Notes export context
- email export context
- calendar context
- health context
- optional location context
- same-day git history context
- DJI audio transcripts for the date (see below)

When email context includes receipts, orders, or transaction confirmations,
carry forward the important ones into the summary body when they are relevant
to behavior, diet, travel, logistics, or money. Do not leave them only in prep
output if they materially explain what happened that day.

### Audio Transcript Ingestion

Check for DJI transcripts at:
```text
dji-audio/transcripts/YYYY/MM/
```

If transcripts exist for the date:
1. Read all clips for the date.
2. Strip obvious MLX hallucination artifacts (repeated identical phrases, zero-duration segments).
3. Run LLM interpretation: detect likely language errors (e.g. Whisper mislabeling language), infer speakers from context clues, flag low-confidence segments.
4. Produce a speaker-labeled pass. Use best-guess speaker names from context; George can correct later.
5. Tag each meaningful segment with one or more domain tags (same tag vocabulary as `Conversation Milestones`): `[workflow]`, `[people]`, `[health]`, `[travel]`, `[work]`, `[personal]`, `[meta]`, etc.
6. Write the result into `## Audio Log — YYYY-MM-DD` in the day's summary.
7. Pull high-signal items (decisions, people interactions, travel events) up into `## People / Relationships`, `## Key Decisions`, and `## Conversation Milestones` as appropriate.

Recommended helper commands:

```bash
python3 <private-repo>/scripts/exports/apple-notes/export_apple_notes.py
python3 <private-repo>/scripts/exports/email/export_emails_gmail_api.py
python3 <private-repo>/scripts/exports/calendar/export_calendar_google.py

python3 <private-repo>/scripts/journal/print_health_interview_context.py --date YYYY-MM-DD
python3 <private-repo>/scripts/journal/print_email_interview_context.py --date YYYY-MM-DD
python3 <private-repo>/scripts/journal/print_location_interview_context.py --date YYYY-MM-DD
```

## Interview Order

Ask in this order:

1. Daily metrics:
   - Energy (1-5)
   - Mood (1-5)
   - Focus (1-5)
   - Productivity (1-5)
2. Optional meal check-in:
   - lunch summary
   - post-lunch crash yes/no
3. Reflection prompts:
   - deep sprint review
   - one challenge
   - one win
   - notable people interactions
   - key decisions
   - top priorities for tomorrow
   - mood sentence and why

## Sprint Check-in (Recommended)

For each day, capture:

- morning sprint (hardest/most important)
- work-hour sprints
- evening sprints
- light blocks

Track domain tags:

- `Job/Interview/Skills`
- `Content`
- `Personal Project`
- `Business/Corp`

## Output Contract

Write/update:

```text
<private-repo>/journal/summaries/YYYY/MM/YYYY-MM-DD_Summary.md
```

Public reference example:

```text
journal/examples/summaries/2026/03/2026-03-24_Summary.md
```

Minimum sections:

- Today at a Glance
- Daily Metrics
- Health Context
- Location Context
- Sprints Today
- Deep Sprint Plan
- Highlights
- Challenges
- Key Decisions
- People / Relationships
- Tomorrow Priorities

Common optional sections when they add signal:

- Reflections
- Notes Highlights
- Important Emails
- Purchases / Spending
- Conversation Milestones
- Narrator Notes

## Stable Section Schema

Use these exact section titles when possible. The structured-memory extractor
relies on them, so naming drift should be treated as a schema change, not just
stylistic variation.

Recommended stable headers:

- `Today at a Glance`
- `Daily Metrics`
- `Health Context`
- `Location Context`
- `Sprints Today`
- `Deep Sprint Plan`
- `Light Block Plan`
- `Highlights`
- `Challenges`
- `Key Decisions`
- `People / Relationships`
- `Tomorrow Priorities`
- `Purchases / Spending`
- `Notes Highlights`
- `Important Emails`
- `Conversation Milestones`
- `Narrator Notes`
- `Reflections`

Preferred normalization rules:

- Prefer `Tomorrow Priorities`, not `Tomorrow`.
- Prefer `People / Relationships`, not separate ad hoc people headers.
- Prefer `Conversation Milestones` as one section. Subsections inside it are
  fine, but do not rename the parent section casually.
- Prefer `Narrator Notes` for pattern-level interpretation rather than
  scattering that tone into unrelated sections.

## Section Semantics

Use each section for a distinct kind of memory signal:

- `Sprints Today`: what actually happened. Use this for the real executed deep
  sprints, partial conversions, misses, and how the day actually unfolded.
- `Deep Sprint Plan`: the opening plan or intended sprint structure for that
  date. This can differ from reality. Use it while the day is still planned or
  actively unfolding, but once the real executed sprints are captured clearly
  in `Sprints Today`, remove `Deep Sprint Plan` instead of keeping both
  sections around forever.
- `Highlights`: concrete wins, shipped outputs, or objectively good outcomes.
- `Challenges`: obstacles, repeated failure modes, or constraints that mattered
  to the day.
- `Key Decisions`: decisions or operating rules likely to matter again.
- `People / Relationships`: notable interactions, social context, and durable
  relationship signals. Use `No notable people interactions...` when there was
  nothing worth capturing.
- `Tomorrow Priorities`: real next-step commitments, not vague aspirations.
- `Conversation Milestones`: meaningful chat-derived progress, tool changes,
  repo changes, workflow upgrades, and other important developments that should
  not live only in chat history.
  **Categorization**: Each milestone bullet should be prefixed with a domain tag
  in square brackets to make the section scannable and to aid downstream
  extraction into `agent-managed/` and `memory/`. Use one of the following
  canonical tags, or introduce a new one when none fits:
  - `[infra]` — repo structure, tooling, scripts, automation, CI/CD
  - `[product]` — shipped features, UI, UX, frontend/backend integration
  - `[outreach]` — emails sent, proposals, CRM, cold outreach, partnerships
  - `[knowledge]` — research, wiki updates, knowledge-base changes
  - `[health]` — health data pipeline, metrics, imports
  - `[workflow]` — daily workflow, journal, sprint schema, process changes
  - `[content]` — social media, video editing, posts, distribution
  - `[conversation]` — distilled conversation note signal
  Example format: `- [product] Deepened the ADA Engagement Loop: connected /commenting/ to backend...`
- `Narrator Notes`: compact pattern recognition or causal interpretation that
  helps future retrieval.
- `Purchases / Spending`: only when transactions materially explain behavior,
  diet, logistics, travel, or money.

## Memory Extraction Mapping

Current structured-memory extraction assumes:

- `Key Decisions` -> `decision`
- `Tomorrow Priorities` -> `commitment`
- `People / Relationships` -> `person`
- `Conversation Milestones` -> `status_change`
- `Challenges` -> `pattern`
- `Narrator Notes` -> `pattern`

If you introduce a new section that should feed memory extraction, update the
extractor and this workflow spec together.

Validation helper:

```bash
python3 <private-repo>/scripts/journal/check_daily_workflow_completeness.py --date YYYY-MM-DD
```

This check now also flags missing stable headers for active summaries.

## Status Header

Use YAML frontmatter.

Daily summaries must include the standard doc header contract
(`doc_schema`, `doc_id`, `doc_type`, `doc_status`, `title`, `description`,
`doc_tags`, `memory_eligible`, `memory_priority`) plus `summary_status`.

Example:

```yaml
doc_schema: "doc-frontmatter-v1"
doc_id: "<private-repo>/journal/summaries/2026/03/2026-03-28_Summary"
doc_type: "daily_summary"
doc_status: "active"
title: "Daily Summary — 2026-03-28"
description: "One-line summary of the day."
doc_tags:
  - "domain:journal"
  - "visibility:private"
  - "type:daily_summary"
memory_eligible: true
memory_priority: "high"
summary_status: planned | partial | completed
```

Definitions:

- `planned`: summary file initialized, interview/finalization not yet run
- `partial`: meaningful content captured, still materially incomplete
- `completed`: workflow completed with best available data

For a next-day file in `planned` state:
- prefer concrete proposed sprints over generic placeholders
- make it obvious the file is a plan for that date, not a claim that the date
  has already happened
- update or replace the plan once the real day starts and incremental capture
  begins
- once `Sprints Today` has been filled in with the actual day, drop the now-stale
  `Deep Sprint Plan` section rather than preserving duplicate planned text

## Quality Rules

- Keep summaries specific and retrieval-friendly.
- Separate objective telemetry from subjective ratings.
- Avoid duplicating raw export dumps in the summary body.
- Preserve high-signal derived facts from ingestion, including notable receipts
  or purchases, so future review does not depend on rerunning exporters.
- Keep personal style preferences in private overlays, not public spec.
- `Conversation Milestones` should stay factual but can retain George's voice
  and judgment.
- `Narrator Notes` are optional but recommended when they help distill the
  day's pattern in a sharper, more voiceful way. They should feel like vivid
  pattern-calling, not generic encouragement.

## LLM Synthesis Handoff

Before moving to the final end-of-day planning handoff, check what the automated agents extracted and perform manual synthesis:

1. Review the generated `agent-managed/_candidates/` and `agent-managed/log.md` outputs.
2. Cross-reference the highlights from `Today at a Glance` and `Conversation Milestones`.
3. Use your LLM capabilities to identify relevant canonical topics in `agent-managed/topics/` or `memory/*.jsonl` and actively rewrite their `Current Understanding` sections to reflect today's new context.
4. Do not solely rely on the Python script's naive bullet extraction. Ensure the wiki genuinely compounds and connects insights semantically.

## End-Of-Day Planning Handoff

At the end of the daily workflow, if tomorrow priorities are clear:

1. Keep the final day's `Tomorrow Priorities` section concise.
2. Also create or update tomorrow's summary file with:
   - `summary_status: planned`
   - a short `Today at a Glance` planning note
   - a concrete `Deep Sprint Plan`
   - any important operating constraints, such as calendar load, recovery
     needs, or energy risks
3. Never leave the next-day planning file as a blank stub if the retrospective
   already surfaced a concrete plan.
4. Once tomorrow becomes today and the real sprint record is written into
   `Sprints Today`, remove the old `Deep Sprint Plan` block unless it still
   serves a specific comparative purpose.
