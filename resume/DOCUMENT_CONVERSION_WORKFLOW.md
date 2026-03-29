# Resume Document Conversion Workflow

Reusable workflow for converting resume source files into text-editable and
submission-ready formats.

## Goal

Maintain an edit-friendly source format while generating consistent PDFs for
applications.

## Supported Approaches

### Fast Manual Path

1. Copy content from source document into markdown/plain text for editing.
2. Apply resume review workflow and revisions.
3. Sync updates back to canonical source format.

### Command-Line Path

Use local conversion/build tooling for repeatable output:

- text extraction for review
- source-to-PDF build for submissions

## Recommended Source-of-Truth Pattern

1. Keep one canonical editable source per variant.
2. Keep generated artifacts separate from source.
3. Version source files in git; treat build artifacts as disposable.

## Quality Checks

- Confirm no missing sections after conversion.
- Verify bullet formatting and character encoding.
- Validate final PDF readability and ATS-safe structure.

## Boundary

- Public workflow spec lives here.
- User-specific files, variants, and compiled outputs live in
  `<private-repo>/Resume/`.
