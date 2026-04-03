---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/knowledge/COMPILED_KNOWLEDGE_WORKFLOW"
doc_type: "workflow_spec"
doc_status: "active"
title: "Compiled Knowledge Workflow"
description: "Reusable workflow for maintaining canonical agent-managed synthesis pages between raw sources and compact memory."
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:knowledge"
  - "visibility:public"
  - "type:workflow_spec"
---
# Compiled Knowledge Workflow

## Goal

Define the middle layer between:

- raw/private source artifacts
- chronological logs
- compact structured memory overlays

This layer should contain maintained markdown pages representing the current
best synthesis of recurring topics.

## Why This Layer Exists

Raw sources preserve evidence, but they are usually too noisy to think with.
Compact memory records preserve retrieval, but they are too compressed to hold
full conceptual understanding.

Compiled knowledge pages fill the gap:

- readable by humans
- inspectable by agents
- updateable over time
- linked back to evidence

## Layering Model

Use the following separation:

- raw source layer: exports, notes, transcripts, source docs
- chronological layer: journals, retros, progress logs
- compiled knowledge layer: current-best topic synthesis
- compact memory layer: high-signal durable facts

## When To Update Compiled Knowledge

Update this layer when all of the following are true:

1. The work produced meaningful synthesis, not just a status update.
2. The topic is likely to recur.
3. A future agent would benefit from reading one canonical page first instead
   of reconstructing the topic from scattered files.

Do not update this layer for every conversation milestone.

## Typical Inputs

- daily summaries
- research notes
- deep exploration artifacts
- source documents or exports
- prior compiled pages

## Typical Outputs

Each compiled page should usually include:

- `Summary`
- `Current Understanding`
- `Important Evidence`
- `Open Questions`
- `Related Pages`
- `Source Map`

## Routing Rules

- If the important thing is what happened, update the chronological layer.
- If the important thing is what durable fact should remain retrievable, update
  compact memory.
- If the important thing is the current best explanation of a recurring topic,
  update compiled knowledge.

## Auto-Update Strategy

Prefer a staged approach:

1. Auto-capture milestones into chronological logs.
2. Auto-refresh candidate memory records into a reviewable overlay.
3. Auto-suggest compiled-page updates only when a topic has enough new signal.
4. Prefer targeted page updates over broad whole-repo recompilation.

This keeps the middle layer selective instead of turning into another noisy
archive.
