# skills

Agent skills by [@psisquare](https://github.com/psisquare). Compatible with Claude Code, Cursor, Copilot, and 70+ agents via the [skills CLI](https://skills.sh).

## Install

```bash
npx skills@latest add psisquare/skills
```

The CLI shows a picker — choose which skills and which agents to install to.

## Update

```bash
npx skills@latest update -y
```

Pulls the latest version of every installed skill — no reinstall needed.

## Skills

### pm

Product/PM workflow skills.

#### [visual-brief](skills/pm/visual-brief/SKILL.md)

Turn any implementation concept (PRD, plan, architecture, postmortem) into a **story-scroll HTML one-pager** humans actually understand — hero "aha" moment first, plain-language beats, technical appendix below the fold. Single self-contained `.html` file, zero external deps, opens in any browser.

Core principle: **distillation is the work; HTML is the easy part.** The skill encodes a workflow (audience → aha → mine real data → ≤6 beats → render-verify) plus a library of 11 visual idioms (waterfall bars, contrast cards, timelines, funnels, tabs, screenshot frames…) and the anti-patterns that make dense handoff docs fail.

See it applied to itself: [examples/visual-brief-demo.html](examples/visual-brief-demo.html) · screenshot frames + scope beat in action: [examples/visual-brief-screenshots-demo.html](examples/visual-brief-screenshots-demo.html)

#### [grill-pm](skills/pm/grill-pm/SKILL.md)

PM-stage grilling — interview the user about a feature's **functional decisions only** (behavior, business rules, edge cases, states, acceptance criteria), one question at a time. Every technical/implementation question is **parked to a Dev Open Questions list**, never resolved. Reads the local codebase (if present) to ground questions in real behavior, and maintains a shared `CONTEXT.md` glossary so later features inherit this one's term precision.

Core principle: **separate the functional pass from the technical pass.** The PM settles *what* the system should do and hands the dev a clean spec plus a bounded list of *how* questions to resolve — killing mid-sprint "wait, what about X?" churn. Output is a `<feature>.functional.md` artifact, deliberately agnostic about whatever PRD/issue tooling consumes it next.


## Layout

```
skills/<bucket>/<name>/SKILL.md   # skill definition + bundled references/ and assets/
examples/                         # sample outputs (not installed)
```

Buckets:

- `pm/` — product/PM workflow skills

Spec: [agentskills.io](https://agentskills.io)
