# Resume Prompt Library

Reusable prompt modules for resume review, tailoring, and rewriting.

## 1) Senior Hiring-Manager Critique

```text
Act as a senior hiring manager for software engineering roles. Critique this
resume for role level alignment, technical depth, ownership signal, and
measurable impact.

Return:
1. Top strengths
2. Top weaknesses
3. Missing evidence for target level
4. Prioritized fixes
```

## 2) Job-Description Fit Analysis

```text
Analyze the candidate's fit for this job description.

Steps:
1. Identify must-have requirements vs nice-to-have.
2. Map explicit matches from resume evidence.
3. List critical gaps.
4. Provide fit score (0-100) with reasoning.
5. Recommend: apply now / upskill first / different role target.
```

## 3) ATS Compatibility Pass

```text
Evaluate this resume for ATS compatibility against this JD.

Check:
- section headings
- keyword coverage and placement
- formatting risks
- contact/info layout

Return concise remediation steps with rewritten snippets.
```

## 4) Summary Rewrite (Senior SWE)

```text
Rewrite this resume summary for a Senior Software Engineer role.

Constraints:
- 2-3 sentences
- include scope, outcomes, and technical depth
- avoid buzzword filler
- keep claims defensible
```

## 5) Senior-Focused Bullet Rewrite

```text
Rewrite these experience bullets to emphasize:
- end-to-end ownership
- architecture and tradeoffs
- cross-team influence
- measurable impact

Keep each bullet concise and specific.
```

## 6) Dynamic Dual-Variant Bullets

```text
For each original bullet, produce:
1) Impact-focused variant (metrics/outcomes)
2) Technical-depth variant (design/performance/constraints)

Then choose the stronger variant for the target role and explain why.
```

## 7) ATS + Interview-Worthy Bullet Pass

```text
Rewrite bullets to be both ATS-friendly and interview-worthy.

Requirements:
- natural keyword integration
- concrete numbers where possible
- strong action verbs
- avoid keyword stuffing
```

## 8) Leadership and Strategy Signal

```text
Identify places where leadership, strategy, and decision quality can be made
more explicit. Rewrite those bullets to show:
- initiative
- cross-functional alignment
- risk/tradeoff handling
- outcome ownership
```

## 9) Gap and Opportunity Finder

```text
Find the highest-impact gaps for this target role:
- missing skills evidence
- weak metric coverage
- unclear scope indicators

For each gap, propose specific rewrite or project evidence.
```

## 10) Final QA Checklist Prompt

```text
Run final QA on this tailored resume:
- role alignment
- consistency
- evidence strength
- readability
- ATS readiness

Return:
1. Pass/fail by category
2. last-mile edits
3. final risk warnings before submission
```
