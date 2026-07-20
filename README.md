# skills

Agent skills by [@psisquare](https://github.com/psisquare) — compatible with Claude Code, Cursor, Copilot, and 70+ agents via the [skills CLI](https://skills.sh).

A growing collection of focused, single-purpose skills, grouped into buckets. Each works standalone; some chain into a workflow. Install all of them or cherry-pick from the picker.

## Install

```bash
npx skills@latest add psisquare/skills
```

The CLI shows a picker — choose which skills and which agents to install to.

## Update

```bash
npx skills@latest update -y
```

Pulls the latest version of every installed skill into place — no reinstall, no re-picking.

## Skills

### `pm/` — product-engineering workflow

Take a feature from fuzzy idea to buildable, prioritised, human-readable handoff — without the mid-sprint "wait, what about X?" churn. Three skills chain into one pipeline (a fourth, **presentation-brief**, is standalone):

```
  idea ──▶ grill-pm ──▶ to-tickets ──▶ visual-brief ──▶ build
          (decide)     (slice)        (explain)
```

| Stage | Skill | Turns… | …into |
|---|---|---|---|
| 1 | **grill-pm** | a fuzzy feature idea | a settled functional spec + parked dev questions |
| 2 | **to-tickets** | that spec | a parent overview + prioritised, gated vertical-slice tickets |
| 3 | **visual-brief** | a plan / spec / ticket | a story-scroll HTML page humans actually read |

#### 1. [grill-pm](skills/pm/grill-pm/SKILL.md) — decide *what* to build

Interviews you about a feature's **functional decisions only** (behavior, business rules, edge cases, states, acceptance criteria), one question at a time. Every technical/implementation question is **parked to a Dev Open Questions list**, never resolved here. Reads your codebase (if present) to ground questions in real behavior, and keeps a shared `CONTEXT.md` glossary so later features inherit this one's term precision.

**Core principle:** separate the functional pass from the technical pass. Settle *what* the system does and hand the dev a clean spec plus a bounded list of *how* questions — killing mid-sprint "wait, what about X?" churn. Output: a `<feature>.functional.md` artifact, agnostic about whatever tooling consumes it next.

#### 2. [to-tickets](skills/pm/to-tickets/SKILL.md) — slice it into buildable work

Breaks a plan or functional spec (e.g. from grill-pm) into independently-grabbable **tracer-bullet vertical slices** on your issue tracker, grouped under a **parent overview issue** (the tracker's own Epic / tracking-issue / parent primitive) that holds the summary, scope, spec link, and open-question roll-up — so the whole feature and its breakdown live in one place. Carries any **open technical questions into the tickets** as explicit "discuss with dev" items — gating those slices to HITL and withholding the ready-for-agent label so no one starts them unresolved. Proposes an **MVP slice** for large breakdowns, and lets you **choose granularity** (coarse / standard / fine).

**Core principle:** no decision and no open question leaves the room as prose. Resolved decisions become acceptance criteria; open questions become gated tickets; a big plan becomes MVP-first phasing — buildable *and* shippable in the right order.

#### 3. [visual-brief](skills/pm/visual-brief/SKILL.md) — explain it to humans

Turns any implementation concept (PRD, plan, architecture, postmortem) into a **story-scroll HTML one-pager** — hero "aha" moment first, plain-language beats, technical appendix below the fold. Single self-contained `.html` file, zero external deps, opens in any browser. Embeds **real design screenshots** so devs see the UI they're building toward.

**Core principle:** distillation is the work; HTML is the easy part. A workflow (audience → aha → mine real data → ≤6 beats → render-verify) plus 11 visual idioms (waterfall bars, contrast cards, timelines, funnels, tabs, screenshot frames…) and the anti-patterns that make dense handoff docs fail.

See it applied to itself: [examples/visual-brief-demo.html](examples/visual-brief-demo.html) · screenshot frames + scope beat in action: [examples/visual-brief-screenshots-demo.html](examples/visual-brief-screenshots-demo.html)

#### 4. [presentation-brief](skills/pm/presentation-brief/SKILL.md) — brief a deck for an AI slide-builder

Standalone (not a pipeline stage). Turns chat context, a URL (Confluence / Notion / NotebookLM / Drive), a file, or pasted text into a single structured **markdown brief** that another AI slide-builder (Claude design, Gamma, Beautiful.ai, Slidev…) generates the deck from — project context, time budget, audience-matched tone, visual direction, slide-by-slide structure (headline · body · visual · speaker note), hard constraints, and source material.

**Core principle:** the brief is the artifact, not the slides. Separate *deciding the deck* from *rendering the deck* — settle audience, time budget, tone, and slide structure up front so the downstream tool has no room to invent filler, mistranslate domain terms, or blow the time budget.

## Layout

```
skills/<bucket>/<name>/SKILL.md   # skill definition + bundled references/ and assets/
examples/                         # sample outputs (not installed)
```

Buckets:

- `pm/` — product/PM workflow skills

Spec: [agentskills.io](https://agentskills.io)
