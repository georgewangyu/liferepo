---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/business/saas-templates/README"
doc_type: "readme"
doc_status: "active"
title: "SaaS Templates Workspace"
description: "Step-by-step workspace for choosing and launching a SaaS template with clear next actions."
memory_eligible: true
memory_priority: "medium"
doc_tags:
  - "domain:business"
  - "visibility:public"
  - "type:readme"
---
# SaaS Templates Workspace

Step-by-step workspace for choosing and launching a SaaS template with clear
execution gates.

## Genesis

Created from user request: "Let's start a folder in liferepo regarding saas
templates and explain to me what next steps are."

## Scope

- Pick a sane SaaS starter without overengineering.
- Define a concrete v1 build path (from scaffold to private trial).
- Keep decisions visible so work can resume quickly after interruptions.

## Step-by-Step Plan

1. Define v1 constraints (30-45 min).
2. Select template candidate and reject alternatives with reasons (45-60 min).
3. Lock naming, repo location, and deployment target (20-30 min).
4. Scaffold app and run it locally end-to-end (60-90 min).
5. Build first vertical slice: idea input -> draft generation workflow
   skeleton (2-4 hours).
6. Run 1-week private usage trial and collect friction log (5-7 days).

## Default Build Pattern

For most SaaS projects, the safest default sequence is:

1. Lock the product spine: user, problem, primary action, and non-goals.
2. Build the frontend shell: marketing page, app frame, and key route skeletons.
3. Build one real vertical slice that proves user value.
4. Add auth, persistence, and backend only as needed to support that slice.
5. If the product is subscription-backed, add the billing spine next:
   - pricing + entitlement policy
   - hosted checkout + billing portal
   - webhook-backed subscription state
   - single entitlement API for every client
6. Repeat outward from the core workflow instead of widening the app randomly.

The practical shorthand is:

- frontend shell
- first vertical slice
- persistence/backend around that slice
- subscription workflow if recurring revenue is core
- repeat

What to avoid:

- building every page before any workflow works
- overbuilding backend before one user action is proven
- bolting subscriptions on after auth and client UX have already drifted apart
- mistaking the starter template for the product itself

## Immediate Next Actions (Today)

- Write a one-page v1 scope: user, problem, non-goals, success metric (30 min).
- Choose template now (recommended default: `nextjs/saas-starter`) and record
  why (20 min).
- Generate scaffold and validate baseline run (`dev`, auth flow, db connection)
  (60 min).

## Decision Log Format

Use this folder to capture each key decision in this compact format:

- Decision:
- Why:
- Tradeoff accepted:
- Revisit trigger:

## Related Docs

- `../SAAS_PRODUCT_DEFAULTS.md`
- `../AGENT-business.md`
- `AGENT-frontend-design.md`
- `SUBSCRIPTION_SETUP_WORKFLOW.md`
- `FRONTEND_DESIGN_WORKFLOW.md`
- `MARKET_OPPORTUNITY_SHORTLIST.md`
