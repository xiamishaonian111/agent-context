# Adaptation Checklist

Before committing a new project agent context file:

- Delete sections that do not apply.
- Replace every placeholder with real project facts.
- Verify every command exists and works, or mark it as intentionally unavailable.
- Verify every path exists.
- Keep the root file concise unless there is a strong reason not to.
- Move long procedures to `skills/`, `docs/`, or a nested `AGENTS.md`.
- Use nested `AGENTS.md` for subprojects with different commands or rules.
- Do not include secrets, credentials, tokens, private keys, or sensitive personal data.
- Prefer primary sources and source links for research projects.
- Add a tool-specific shim only when needed, for example `CLAUDE.md` importing `AGENTS.md`.
- Review for stale, redundant, or conflicting instructions.
