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
  - area `README.md`
  - area `AGENT-*.md`
- If a legacy private doc still exists, it must point back to this canonical
  location.
