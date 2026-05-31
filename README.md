# agent-context

Reusable guidance for creating concise, effective agent context files across projects.

This repo provides:

- `principles.md`: durable principles for writing agent instructions.
- `AGENTS.template.md`: a small default template for new projects.
- `adaptation-checklist.md`: checks to run before committing an agent context file.
- `examples/`: project-type-specific examples to copy and trim.

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
