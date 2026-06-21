---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/VISION"
doc_type: "vision"
doc_status: "active"
title: "LifeRepo Vision"
description: "Strategic direction for the public personal operating system framework."
memory_eligible: true
memory_priority: "medium"
doc_tags:
  - "domain:vision"
  - "visibility:public"
  - "type:vision"
---
# LifeRepo Vision

LifeRepo should be a public, reusable framework for AI-assisted life management:
agent specs, workflow contracts, templates, and conventions that keep private
state in a separate repo.

## Product Thesis

AI assistants become more useful when personal context is versioned, scoped by
domain, and separated into public framework, reusable execution skills, and
private state. LifeRepo owns the shareable structure, not the user's sensitive
records.

## Goals

- Keep public specs generic, concise, and reusable.
- Preserve the public/private split through placeholders and pointer config.
- Make each domain understandable through `README.md`, `AGENT-*.md`, and
  `IMPROVEMENTS.md`.
- Keep execution-heavy automation in a skills repo.

## Non-Goals

- Do not store personal journals, health records, financial records, secrets,
  or private company data here.
- Do not hardcode one user's private repo names or paths.
- Do not let public templates drift into private operational truth.
