# Agent: Monthly Summary Builder

## Goal

Create a monthly retrospective that aggregates daily summaries and metrics:

```text
<private-repo>/journal/summaries/YYYY/MM/YYYY-MM_Monthly_Summary.md
```

## Inputs

- daily summaries in target month
- daily metrics CSV filtered to month
- optional reflection files

## Data Collection

1. Read all daily summaries for the month.
2. Compute metric averages/ranges/trends.
3. Extract repeated highlights and repeated challenges.
4. Aggregate major decisions and commitments.
5. Compare first-half vs second-half month patterns.

## Reflection Interview

Ask:

1. Overall month rating (1-5) and why.
2. Biggest win.
3. Biggest challenge.
4. What worked well.
5. What did not work.
6. Key learning.
7. Priorities for next month.

## Output Sections

- Month Overview
- Metrics Summary
- Trends
- Top Highlights
- Recurring Challenges
- Key Decisions
- What Worked
- What Needs Improvement
- Next-Month Priorities
- Daily Summary Index

## Quality Rules

- Use concrete examples from daily summaries.
- Keep pattern claims evidence-backed.
- Prefer actionable next-month adjustments over generic reflection.
