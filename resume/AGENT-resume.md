# AGENT-resume

## Purpose

Define reusable resume-building behavior for role targeting, JD tailoring, and
quality review.

## Standard Workflow

1. Capture target role context (level, domain, hiring bar).
2. Evaluate baseline resume against target requirements.
3. Identify strength gaps and narrative gaps.
4. Rewrite summary and bullets for impact and clarity.
5. Run ATS and formatting pass.
6. Produce role-specific variant and final QA notes.

## Writing Rules

- Prefer outcome-first bullets with measurable impact.
- Show ownership, technical depth, and scope.
- Use concrete verbs; avoid generic task phrasing.
- Keep claims defensible and evidence-backed.

## Review Lenses

- Hiring-manager lens: signal quality, seniority, leadership evidence.
- Recruiter lens: scan clarity, role fit, keyword alignment.
- ATS lens: formatting compatibility and terminology coverage.

## Standard Prompt Modules

Use these reusable modules when reviewing or rewriting:

1. Senior hiring-manager critique.
2. Job-description fit analysis with explicit gap list.
3. ATS keyword and formatting pass.
4. Bullet rewrite variants:
   - impact-first variant
   - technical-depth variant
5. Final role-targeted synthesis.

Detailed reusable prompts live in `PROMPT_LIBRARY.md`.

## Companion Specs

- `DOCUMENT_CONVERSION_WORKFLOW.md`
- `VARIANT_STRATEGY.md`

## Quality Constraints

- Avoid inflated claims that cannot be defended in interview.
- Keep metrics concrete and attributable.
- Prefer specific ownership language over generic contribution phrasing.

## Output Contract

For each target role, produce:

- revised resume variant
- top strengths and top gaps
- prioritized improvement plan

All user-specific artifacts stay in private storage.

## Repository Boundary

- Public workflow specs: `liferepo/resume/`
- Optional tooling/helpers: `georgeskills`
- Private files and tailored variants: `<private-repo>/Resume/`
