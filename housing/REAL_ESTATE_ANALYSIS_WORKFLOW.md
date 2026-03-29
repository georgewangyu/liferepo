---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/housing/REAL_ESTATE_ANALYSIS_WORKFLOW"
doc_type: "workflow_spec"
doc_status: "active"
title: "Real Estate Analysis Workflow"
description: "Produce data-driven keep/sell/refinance recommendations for investment"
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:housing"
  - "visibility:public"
  - "type:workflow_spec"
---
# Real Estate Analysis Workflow

## Goal

Produce data-driven keep/sell/refinance recommendations for investment
properties.

## Analysis Framework

1. Gather complete financial inputs (target 95% confidence).
2. Calculate baseline performance metrics.
3. Build scenario comparison:
   - keep
   - sell now
   - sell later
4. Evaluate risks, sensitivity, and opportunity cost.
5. Recommend with explicit confidence level.

## Core Metrics

- cash flow (monthly/annual)
- cap rate
- cash-on-cash return
- ROI with appreciation/carry costs
- debt service coverage ratio
- net proceeds under sale scenarios

## Valuation Methods

Use multiple approaches:

1. comparable sales (recent, similar units/properties)
2. market trend context
3. available appraisals/CMA
4. financing context (rate/term/refi potential)

## Input Checklist

- purchase basis and date
- mortgage balance/rate/payment
- rental income and vacancy assumptions
- taxes, fees, insurance, maintenance reserves
- disposition costs
- marginal tax rate assumptions for capital gains
- alternative investment return assumptions

## Output Contract

1. Executive summary recommendation.
2. Full assumptions and calculations.
3. Scenario table (keep vs sell now vs sell later).
4. Risk analysis and sensitivity notes.
5. Actionable next steps.
