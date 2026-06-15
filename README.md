# agent-context

Reusable guidance for creating concise, effective agent context files across projects.

This repo provides:

- `principles.md`: durable principles for writing agent instructions.
- `AGENTS.template.md`: a small default template for new projects.
- `adaptation-checklist.md`: checks to run before committing an agent context file.
- `examples/`: project-type-specific examples to copy and trim.
- `skills/INDEX.md`: manual discovery index and installation protocol for reusable skills.
- `skills/project-agent-context/`: Codex skill source for applying this repo to new projects.
- `skills/write-new-skill/`: Codex meta skill for writing outcome-oriented, interactive skills.

## Source And Influence

This project is inspired by Yage / grapeot's public context-infrastructure work, especially the pattern of keeping root agent instructions concise, routing reusable procedures into skills, and maintaining a manual skill index instead of auto-generating one.

## Recommended Use

1. Start from the closest example in `examples/`.
2. Delete sections that do not apply.
3. Replace every placeholder with real project facts.
4. Keep root instructions concise; move local detail to nested files, docs, or skills.
5. Verify every command and path before committing.

## File Naming

Prefer `AGENTS.md` for cross-tool compatibility. Use a thin shim for tool-specific files when needed, for example:

```markdown
# CLAUDE.md

@AGENTS.md
```
