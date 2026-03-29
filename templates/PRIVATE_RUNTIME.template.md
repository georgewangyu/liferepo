---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/templates/PRIVATE_RUNTIME.template"
doc_type: "templates_doc"
doc_status: "active"
title: "Private Runtime Template"
description: "Use this file for private runtime quirks and local execution overrides that"
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:templates"
  - "visibility:public"
  - "type:templates_doc"
---
# Private Runtime Template

Use this file for private runtime quirks and local execution overrides that
should not live in public reusable docs.

## Purpose

- capture machine/workspace quirks
- capture local git/runtime gotchas
- capture user-specific execution policy deltas

## Runtime Quirks

Document concrete issues and deterministic fixes.

## Local Policy Overrides

Add private-only defaults that should be loaded before domain overlays.

## Maintenance

- keep this file concise and practical
- remove obsolete quirks once no longer relevant
