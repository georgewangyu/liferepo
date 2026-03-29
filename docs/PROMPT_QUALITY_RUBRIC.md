# Prompt Quality Rubric

Use this rubric to evaluate whether a prompt is reusable and operationally
reliable.

## Core Principle

Good prompts encode judgment. Weak prompts outsource judgment.

## Five Axes

Score each axis `0` or `1`.
Total score `4-5` is reusable; `<4` should be revised.

1. Role anchoring: Is the evaluator role explicit and appropriate?
2. Objective clarity: Is success concrete and testable?
3. Constraints: Are common failure modes blocked?
4. Input awareness: Is reasoning constrained to provided inputs?
5. Output structure: Is output schema explicit and predictable?

## Operating Rule

- If score `<4`, improve the prompt before execution.
- If score `>=4`, proceed and keep the prompt for reuse.
