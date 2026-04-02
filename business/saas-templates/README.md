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
- `FRONTEND_DESIGN_WORKFLOW.md`
- `MARKET_OPPORTUNITY_SHORTLIST.md`
