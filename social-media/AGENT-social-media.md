---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/social-media/AGENT-social-media"
doc_type: "agent_spec"
doc_status: "active"
title: "AGENT-social-media"
description: "Define reusable cross-platform workflows for video, short-form text promotion,"
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:social-media"
  - "visibility:public"
  - "type:agent_spec"
---
# AGENT-social-media

## Purpose

Define reusable cross-platform workflows for video, short-form text promotion,
and long-form article distribution.

## Canonical Content Models

- Short-form video: `hook -> beat -> beat -> twist`.
- Short-form text (posts/threads): `hook -> development -> value -> engagement`.
- Long-form article: `hook -> beat 1 -> beat 2 -> beat 3 -> twist -> resolution`.

## Global Workflow

1. Choose platform and objective (reach, engagement, conversion).
2. Generate multiple hooks before drafting body copy.
3. Select one structure and one core takeaway.
4. Draft platform-native version first.
5. Produce repurposed variants for the other channels.
6. Attach explicit CTA and distribution plan.

## Platform Rules

### Short-Form Video

- Prioritize human, specific, experience-backed hooks over generic advice.
- Keep each beat focused on one progression step.
- Make the twist non-obvious but still defensible from the story.
- Use natural language that is easy to film directly.

### Short-Form Text Promotion

- Extract snippets from long-form assets or concrete experiences.
- Keep curiosity high while withholding full detail.
- Adapt format by platform:
  - X/Threads: compact primary post + continuation comments where needed.
  - LinkedIn: longer, readable blocks with a clear professional takeaway.
- Keep external-link placement and CTA strategy platform-aware.

### Long-Form Distribution

- Bias to quality over frequency; every article should deliver substantive value.
- Use staged workflow: planning -> drafting -> review -> distribution.
- For newsletter/article launches, support teaser-first distribution across social channels.
- Use future-date scheduling when launch strategy benefits from pre-release subscription intent.

## Quality Filters

- Specific, experience-based claims over broad motivational claims.
- Clear progression and pacing with one dominant narrative arc.
- Actionable value and explicit CTA.
- Format matches platform expectations without copy-paste artifacts.
- Claims remain factual and reproducible.

## Required Companion Specs

- `PLATFORM_PROMOTION_WORKFLOW.md`
- `SUBSTACK_DISTRIBUTION_WORKFLOW.md`

## Repository Boundary

- Public workflow specification lives in `liferepo/social-media/`.
- Private creator profile details, account data, and historical performance data stay in `<private-repo>/social-media/`.
