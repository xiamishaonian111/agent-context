# AGENTS.md

## Overview

This is a Markdown research and distillation project. The goal is source-auditable synthesis, not executable software.

## Validate

- List files: `rg --files`
- Check unfinished markers: `rg -n "TODO|TBD|待补"`
- Review git status before finishing: `git status --short`
- Verify current facts with primary sources when claims may have changed.

## Project Structure

- `README.md`: human entry point and reading order.
- `00-source-map.md`: source map and evidence notes.
- `v1-*.md`: independent investigation.
- `v2-*.md`: merged synthesis.
- `docs/`: supporting notes or long-form background, if present.

## Working Rules

- Default to Simplified Chinese unless instructed otherwise.
- Separate facts, interpretations, and recommendations.
- Prefer primary sources over secondary summaries.
- Do not present mutable numbers as stable facts.
- Do not preserve unsupported process claims as fact.

## Boundaries

- Always: update the source map when adding important new sources.
- Always: update `README.md` when navigation or reading order changes.
- Ask first: deleting prior agent work or restructuring the project.
- Never: invent citations or claim a source proves more than it does.

## Definition of Done

- Current entry points are linked from `README.md`.
- New sources are listed in `00-source-map.md`.
- No TODO/TBD markers remain in final deliverables.
- Facts, inferences, and recommendations are distinguishable.
