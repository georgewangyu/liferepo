# Resume Spec

Public specification layer for resume workflows and resume agents.

## Contains

- resume review workflow (hiring-manager lens)
- ATS optimization rules
- JD-tailoring decision process
- bullet/summary rewrite prompt patterns
- reusable prompt library: `PROMPT_LIBRARY.md`
- conversion pipeline guidance: `DOCUMENT_CONVERSION_WORKFLOW.md`
- role-family strategy: `VARIANT_STRATEGY.md`

## Suggested Workflow

1. Define target role and level.
2. Compare current resume against target JD.
3. Rewrite summary and bullets for measurable impact.
4. Run ATS compatibility pass.
5. Produce role-specific variant and final QA pass.

## Deliverables Per Role Target

- revised resume variant
- strengths/gaps assessment
- prioritized improvement actions

## Tooling Hooks

- Private-wrapper entrypoint: `<private-repo>/scripts/utils/build_resume_pdf.py`
- Canonical implementation: `georgeskills/skills/utility-ops/scripts/build_resume_pdf.py`

## Boundary

- Public specs here
- Private resume files and variants in `<private-repo>/Resume`
