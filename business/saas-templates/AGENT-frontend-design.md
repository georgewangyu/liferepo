---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/business/saas-templates/AGENT-frontend-design"
doc_type: "agent_spec"
doc_status: "active"
title: "AGENT-frontend-design"
description: "Reusable agent guidance for SaaS frontend design work, including clone-first baselines, layered design-language systems, and closed-loop validation."
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:business"
  - "domain:frontend-design"
  - "visibility:public"
  - "type:agent_spec"
---
# AGENT-frontend-design

## Purpose

Define a reusable operating model for frontend design work in SaaS projects.

This guidance exists because page-by-page styling drift is too easy. The goal
is to turn frontend quality into a layered, reviewable system instead of a
sequence of one-off taste decisions.

## Core Lessons From Mira / Aster

The first strong frontend pass for Mira, later repositioned as Aster, worked
because the work stopped trying to solve everything in one pass.

The failing pattern was:
- invent brand language
- write product copy
- decide scope
- think about backend shape
- style full pages at the same time

The better pattern was:
- separate frontend quality from backend readiness
- clone one strong reference to lock spacing, hierarchy, and interaction rhythm
- rebuild it as editable local code
- document the design language in layers so future changes stop drifting

## Clone-First Rule

When the team does not yet have a stable visual language, a clone-first move is
allowed and often preferable.

Use a clone-first baseline when:
- the current UI quality is too weak to iterate from
- there is no stable token/primitives system yet
- the team needs a concrete quality bar fast
- the main need is rhythm, hierarchy, and interaction baseline, not originality
  on day 1

The Mira / Aster example used `foaster.ai` as the reference and reimplemented
it structurally in local Next.js routes rather than embedding it blindly.

What mattered was not "copy that site."
What mattered was locking:
- spacing rhythm
- section hierarchy
- interaction energy
- visual confidence

Treat the clone as a scaffold, not the final brand.

## Layer Order

Do frontend work in this order:

1. visual signal
2. tokens
3. primitives
4. shell
5. patterns
6. sections
7. mixes
8. QA

If something looks wrong, fix the lowest relevant layer first.

Examples:
- vibe is wrong -> visual thesis / visual detection
- color or spacing drifts -> tokens
- buttons/forms/cards feel inconsistent -> primitives
- page frame/navigation feels weak -> shell
- repeated interaction is awkward -> patterns
- composition is unclear -> sections or mixes
- finish quality is suspect -> QA

## Design-Language Folder Rule

For serious frontend work, keep an explicit design-language folder or its
equivalent. The folder matters because it prevents the team from rebuilding
frontend decisions from scratch every time messaging or scope changes.

The useful layers from the Mira / Aster pattern were:

1. visual detection
2. design tokens
3. core primitives
4. app shell
5. patterns
6. page sections
7. ready mix
8. QA

These layers are not documentation overhead. They are control surfaces.

## Closed-Loop Validation Rule

Do not trust codegen or static code review alone.

Frontend work should use a closed loop:

1. make the change
2. run the app locally
3. inspect the rendered result in browser
4. capture desktop and mobile screenshots
5. inspect fine visual details closely
6. check browser console output
7. test key states and one edge case
8. patch and repeat

If the rendered UI is wrong, the work is not done, even if the code is clean.

## Editing Boundaries

Keep in frontend-design docs:
- visual-system rationale
- token and primitive rules
- composition and QA standards
- clone-first reasoning when it explains the system

Keep out:
- long product strategy debates
- backend planning
- random inspiration dumps with no applied lesson
- copy experimentation that does not change the design system

## Output Contract

A meaningful frontend design pass should leave behind at least one of:
- a clearer visual rule
- a better token/primitives decision
- a tighter section or pattern definition
- a stronger QA rule based on something that actually broke

If the work does not improve the system, it is probably decoration.

## Companion Docs

- `README.md`
- `FRONTEND_DESIGN_WORKFLOW.md`
