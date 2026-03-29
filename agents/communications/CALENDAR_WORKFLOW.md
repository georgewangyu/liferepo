# Calendar Workflow

Reusable workflow for schedule-aware planning support.

## Objective

Use calendar context to improve planning decisions, sequencing, and execution
window selection.

## Input Sources

Typical private inputs:

- daily calendar export
- rolling upcoming window export

Inputs should be read from `<private-repo>` and never committed in raw form.

## Processing Flow

1. Read current day and upcoming commitments.
2. Identify open work windows and fragmentation risks.
3. Map requested tasks to realistic slots.
4. Flag conflicts, overload risk, and dependency mismatches.
5. Return schedule options with tradeoff notes.

## Planning Rules

- Prefer concrete windows over vague "sometime today" guidance.
- Separate hard commitments from flexible tasks.
- Surface buffer recommendations when schedules are tightly packed.
- Feed constraints back into daily summary/planning workflows.

## Output Contract

For each planning request, return:

- recommended execution window(s)
- explicit conflict notes (if any)
- fallback schedule option
