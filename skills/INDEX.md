# Skills Index

This index is the manual discovery surface for reusable skill sources in this
repo. It is maintained by hand; do not auto-generate it unless that becomes a
separate, intentional project decision.

## Current Skills

| Skill | Source | Runtime | Use when |
|---|---|---|---|
| `project-agent-context` | [`project-agent-context/SKILL.md`](project-agent-context/SKILL.md) | `~/.codex/skills/project-agent-context/SKILL.md` | Creating, updating, or reviewing project-level agent context files such as `AGENTS.md`, `CLAUDE.md`, or `.github/copilot-instructions.md`. |
| `write-new-skill` | [`write-new-skill/SKILL.md`](write-new-skill/SKILL.md) | `~/.codex/skills/write-new-skill/SKILL.md` | Creating or rewriting agent skills so they are outcome-oriented, bounded, discoverable, and easy for another agent to apply. |

## Maintenance Rules

- Treat `~/agent-context/skills/<name>/SKILL.md` as the source of truth for
  skills owned by this repo.
- When a source skill should be active locally, sync it to
  `~/.codex/skills/<name>/SKILL.md` and verify the source/runtime diff is empty.
- When adding, renaming, removing, or materially changing a skill in this repo,
  update this index in the same change.
- Prefer updating an existing skill over adding a near-duplicate.
- Keep private aliases, local paths, credentials, endpoint defaults, and
  business context out of public skill sources. Put private configuration in a
  local overlay or `.env` that is not published.

## Public Skill Repo Installation Protocol

When installing an external public skill repo into this workspace:

1. Start from the target workspace's `AGENTS.md` or equivalent agent instruction
   file.
2. Follow any local routing files, especially `WORKSPACE.md` and this
   `skills/INDEX.md`.
3. Clone or vendor the repo under an appropriate project directory instead of
   copying all of its internals into this repo by default.
4. Expose exactly one root/router skill to the global discovery surface. The
   root skill can link to focused files inside the installed repo.
5. Do not globally expose every focused sub-skill from an external repo; that
   makes discovery noisy and weakens the public/private boundary.
6. Keep private aliases, local paths, credentials, endpoint defaults, and
   business context in local overlay files, not in the public repo.
7. Update this index, a relevant runtime registry, or the target workspace's
   agent instructions so future agents can find the installed root skill.

## Deferred Quick Table

Do not add a quick table to this repo's root `AGENTS.md` yet. Add one later only
after real usage shows which skills are frequent enough to deserve always-on
shortcuts. When added, keep it short and treat this index as the source of truth.
