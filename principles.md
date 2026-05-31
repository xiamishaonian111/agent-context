# Agent Context Principles

Use these principles when creating `AGENTS.md`, `CLAUDE.md`, `GEMINI.md`, `.github/copilot-instructions.md`, or similar project memory files.

## Core Principles

1. Keep root instructions concise by default.
2. Include only non-obvious, repeatedly needed, project-specific information.
3. Use real commands and real paths only.
4. Prefer executable checks over vague quality advice.
5. Do not duplicate the README; route to docs when needed.
6. Put multi-step procedures into skills or docs, not always-on context.
7. Use nested `AGENTS.md` files for local rules in large repos.
8. Make boundaries explicit with `Always`, `Ask first`, and `Never` rules.
9. Remove stale, redundant, or conflicting rules.
10. Treat agent context as operational memory, not project marketing copy.

## Length Guidance

Root context should usually be short enough to scan quickly. Add detail only when it is:

- repeatedly needed,
- hard to infer from the repo,
- likely to change agent behavior, and
- cheaper to keep in context than to rediscover.

Large projects can use nested context files, docs, and skills instead of one oversized root file.

## Content Guidance

Good content:

- project-specific commands,
- project layout and key entry points,
- validation and test commands,
- source or evidence policy,
- non-obvious conventions,
- safety or deletion boundaries,
- update rules linking related files.

Bad content:

- generic advice any competent agent already knows,
- stale status updates,
- long architecture essays,
- copied README prose,
- secrets or credentials,
- commands that have not been verified.
