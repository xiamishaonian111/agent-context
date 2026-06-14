---
name: write-new-skill
description: >
  Write or rewrite agent skill files so they are outcome-oriented, bounded,
  interactive when key details are uncertain, and easy for another agent to
  apply. Use when creating a new skill, translating a skill, or tightening an
  existing skill's acceptance criteria, boundaries, output contract, or
  human-in-the-loop elicitation behavior.
user-invocable: true
argument-hint: '[skill-path-or-dir]'
disable-model-invocation: false
allowed-tools: Read, Write, Edit, Glob
---

# Write New Skill

Create or rewrite a skill so another agent can use it reliably without hidden
context. Optimize for result certainty and enabling guidance, not rigid step
scripting.

This skill is the default meta-skill for authoring skills. Treat Yage's
`context-infrastructure/rules/skills/bestpractice_skill_writing.md` as the
primary guide for skill quality. The local references `reference.en.md` and
`reference.md` preserve that guidance for offline use.

## Input

`$ARGUMENTS` - Optional target skill file or directory. If omitted, infer the
target from the user's request and the current workspace context.

## Success Contract

Every skill should make these four items explicit:

- **Goal** - What the skill accomplishes, in one sentence.
- **Acceptance criteria** - Concrete conditions an unfamiliar agent can use to
  decide whether the task is done.
- **Resources and boundaries** - Which tools, files, dependencies, and
  non-negotiable limits apply.
- **Output specification** - What is produced, where it lives, and what format
  or schema it must follow.

If any of these four are missing, the skill is underspecified.

## Interactive Elicitation Contract

Infer reasonable defaults first, then ask the user before finalizing whenever an
uncertainty could materially change the skill's scope, safety, usability, or
output. Ask even if you have a plausible answer.

High-impact uncertainties include:

- The skill's goal, trigger conditions, target user, or target agent.
- The success criteria or verification gates.
- The target runtime, source tree, package, install path, or discovery index.
- Allowed tools, private data boundaries, credentials, external services, or
  publishability.
- Output format, schema, destination path, naming convention, or retention
  policy.
- Whether to update an existing skill or create a new one.
- Claimed known pitfalls, especially if they are not grounded in observed
  failures or user-provided history.

Do not interrupt for low-impact details that can be safely represented as a
clearly labeled assumption or placeholder. When the user is unavailable and the
change is reversible, draft the skill with an explicit `Assumptions` or
`Open Questions` section instead of fabricating facts.

## Question Format

When asking the user, keep the interaction short and decision-oriented:

- Ask one to three questions at a time.
- Give a recommended default first when one is defensible.
- Provide two or three common options.
- Preserve a final free-form option such as `Other / I will describe it` so the
  user can correct the framing rather than choosing from your options.
- Explain the tradeoff in one sentence per option when useful.

If the UI tool automatically adds a free-form `Other` option, still phrase the
question so the user knows custom feedback is welcome.

Example question:

```text
Where should this skill live?

1. Public source repo `agent-context/skills/<name>/` (Recommended): reusable, publishable, and reviewable.
2. Codex runtime `~/.codex/skills/<name>/`: immediately active on this machine, but easy to drift from source.
3. Project-local `skills/<name>/`: scoped to one repo and not global by default.
4. Other / I will describe it.
```

## Authoring Guidance

- Optimize for result certainty, not process certainty.
- Prefer constraints, heuristics, and verification rules over "step 1 / step 2"
  scripts.
- Only make order mandatory when later work truly depends on earlier output.
- Write enabling guidance: every paragraph should increase the probability that
  a reasoning agent succeeds.
- Keep `SKILL.md` lean; move detailed discussion to a sibling reference file
  when needed.
- Include real failure modes and repo-specific pitfalls when they are known.
- Do not invent speculative pitfalls just to fill a section.
- Preserve raw error details in troubleshooting guidance.
- Prefer updating an existing skill over creating a near-duplicate.

## Suggested Structure

Use the lightest structure that still makes the skill executable:

- Frontmatter with an accurate `name` and discovery-friendly `description`.
- A short overview of what the skill does and when to use it.
- Inputs or arguments, if any.
- Core instructions, constraints, and human-in-the-loop checkpoints.
- Acceptance criteria and output expectations.
- Links to deeper references or examples when they materially improve execution.

Exact headings can vary. The contract matters more than the section order.

## Placement And Discovery

Before writing, inspect the current workspace for the active skill source or
runtime location. Use the project's established pattern over a generic path.

Common placements:

- A repo-local `skills/<name>/SKILL.md` when the project owns its skill source.
- `~/agent-context/skills/<name>/SKILL.md` for this workspace's project-agent
  context toolkit.
- `~/.codex/skills/<name>/SKILL.md` only when the Codex runtime skill directory
  is the only available active registry.
- `~/App/agent-skills/<package>/<name>/SKILL.md` only when that source tree
  exists in the current environment.

## Source Of Truth And Sync

When both a versioned source tree and a runtime skill directory exist, treat the
versioned source tree as the source of truth. Edit source first, then sync the
runtime copy, then verify the two files match before claiming the skill is
installed or updated.

For this workspace, the normal flow is:

```text
1. Edit `~/agent-context/skills/<name>/SKILL.md`.
2. Copy it to `~/.codex/skills/<name>/SKILL.md` when the skill should be active locally.
3. Run `diff -u ~/agent-context/skills/<name>/SKILL.md ~/.codex/skills/<name>/SKILL.md`.
4. Commit and push the source repo after verification.
```

If the source tree and runtime copy disagree, do not silently pick one. Inspect
the diff and preserve whichever side contains the intentional latest change.

Update the relevant discovery surface when one exists, such as `README.md`, a
skills index, marketplace manifest, or runtime skill list. Do not claim the
skill is installed until the active registry or installer has been verified.

## Acceptance Criteria

Before finishing, confirm that:

- A new agent can tell what success looks like from the skill alone.
- The skill makes goal, acceptance criteria, resources/boundaries, and output
  specification explicit.
- High-impact uncertainty has either been resolved with the user or recorded as
  an explicit assumption/open question.
- Any user-facing clarification offered options plus a free-form feedback path.
- The main file is concise and information-dense.
- Any rigid sequencing that remains is genuinely required.
- Every referenced file or path exists.
- Terminology is consistent throughout.
- Supporting docs are linked only when they materially improve execution.
- The skill is discoverable from the active source tree or runtime registry.
- If both source and runtime copies exist, they have been synced or the
  intentional difference is explicitly documented.

## Additional Resources

- For the fuller English guide based on Yage's best practice, see
  [reference.en.md](reference.en.md).
- For the original Chinese draft, see [reference.md](reference.md).
