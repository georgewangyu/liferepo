---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/docs/AGENT_MIGRATION_MAP"
doc_type: "agent_spec"
doc_status: "active"
title: "Agent Migration Map"
description: "This file maps legacy `<private-repo>` agent docs to canonical public specs in"
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:docs"
  - "visibility:public"
  - "type:agent_spec"
---
# Agent Migration Map

This file maps legacy `<private-repo>` agent docs to canonical public specs in
`liferepo`.

## Core

| Legacy path | Canonical spec |
|---|---|
| `<private-repo>/AGENT.md` | `liferepo/AGENT.md` + `liferepo/docs/ASSISTANT_OPERATING_MANUAL.md` + `liferepo/docs/AGENT_CATALOG_GOVERNANCE.md` |
| `<private-repo>/journal/AGENT-journal.md` | `liferepo/journal/AGENT-journal.md` |
| `<private-repo>/memory/AGENT-memory.md` | `liferepo/memory/AGENT-memory.md` |
| `<private-repo>/deep-exploration/AGENT-deep-exploration.md` | `liferepo/deep-exploration/AGENT-deep-exploration.md` |
| `<private-repo>/Resume/AGENT-resume.md` | `liferepo/resume/AGENT-resume.md` |

## Business / Operations

| Legacy path | Canonical spec |
|---|---|
| `<private-repo>/business/AGENT-business.md` | `liferepo/business/AGENT-business.md` |
| `<private-repo>/data-ownership/AGENT-data-ownership.md` | `liferepo/data-ownership/AGENT-data-ownership.md` |
| `<private-repo>/housing/AGENT-housing.md` | `liferepo/housing/AGENT-housing.md` |
| `<private-repo>/housing/AGENT-real-estate-analysis.md` | `liferepo/housing/AGENT-housing.md` |
| `<private-repo>/housing/**/AGENT-real-estate-analysis.md` | `liferepo/housing/AGENT-housing.md` |
| `<private-repo>/aster-company/expenses/**/AGENT-*.md` | `liferepo/business/AGENT-business.md` |
| `<private-repo>/finance/expenses/**/AGENT-*.md` | `liferepo/business/AGENT-business.md` |

## Knowledge / Principles

| Legacy path | Canonical spec |
|---|---|
| `<private-repo>/knowledge/AGENT-knowledge.md` | `liferepo/knowledge/AGENT-knowledge.md` |
| `<private-repo>/knowledge/**/AGENT-*.md` | `liferepo/knowledge/AGENT-knowledge.md` |
| `<private-repo>/principles/AGENT-principles.md` | `liferepo/principles/AGENT-principles.md` |

## Career / Interviewing

| Legacy path | Canonical spec |
|---|---|
| `<private-repo>/Job-Hunting/AGENT-Job-Hunting.md` | `liferepo/career/AGENT-career.md` |
| `<private-repo>/Georges-Vault/Coding-Interviews/AGENT-coding-interviews.md` | `liferepo/career/AGENT-career.md` |
| `<private-repo>/Georges-Vault/System-Design/AGENT-system-design.md` | `liferepo/career/AGENT-career.md` |
| `<private-repo>/Georges-Vault/Company-Interview-Prep/AGENT-*.md` | `liferepo/career/AGENT-career.md` |

## Writing / Distribution

| Legacy path | Canonical spec |
|---|---|
| `<private-repo>/writing/AGENT-writing.md` | `liferepo/writing/AGENT-writing.md` |
| `<private-repo>/writing/AGENT-writing-long-form-blog.md` | `liferepo/writing/AGENT-writing.md` |
| `<private-repo>/social-media/text/AGENT-social-media-text.md` | `liferepo/social-media/AGENT-social-media.md` |
| `<private-repo>/social-media/video/AGENT-social-media-video.md` | `liferepo/social-media/AGENT-social-media.md` |
| `<private-repo>/social-media/text/platforms/**/AGENT-*.md` | `liferepo/social-media/AGENT-social-media.md` |

## Communications / Tooling

| Legacy path | Canonical spec |
|---|---|
| `<private-repo>/tooling/email/AGENT-email.md` | `liferepo/communications/AGENT-communications.md` |
| `<private-repo>/tooling/email/AGENT-email-writing.md` | `liferepo/communications/AGENT-communications.md` |
| `<private-repo>/tooling/calendar/AGENT-calendar.md` | `liferepo/communications/AGENT-communications.md` |
| `<private-repo>/scripts/memory/AGENT-memory.md` | `liferepo/memory/AGENT-memory.md` |
| `<private-repo>/scripts/pdf-reconstruction/AGENT-pdf-reconstruction.md` | `liferepo/data-ownership/AGENT-data-ownership.md` |

## Personal-Only Legacy Areas

These are private overlays only and should not be copied verbatim to public
specs:

- `<private-repo>/notes-private/**/AGENT-*.md`
- `<private-repo>/personal-health/**/AGENT-*.md`
- `<private-repo>/openclaw/workspace/**/AGENT*.md`
- `<private-repo>/projects/**/AGENT-*.md`
