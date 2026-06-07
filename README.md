# skills

Agent skills by [@psisquare](https://github.com/psisquare). Compatible with Claude Code, Cursor, Copilot, and 70+ agents via the [skills CLI](https://skills.sh).

## Install

```bash
npx skills@latest add psisquare/skills
```

The CLI shows a picker — choose which skills and which agents to install to.

## Skills

### pm

Product/PM workflow skills.

#### [visual-brief](skills/pm/visual-brief/SKILL.md)

Turn any implementation concept (PRD, plan, architecture, postmortem) into a **story-scroll HTML one-pager** humans actually understand — hero "aha" moment first, plain-language beats, technical appendix below the fold. Single self-contained `.html` file, zero external deps, opens in any browser.

Core principle: **distillation is the work; HTML is the easy part.** The skill encodes a workflow (audience → aha → mine real data → ≤6 beats → render-verify) plus a library of 11 visual idioms (waterfall bars, contrast cards, timelines, funnels, tabs, screenshot frames…) and the anti-patterns that make dense handoff docs fail.

See it applied to itself: [examples/visual-brief-demo.html](examples/visual-brief-demo.html)


## Layout

```
skills/<bucket>/<name>/SKILL.md   # skill definition + bundled references/ and assets/
examples/                         # sample outputs (not installed)
```

Buckets:

- `pm/` — product/PM workflow skills

Spec: [agentskills.io](https://agentskills.io)
