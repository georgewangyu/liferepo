---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/docs/ASSISTANT_OPERATING_MANUAL"
doc_type: "docs_doc"
doc_status: "active"
title: "Assistant Operating Manual"
description: "This file is the canonical public operating manual migrated from legacy"
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:docs"
  - "visibility:public"
  - "type:docs_doc"
---
# Assistant Operating Manual

This file is the canonical public operating manual migrated from legacy
private `AGENT.md` guidance.

## Standard Development Workflow

### Documentation First

Read the design doc for the service/project in `project/docs/` before starting work. For instance, if working on "notes", read `project/docs/notes.md`.

**CRITICAL**: Always update the appropriate README or design document when changes impact them. This includes:
- The project's own README or design docs
- **The main `liferepo/README.md` MUST be updated if the change affects overall structure, adds/removes directories, or changes repository organization**
- Any cross-referenced documentation
- **If you add, remove, or reorganize directories in the root of `liferepo/`, you MUST update the Structure section in `README.md`** (mandatory, not optional)

### File Structure and Context Loading

**Principle**: Start with the general context, then drill down into project-specific context as needed.

**Workflow:**
1. **Always start with** `@AGENT.md` and `@README.md` (root level) - these provide general rules and repository structure
2. **Whenever you open files in a subdirectory**, immediately check whether that directory (or its nearest parent) has its own `AGENT-*.md` and README. If it does, load them (e.g., `journal/AGENT-journal.md`, `obsidian/Georges-Vault/Coding-Interviews/AGENT-coding-interviews.md`, `social-media/AGENT-social-media.md`) before continuing work.
3. **Then read relevant documentation** within that project directory as needed for the task
4. **Task capture lives in the journal now**: Any request to "add to my TODO list", "update my todos", or similar should update the relevant daily summary instead of a root TODO file.
   - For **today's work**, update `journal/summaries/YYYY/MM/YYYY-MM-DD_Summary.md`.
   - For **tomorrow planning**, write concrete priorities into **tomorrow's** summary file as part of the deep sprint plan.
   - **Time estimates required**: When adding tasks or priorities, include time estimates when helpful (e.g., `(30 min)`, `(2 hours)`, `(15 min)`) so work does not blur into one giant fog bank.
   - **Time estimation strategies**: For detailed strategies on handling time uncertainty (ranges, buffers, time discovery, etc.), see `knowledge/adhd-learnings/pattern-01-strategies-time-estimation.md`. Apply these strategies when tasks have uncertain time requirements.
   - Keep the journal focused on a small set of real priorities, not a giant backlog dump.

**Agent File Naming Convention:**
- **Root level**: `AGENT.md` (always use this name)
- **Subdirectories**: Use descriptive names like `AGENT-{{descriptivename}}.md` (e.g., `AGENT-social-media.md`, `AGENT-journal.md`, `AGENT-coding-interviews.md`)
- This makes it clear which area each agent file covers and helps with file organization

**Examples:**
- Working on daily summaries → Read `journal/AGENT-journal.md` and `journal/DAILY_SUMMARY_WORKFLOW.md`
- Working on coding interviews → Read `obsidian/Georges-Vault/Coding-Interviews/AGENT-coding-interviews.md` and related pattern files
- Working on social media content → Read `social-media/AGENT-social-media.md` and `social-media/README.md`
- Working on a project → Read `projects/repos/[project-name].md` and project-specific docs

**Starting New Projects:**

When creating a new project directory or area in liferepo, always create these three files:

1. **`AGENT-{{descriptivename}}.md`** - Agent instructions specific to this project/area
   - Define rules, workflows, and guidelines for AI assistants working in this area
   - Reference the root `AGENT.md` for general rules
   - AI may need to ask the user questions to understand what should be included

2. **`README.md`** - Project overview and documentation
   - Purpose, structure, usage guidelines
   - How this project integrates with other parts of liferepo
   - AI may need to ask the user questions to understand what should be included

3. **`IMPROVEMENTS.md`** - Backlog of potential enhancements
   - Ideas for improvements, features, or optimizations
   - Can be updated over time as new ideas emerge
   - AI may need to ask the user questions to understand what should be included

**Note**: When creating these files, if unclear about their content, ask the user clarifying questions to ensure the files are useful and aligned with their needs.

**Documentation Genesis Rule**: When creating or updating `README.md` and `IMPROVEMENTS.md` files, include a section (at the top or in a "Genesis" section) that captures:
- The original prompt or user request that inspired the directory/project
- A brief summary of the motivation or problem being solved
- The context or "why" behind the improvements listed

This helps maintain institutional memory and makes it easier to understand the evolution and purpose of each area. Format examples:
- **Genesis**: "Created after realizing daily summary workflow had Apple Notes and commits but was missing calendar context"
- **Inspiration**: "User requested: 'we have my apple notes, we have my commits but we don't have my calendar'"

**Directory Organization Rule**: If a root directory (like `scripts/`, `docs/`, etc.) has more than 10 files, ask the user if they want to organize by function before adding more files. Group related files together (e.g., `scripts/exports/`, `scripts/journal/`, `scripts/automation/`).

**Note**: Do not create additional markdown files unless explicitly instructed. Follow the established structure documented in `README.md`.

### Markdown Frontmatter (Required)

All markdown docs in `liferepo` and the private overlay repo must include YAML
frontmatter at the top of the file.

Minimum required keys:
- `doc_schema`
- `doc_id`
- `doc_type`
- `doc_status`
- `title`
- `description`
- `doc_tags`
- `memory_eligible`
- `memory_priority`

Do not place runtime retrieval stats in headers. Keep dynamic usage metadata
(`access_count`, `last_accessed`, etc.) in the dedicated memory access
index/log.

### Prompt Quality Assessment

When evaluating prompts, use the **Prompt Quality Rubric** to judge whether a prompt is LifeRepo-worthy. **Always assess prompts when:**
- Creating new agents, workflows, or reusable prompts
- The task is longer or more difficult (complex tasks benefit from well-formed prompts)
- The user's request is ambiguous or could be interpreted multiple ways

**Reference**: See `PROMPT_QUALITY_RUBRIC.md` for the complete 5-axis evaluation framework.

**Quick Summary**: A good prompt (score 4–5) should:
1. **Role Anchor**: Explicitly define the evaluator mindset/role
2. **Objective Clarity**: Have clearly defined, testable success criteria
3. **Constraints & Guardrails**: Prevent common failure modes
4. **Input Awareness**: Explicitly reference and constrain to inputs
5. **Output Structure**: Demand structured, predictable output

If a prompt scores below 4, suggest improvements before proceeding. If it scores 4–5, acknowledge it's strong and proceed.

### Context Budgeting

Prefer a token-budget approach over hard file-size percentages.

- Keep always-loaded startup context lean: roughly `1,000-2,500` tokens total
  across bootstrap + core agent docs.
- Keep directory-level agent docs focused: roughly `300-1,000` tokens each.
- Load deeper docs on demand based on task relevance.
- Reserve most context for the task itself (code, diffs, logs, user intent).

If startup docs become bloated or repetitive, propose splitting them into
smaller focused files and moving shared guidance into a canonical source.

### Testing and Building

Always run the appropriate build and test commands before committing your work. Fix all errors and warnings from the changes you've made. The specific commands depend on the project's tech stack:
- For Node.js projects: `npm test` and `npm run build`
- For Python projects: `pytest` and appropriate linting/type checking
- For Rust projects: `cargo build --all` and `cargo test --all`
- For other stacks: use the appropriate build and test commands

### Unit Testing Best Practices

When working on unit tests:
- Write tests that will fail with clear errors (e.g., use `result.unwrap()` or explicit assertions with descriptive messages, instead of `assert!(result.is_ok())`)
- Avoid unit tests that test too much - prefer tests that test small pieces of functionality
- Each test should be focused and clearly named

### Logging Guidelines

Add appropriate log messages where human operators or developers will benefit, but ensure the system isn't overwhelmed with logs:
- Use `info!()` or equivalent for important operational events
- Use `debug!()` or equivalent for detailed debugging information
- Use `warn!()` or `error!()` for warnings and errors
- Consider log levels and ensure production systems aren't flooded with debug logs

### Dependency Management

When adding a new dependency:
- First check if that dependency is already used elsewhere in the monorepo
- If it is shared across multiple projects, consider adding it to a shared workspace configuration (e.g., root `package.json`, `Cargo.toml`, `requirements.txt`, etc.) and reference it from child projects
- Keep dependencies up to date and document why each dependency is needed
- Prefer well-maintained, widely-used dependencies when possible

### Pre-Commit Cleanup

**CRITICAL**: Before committing, always clean up formatting issues:

1. **Remove trailing whitespace** from all modified files:
   ```bash
   git diff --name-only | while read file; do
     if [ -f "$file" ]; then
       sed -i '' 's/[[:space:]]*$//' "$file"
     fi
   done
   ```

2. **Normalize EOF newlines** - Ensure files end with exactly one newline:
   ```bash
   git diff --name-only | while read file; do
     if [ -f "$file" ]; then
       perl -i -pe 'chomp if eof' "$file" && echo >> "$file"
     fi
   done
   ```

3. **Verify cleanup** using `git diff --check` to ensure no trailing whitespace or inconsistent EOF remains

**Why**: Cursor and other editors often add trailing whitespace and inconsistent EOF handling. Cleaning this up before committing prevents unnecessary diff noise and maintains code quality.

### Commit Organization & Separation

**Multi-Commit Strategy**: When you have multiple logically distinct changes, **create separate commits for each logical group**, not one giant commit.

**How to identify logical groups:**
- **By feature/domain**: docs updates, code changes, config changes belong in separate commits
- **By project/subsystem**: changes to `projects/x/` and `projects/y/` should be separate
- **By type of change**: new files/structures, modifications to existing files, deletions
- **By responsibility**: "what belongs together stays together"

**Examples of good separation:**
- ✅ Commit 1: `chore: update agent workspace docs (heartbeat, user, identity, memory)`
- ✅ Commit 2: `docs: add comprehensive architecture & token cost model documentation`
- ✅ Commit 3: `feat: establish per-project folder structure with README/TASKS/LOG templates`
- ✅ Commit 4: `feat: implement heartbeat fanout infrastructure & bookkeeping audit framework`

**Examples of BAD bundling:**
- ❌ `feat: update everything` (vague, mixes unrelated changes)
- ❌ One giant commit with docs + code + config + all projects at once

**Why this matters:**
- Makes history readable and reviewable
- Easier to revert specific changes if needed
- Git bisect/blame/log becomes useful
- CI/CD can test per-commit
- Future developers understand intention

**When in doubt, ask:** "Do these changes serve the same purpose or touch the same area?" If the answer is no, make separate commits.

### Atomic Commits with Explicit Paths

**CRITICAL**: Keep each commit atomic to the current task and always commit
using explicit file paths.

- For tracked files:
  `git commit -m "<type(scope): message>" -- path/to/file1 path/to/file2`
- For new files:
  `git add path/to/file1 path/to/file2 && git commit -m "<type(scope): message>" -- path/to/file1 path/to/file2`
- Do not use global unstaging commands like `git restore --staged :/`
  unless explicitly instructed by the owner.
- Before committing, verify staged intent with:
  `git diff --name-only --cached`

### Git Hooks (Required — Do Not Bypass)

**CRITICAL**: This repo uses `.githooks/` for commit-msg and pre-commit hooks. You MUST follow them. Never bypass hooks (no `--no-verify`, no `-c core.hooksPath=/dev/null`). Commit messages must pass the commit-msg hook validation.

If hooks are not active yet, bootstrap them before committing:

```bash
git config core.hooksPath .githooks
chmod +x .githooks/commit-msg .githooks/pre-commit
```

Verify:

```bash
git config --get core.hooksPath
```

### Commit Messages

Commit your changes in git using a well-formed commit message with the following structure:

1. **Single sentence summary** (first line, ~50-72 characters) - **MUST start with a conventional commit prefix** in format `<type>: <subject>` or `<type>(<scope>): <subject>`. Standard prefixes: `feat:` (new features), `fix:` (bug fixes), `chore:` (maintenance), `docs:` (documentation), `style:` (formatting), `refactor:` (code restructuring), `perf:` (performance), `test:` (tests), `build:` (build system), `ci:` (CI/CD). Example: `feat(interview): add topKFrequent solution using min-heap approach`
2. **What we did** - A few paragraphs explaining the change and implementation approach
   - **Work Type Tracking**: If the work was a "deep sprint", "light work", or other work intensity type, mention this in the "What we did" section (e.g., "This was a deep sprint focused on..."). This helps with daily workflow tracking and understanding work patterns.
3. **Challenges faced** - Document any obstacles, trade-offs, or decisions made during implementation
4. **Acceptance criteria** - What was required for this change to be considered complete
5. **Testing** - How the change was tested
6. **Prompt** - After a single line consisting of `---`, include a **reproducible prompt** that would produce the outputs from this session. This is NOT just the first prompt verbatim — it should:

   - **Summarize the initial prompt**: What work or outcome was requested?
   - **Summarize key conversation context**: Constraints, decisions, or clarifications that shaped the output
   - **Be standalone**: A reader (or AI) could use this prompt alone and get similar results

   The goal: the Prompt section should be a distilled, complete prompt that gets the outputs we got.

   **Examples:**
   - ✅ GOOD: `Prompt: The export script is hanging during incremental exports. Fix it to be fast. Use the existing sync logic but add a timeout; don't change the export format.`
   - ✅ GOOD: `Prompt: Add dark mode to settings. User wants a toggle that persists to localStorage. Match the existing component style (Tailwind, same spacing).`
   - ❌ BAD: `Prompt: fix the script` (too vague; wouldn't reproduce the work)
   - ❌ BAD: `Prompt: nice it works now lets commit and push` (procedural, not a work request)

   When writing the Prompt section: ask "If I gave only this prompt to an AI, would it produce something like what we built?"

Word wrap all paragraphs at 72 columns including the prompt. Make sure there are no empty lines before or after the `---` separator line.

For the author of the commit, use the configured username in git with ` (AI Assistant)` appended and the user email. For example:
```
git commit --author="John Doe (AI Assistant) <john@example.com>"
```

### Git Push Policy

**CRITICAL**: Never push changes to remote repositories unless explicitly instructed by the owner. Only commit changes locally.

**What counts as explicit instruction:**
- Direct commands like "push this", "commit and push", "push to remote"
- Explicit permission: "yes, push it", "go ahead and push", "push now"

**What does NOT count as explicit instruction:**
- Questions like "should X be pushed?", "does X need to be committed and pushed?"
- Implied permission from context
- Assuming push is needed because something was committed

**When in doubt, DO NOT PUSH.** Only commit locally and wait for explicit push instruction.

### Auto-Commit and Review Gates

Use a tiered automation policy: auto-commit is acceptable for low-risk,
reversible work, but review should gate behavior-changing work. Be more
conservative about auto-push than auto-commit.

**Default stance:**
- Auto-commit is acceptable when the main risk is history clutter rather than
  product or workflow damage.
- Review is required when a change could alter user-visible behavior, agent
  behavior, security posture, deployment behavior, or data safety.
- Auto-push remains disallowed unless the owner explicitly instructs it, per
  the push policy above.

**Generally safe to auto-commit:**
- Docs, notes, summaries, and principle updates
- Generated exports and snapshots
- Formatting-only changes
- Test additions that do not change runtime behavior
- Mechanical refactors in non-critical areas when validation passes

**Usually requires review before commit or before push:**
- Product logic changes
- Prompt, agent, or workflow behavior changes
- Auth, billing, permissions, privacy, or deletion flows
- Infra, deployment, migrations, or environment-sensitive config
- Cross-subsystem changes or large diffs
- Any change where the agent has meaningful uncertainty

**Recommended operating model:**
- Auto-commit low-risk work to keep momentum and preserve progress
- Use a branch-first workflow for code changes that may still need inspection
- Require explicit human review before pushing or merging behavior-changing work

**Practical heuristics:**
- Ask: "Would it be fine if this were committed right now with no further
  thought?" If yes, auto-commit is reasonable.
- Ask: "Would it be fine if I woke up and found this already pushed?" If no,
  do not automate the push step.
- If the change alters behavior rather than merely recording or organizing
  information, bias toward review

**LifeRepo-specific default bias:**
- Strong auto-commit bias for `journal/`, `principles/`, summaries, notes,
  README-style docs, and similar low-risk repository-memory files
- More caution for scripts, automations, prompts, agent instructions, and any
  code that changes system behavior

## Common Workflow Shortcuts

When users mention these phrases, automatically load the corresponding workflow file and execute it:

- **Daily Journal/Summary Workflow**:
  - Phrases: "daily workflow", "daily summary", "journal workflow", "start my daily ai workflow", "let's do the daily summary", "run daily summary"
  - Action: Read `journal/DAILY_SUMMARY_WORKFLOW.md` and execute the daily summary workflow for today (or specified date)

- **Other workflows can be added here as needed**

## ALWAYS FOLLOW THESE RULES WHEN YOU WORK IN THIS PROJECT
