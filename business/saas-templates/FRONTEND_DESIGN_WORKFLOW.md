---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/business/saas-templates/FRONTEND_DESIGN_WORKFLOW"
doc_type: "guide"
doc_status: "active"
title: "Frontend Design Workflow for SaaS Templates"
description: "Research-backed process for turning visual references into a reusable design language and component system."
memory_eligible: true
memory_priority: "medium"
doc_tags:
  - "domain:business"
  - "domain:frontend-design"
  - "visibility:public"
  - "type:guide"
---
# Frontend Design Workflow for SaaS Templates

## Genesis

Created from user request to improve Mira's visual quality by building the UI
step by step instead of page by page.

## What Most Teams Actually Do

High-performing frontend teams usually do this in order:

1. Define product and conversion intent first (target user, one page goal, one
   primary action).
2. Lock a visual thesis (the intended vibe and level of visual intensity).
3. Create a small design language (tokens and primitives) before building full
   pages.
4. Build pages from reusable sections and components.
5. Continuously validate accessibility and consistency.

This is the design-system model used by teams like GitHub Primer, Atlassian,
Carbon, GOV.UK, and USWDS: foundations -> components -> patterns -> pages.

## Step-by-Step Process (Mira)

### Step 0: Product Brief (30-45 min)

Define:
- ICP and job-to-be-done
- one page goal (for example: "start trial")
- one non-goal (what this page should not try to do)

Output:
- a 5-8 line brief in plain text

### Step 1: Reference Sweep (45-60 min)

Collect 20-30 screenshots:
- 10 landing/marketing references
- 10 app/dashboard references
- 5-10 form and onboarding references

Tag each screenshot:
- `hero`, `pricing`, `social-proof`, `nav`, `table`, `form`, `empty-state`,
  `mobile`

For each screenshot, write:
- what works
- what feels wrong
- one pattern worth borrowing

Output:
- short reference board plus notes

### Step 2: Visual Thesis + Constraints (20-30 min)

Write one sentence:
- "Mira should feel ___, through ___ layout, with ___ interaction energy."

Define anti-goals:
- what to avoid visually (for example: glassmorphism, random gradients,
  over-animated cards)

Output:
- one thesis line + 3-5 anti-goals

### Step 3: Tokens (60-90 min)

Lock first-pass tokens only:
- color: `bg`, `surface`, `text`, `muted`, `accent`, `danger`, `success`
- type: family, scale, line-height, heading/body weights
- spacing scale: 4/8-based or equivalent
- radius scale
- shadow/elevation levels
- container widths and breakpoint behavior

Output:
- token table with names + values + intended usage

### Step 4: Primitives (90-120 min)

Build only these first:
- `Button` (primary, secondary, ghost; hover/focus/disabled/loading)
- `Input` (default/focus/error/disabled; hint + error text)
- `Card` (default/emphasis/interactive)

Output:
- component spec and coded primitives in one place

### Step 5: Page Composition Rules (45-60 min)

Define section responsibilities:
- hero: promise and CTA
- proof: logos, stats, testimonials
- mechanism: how it works in 3 steps
- conversion: pricing/CTA close

Output:
- one wireframe with section goals (not final visuals yet)

### Step 6: Build and Review Loop (daily)

Use a tight loop:
1. Build one section.
2. Take desktop + mobile screenshots.
3. Score against checklist (below).
4. Adjust tokens/components before adding new sections.

## Closed-Loop Frontend Validation

One useful pattern from Anthropic's public Claude Code material is not just
"generate UI faster," but keeping the model inside a render-and-check loop.

The loop is:

1. make the frontend change
2. run the app locally
3. open the page in a browser
4. inspect the rendered result with screenshots
5. zoom into small areas to check labels, spacing, alignment, and fine details
6. inspect browser console output for runtime errors
7. resize to at least desktop and mobile widths
8. test key states, not just the happy path
9. patch the code
10. repeat until the rendered result matches the intended design and behavior

This matters because frontend quality failures are often not code failures.
They show up as:

- spacing that feels slightly off
- copy wrapping badly on smaller screens
- hierarchy collapsing under real content
- hover/focus/error/loading states being inconsistent
- JavaScript errors that only appear in the browser

### What To Validate In The Loop

For each meaningful frontend pass, check:

- visual hierarchy: is the first thing on screen the thing that matters?
- spacing and alignment: are gaps, paddings, and edges consistent?
- typography rhythm: do headings, body text, and labels feel coherent?
- responsive behavior: does the layout still make sense on narrow screens?
- component states: default, hover, focus, disabled, error, loading
- edge cases: long names, empty states, validation errors, unexpected data
- runtime health: no relevant browser console errors

### Minimum Viable Validation Pass

Before calling a section or page "done," capture:

- one desktop screenshot
- one mobile screenshot
- one pass through the primary interaction path
- one deliberate edge-case pass
- one browser-console check

If any of those fail, the section is still in draft, even if the code looks
clean in the editor.

### Practical SaaS Default

For SaaS work, the best default is:

- use code generation to get the first pass quickly
- use screenshot inspection to validate visual fidelity
- use browser interaction to validate actual behavior
- use console inspection to catch hidden breakage
- only then move on to the next section or flow

This is a better operating loop than page-by-page building with delayed review,
because it catches both design drift and state/interaction bugs while the
context is still fresh.

## What You Should Look At in References

When you review and send screenshots, focus on these signals:

- Clarity in first 5 seconds: headline + CTA + visual hierarchy
- Type rhythm: heading scale and paragraph readability
- Spacing discipline: consistent vertical spacing and section padding
- Color restraint: small palette with clear semantic usage
- Component consistency: same button/input/card behavior everywhere
- Proof quality: believable logos/testimonials/metrics placement
- Mobile integrity: hierarchy still works on narrow screens
- Motion restraint: meaningful transitions only

If a design is "pretty but unclear," do not use it as a primary reference.

## Frontend Skills to Build (In Order)

1. Visual hierarchy and layout composition
2. Typography system design
3. Color + contrast decision-making
4. Component state design (default/hover/focus/error/disabled/loading)
5. Responsive behavior and content reflow
6. Accessibility checks (contrast, focus, keyboard, labels)
7. Component documentation discipline (stories/examples)

## Suggested Deliverables for This Week

1. Reference board with annotations (30 screenshots)
2. Mira v0 token table
3. Three polished primitives (`Button`, `Input`, `Card`)
4. One section at production quality (hero or signup block)

## Source Links (Research)

- NN/g, Design Systems 101: https://www.nngroup.com/articles/design-systems-101/
- Figma design systems overview: https://www.figma.com/design-systems/
- Atlassian Design (get started/foundations): https://atlassian.design/get-started/ and https://atlassian.design/foundations/
- GOV.UK Design System styles: https://design-system.service.gov.uk/styles/
- USWDS (components, patterns, tokens): https://designsystem.digital.gov/
- W3C WCAG 2.2 quick reference: https://www.w3.org/WAI/WCAG22/quickref/?versions=2.2
- Storybook (component-driven UI development/docs): https://storybook.js.org/
- Design Tokens Community Group drafts: https://www.designtokens.org/tr/drafts/

## Inspiration Sources (For Screenshot Collection)

- Lapa Ninja (SaaS category): https://www.lapa.ninja/category/saas/
- Land-book (SaaS): https://land-book.com/design/website/saas
- Mobbin (web app inspiration): https://mobbin.com/discover/apps/web
- designsystems.com (open design-system references): https://www.designsystems.com/

## YC Website Stack Snapshot (2026-04-01)

Quick scan for practical stack signal before deciding how to build Mira.

Sample:
- 30 YC company sites from recent batches (`W26` + `S25`, 15 each)
- stack inferred from live HTML/header markers (not self-reported)

Observed distribution:
- Next.js: 14/30 (46.7%)
- Webflow: 5/30 (16.7%)
- Framer: 3/30 (10.0%)
- React SPA (likely Vite): 2/30 (6.7%)
- Static/Other: 4/30 (13.3%)
- WordPress: 1/30 (3.3%)
- Wix: 1/30 (3.3%)

Practical takeaway for Mira:
- Default to a code-first app stack (Next.js-style approach) for product and
  primary marketing surface.
- Use Webflow/Framer/WordPress only when non-dev content velocity is the main
  requirement for a separate content surface.
