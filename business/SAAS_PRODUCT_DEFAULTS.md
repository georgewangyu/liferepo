---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/business/SAAS_PRODUCT_DEFAULTS"
doc_type: "business_doc"
doc_status: "active"
title: "SaaS Product Defaults"
description: "Reusable default stance for early SaaS product architecture."
memory_eligible: true
memory_priority: "medium"
doc_tags:
  - "domain:business"
  - "visibility:public"
  - "type:business_doc"
---
# SaaS Product Defaults

Reusable default stance for early SaaS product architecture.

## Default Stance

- Start with a single product and single database.
- Optimize for time-to-first-paying-user, not architectural prestige.
- Keep frontend and backend together unless separation is clearly justified.
- Explain when infrastructure is unnecessary, not only when it is useful.

## Day 1 Checklist

- minimal product scope
- one deployable app
- one persistent data store
- one billing/activation path
- one feedback loop from real users

## Upgrade Triggers

Only add architecture layers when concrete triggers appear, such as:

- sustained load requiring independent scaling
- hard isolation requirements
- organizational growth creating ownership bottlenecks

## Anti-Patterns

- defaulting to microservices pre-PMF
- adding gateways/queues without measured need
- copying big-company architecture into solo/small-team products
