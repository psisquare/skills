# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

Public agent skills repo, installable via `npx skills@latest add psisquare/skills`. Follows the [agentskills.io](https://agentskills.io) spec. There is no build, lint, or test step — skills are plain markdown plus bundled assets.

## Layout

Skills are organized into bucket folders under `skills/`:

- `pm/` — product/PM workflow skills

```
skills/<bucket>/<name>/SKILL.md      # skill definition (frontmatter: name, description)
skills/<bucket>/<name>/references/   # optional deep-dive docs the skill links to
skills/<bucket>/<name>/assets/       # optional templates/files the skill uses
examples/                            # sample outputs, referenced from README — not installed
```

New skill goes into an existing bucket if one fits; otherwise add a new bucket folder and list it both here and in the README's Layout section.

## Invariants

- Every skill under `skills/` must have an entry in the top-level `README.md`: skill name linked to its `SKILL.md`, plus a short description of what it does and its core principle.
- `SKILL.md` frontmatter `name` must match its folder name. The `description` field is what agents use to decide when to trigger the skill — it should state the use cases and trigger phrases, not just summarize the skill.
- Skills must be self-contained: everything they need lives in their folder (`references/`, `assets/`). No links to files elsewhere in the repo.
- If a skill ships an example output, put it in `examples/` and link it from the README entry — `examples/` is showcase only, never installed, and skills must not link to it.

## When adding or changing a skill

Keep `SKILL.md`, its README entry, and any `examples/` artifact in sync — a description change in one place must be reflected in the others.
