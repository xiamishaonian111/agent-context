# AGENTS.md

## Overview

This repo stores reusable agent context assets for future projects.

Main artifacts:

- `principles.md`: durable principles for writing agent instruction files.
- `AGENTS.template.md`: default starting template.
- `adaptation-checklist.md`: checklist before committing adapted context files.
- `examples/`: project-type-specific examples.

## Validate

- List files: `rg --files`
- Check unfinished markers: `rg -n "TODO|TBD|待补"`
- Review git status before finishing: `git status --short`

## Working Rules

- Keep root instructions concise and operational.
- Prefer `AGENTS.md` as the canonical cross-tool instruction file.
- Use tool-specific files such as `CLAUDE.md` or `GEMINI.md` only as shims or examples unless there is a reason to duplicate content.
- Do not add generic advice that would apply to every software project.
- Templates must use placeholders only where adaptation is expected.
- Examples must be realistic and copyable after trimming.

## Boundaries

- Always: update `README.md` when adding or removing top-level assets.
- Always: update `adaptation-checklist.md` when principles imply a new pre-commit check.
- Ask first: adding a new tool-specific canonical format.
- Never: include secrets, credentials, private tokens, or personal sensitive data in templates.

## Definition of Done

- New templates are short enough to adapt quickly.
- Every command or path in an example is plausible for that project type.
- The repo remains clean after committing changes.
