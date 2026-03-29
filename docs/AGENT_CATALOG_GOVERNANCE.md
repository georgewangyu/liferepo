---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/docs/AGENT_CATALOG_GOVERNANCE"
doc_type: "agent_spec"
doc_status: "active"
title: "Agent Catalog Governance"
description: "Define governance for the public agent catalog."
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:docs"
  - "visibility:public"
  - "type:agent_spec"
---
# Agent Catalog Governance

## Purpose

Define governance for the public agent catalog.

## Rules

1. Keep these docs public-safe and reusable.
2. Do not include personal identifiers, private paths, or confidential records.
3. Put user-specific behavior in `<private-repo>` overlay docs.
4. Put executable logic in `georgeskills`, not this repository.
5. Keep one canonical home per workflow; avoid copy-paste drift.

## Update Contract

- When migrating agent guidance from private repos, update:
  - `docs/AGENT_MIGRATION_MAP.md`
  - `docs/ASSISTANT_OPERATING_MANUAL.md` (for cross-domain policy)
  - area `README.md`
  - area `AGENT-*.md`
- If a legacy private doc still exists, it must point back to this canonical
  location.
