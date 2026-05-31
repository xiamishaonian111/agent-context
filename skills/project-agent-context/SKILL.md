---
name: project-agent-context
description: Create, update, or review project-level agent context files such as AGENTS.md, CLAUDE.md, GEMINI.md, .github/copilot-instructions.md, or PROJECT_CONTEXT.md. Use when the user asks to add project instructions, write a project context file, generate repo instructions for agents, adapt the reusable agent-context templates, or decide what agent instruction file a project should have.
---

# Project Agent Context

Create concise, reusable project-level instructions for coding and research agents by applying the user's template assets in `~/agent-context`.

## Goal

Produce or improve a project context file that tells agents how to work in the target repo: what the project is, how to validate work, what conventions matter, and what boundaries must be respected.

## Required Resources

Read these files from `~/agent-context` as needed:

- `principles.md` for quality principles.
- `AGENTS.template.md` for the default shape.
- `adaptation-checklist.md` before finalizing.
- `examples/*.AGENTS.md` when one matches the target project type.

If `~/agent-context` is missing, tell the user and fall back to a minimal `AGENTS.md` based on local repo inspection.

## Canonical File Policy

- Prefer `AGENTS.md` as the canonical cross-tool instruction file.
- Use `CLAUDE.md`, `GEMINI.md`, `.github/copilot-instructions.md`, or `.cursor/rules/*` only when the user asks or the repo already uses that harness.
- If adding tool-specific files, prefer thin shims that point to `AGENTS.md` instead of duplicating full content.
- Do not create `PROJECT_CONTEXT.md` unless the user explicitly asks for that filename or the repo already uses it.

## Workflow

1. Identify the target project directory from the user's request or current working directory.
2. Inspect the repo before writing: use `rg --files`, read `README.md` if present, and check for existing agent instruction files.
3. Classify the project type, such as Markdown research, software app/library, monorepo, or unknown.
4. Select the closest asset from `~/agent-context`: a matching example first, otherwise `AGENTS.template.md`.
5. Draft a concise root `AGENTS.md` using only real project facts, real paths, and verified commands.
6. Keep root context operational: overview, commands/checks, structure, working rules, boundaries, update rules.
7. Move long procedures, detailed architecture, and local rules out of the root file into docs, skills, or nested `AGENTS.md` when appropriate.
8. Apply `adaptation-checklist.md` before finishing.

## Boundaries

- Do not invent build, test, lint, release, or validation commands.
- Do not include secrets, credentials, tokens, private keys, or sensitive personal data.
- Do not copy generic engineering advice that does not change behavior in this repo.
- Do not overwrite an existing instruction file without reading it first and preserving useful project-specific rules.
- Ask before deleting prior agent work, changing canonical filename strategy, or restructuring multiple instruction files.

## Acceptance Criteria

The work is complete when:

- The selected instruction file exists in the target repo.
- It is concise enough to scan quickly and contains no unfilled placeholders.
- Every referenced path exists or is clearly marked as intentionally absent.
- Every command is verified, or the file says the command is unavailable/unverified.
- It distinguishes always-on project rules from optional long-form docs or skills.
- Existing repo-specific instructions are preserved or deliberately superseded with a clear reason.

## Output

When reporting back, include:

- The file created or updated.
- Which `~/agent-context` asset was used as the base.
- Any commands or paths that could not be verified.
- Whether tool-specific shim files were added or intentionally skipped.
