# Sample Resume (LaTeX -> PDF)

This folder contains a public fake resume example that demonstrates the
expected source and build flow.

The sample uses the same visual formatting system as the private canonical
resume template (layout, typography, section styling, spacing, and macros),
with fully generic placeholder content.

## Files

- `Sample_Senior_SWE_Resume.tex` - LaTeX source
- `Sample_Senior_SWE_Resume.pdf` - Built output

## Build (from `liferepo/`)

Preferred command:

```bash
python3 ../georgeskills/skills/utility-ops/scripts/build_resume_pdf.py \
  resume/examples/senior-swe/Sample_Senior_SWE_Resume.tex \
  --project-root .
```

Direct `pdflatex` fallback:

```bash
cd resume/examples/senior-swe
pdflatex -interaction=nonstopmode Sample_Senior_SWE_Resume.tex
```
