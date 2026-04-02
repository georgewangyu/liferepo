---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/knowledge/PERSONAL_PROFILE_CAPTURE_WORKFLOW"
doc_type: "workflow_doc"
doc_status: "active"
title: "Personal Profile Capture Workflow"
description: "Reusable workflow for capturing durable facts about the human over time and routing them into profile artifacts."
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:knowledge"
  - "visibility:public"
  - "type:workflow_doc"
---
# Personal Profile Capture Workflow

## Purpose

When repeated conversations reveal durable facts about the human, do not leave
those facts only in transient chat history or day logs. Capture them in the
appropriate private profile artifacts so the system gets better at knowing its
human over time.

## What To Capture

Capture facts that are:

- durable rather than one-off
- useful for future reasoning or decisions
- identity-level, preference-level, or constraint-level
- likely to matter across multiple domains

Examples:

- recurring preferences and dislikes
- stable work styles and attention patterns
- social or cultural context that affects decisions
- repeated health-adjacent constraints at a profile level
- favorite environments, foods, routines, or failure modes

## Routing Rules

Route captured information into the private repo, not `liferepo`.

- Use `<private-repo>/knowledge/personal/profile.md` for concise durable traits,
  constraints, tendencies, and recurring facts.
- Use `<private-repo>/knowledge/personal/who-i-am/` for more human,
  identity-level notes that describe the person as a whole.
- Keep detailed medical or operational logs in the appropriate private health,
  finance, journal, or domain folders, then add short profile-level references
  only when the pattern is durable enough to matter broadly.

## Capture Strategy

Start small, then split when a real cluster emerges.

1. Add the durable fact to the main profile layer.
2. If the same theme keeps recurring, create or extend a dedicated note for
   that category in `<private-repo>/knowledge/personal/who-i-am/`.
3. Update the local README when the folder structure changes.

Examples of category splits:

- `foods.md`
- `relationships.md`
- `work-style.md`
- `taste.md`
- `identity-shifts.md`

Do not create category files speculatively. Split only when repeated facts make
the category retrieval-useful.

## Quality Bar

- Prefer concrete wording over vague personality labels.
- Preserve the human texture, not just sterile summaries.
- Keep profile notes brief, scan-friendly, and cumulative.
- Link out to supporting docs instead of duplicating long source material.
