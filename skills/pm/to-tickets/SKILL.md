---
name: to-tickets
description: Break a plan, spec, or PRD into independently-grabbable tickets on the project issue tracker using tracer-bullet vertical slices. Carries any open technical questions into the tickets as explicit "discuss with dev" items (and gates those tickets), proposes an MVP slice when the breakdown is large so the PM can prioritise what ships first, and lets the PM choose how coarse or fine the tickets should be. Use when a user wants to convert a plan or a functional spec (e.g. from grill-pm) into implementation tickets.
---

# To Tickets

> Adapted from [`mattpocock/skills` → `to-issues`](https://github.com/mattpocock/skills/blob/main/skills/engineering/to-issues/SKILL.md), MIT © 2026 Matt Pocock. Adds: open-technical-question gating, MVP/phase proposal, and PM-chosen granularity.

Break a plan into independently-grabbable issues using vertical slices (tracer bullets). Built to consume a functional spec (e.g. `<feature>.functional.md` from grill-pm) or any plan/PRD already in context.

The issue tracker and triage label vocabulary should have been provided to you — run `/setup-matt-pocock-skills` if not.

## Process

### 1. Gather context

Work from whatever is already in the conversation context. If the user passes a reference (issue number, URL, or a path like `<feature>.functional.md`) as an argument, fetch/read its full body. If the source is a grill-pm functional spec, read **all four sections** — Resolved Functional Decisions, Out of Scope, Glossary touched, and **Dev Open Questions** (you will need the open questions in step 4).

### 2. Choose granularity (ask the PM first)

Before drafting, ask the PM how coarse or fine they want the tickets — this drives everything below:

- **Coarse** — a few large tickets (≈ epic-sized; one per major capability). Best for early scoping or when one owner takes a big chunk.
- **Standard** (default) — vertical slices, each a thin end-to-end path. Most teams want this.
- **Fine** — many small slices. Best for parallelising across devs or AFK agents.

If the PM doesn't say, default to Standard and tell them you did.

### 3. Explore the codebase (optional)

If a repo is present and you haven't explored it, do so to ground titles/descriptions in real behaviour. Use the project's domain glossary (CONTEXT.md) vocabulary and respect ADRs in the area you're touching. No repo → proceed from the spec; do not block.

### 4. Draft vertical slices

Break the plan into **tracer bullet** issues at the chosen granularity. Each issue is a thin vertical slice cutting through ALL integration layers end-to-end, NOT a horizontal slice of one layer.

Slices are **HITL** or **AFK**. HITL needs human interaction (an architectural decision, a design review, an unresolved question). AFK can be implemented and merged without human interaction. Prefer AFK where possible — **but see the open-questions rule below.**

<vertical-slice-rules>
- Each slice delivers a narrow but COMPLETE path through every layer (schema, API, UI, tests)
- A completed slice is demoable or verifiable on its own
- Prefer many thin slices over few thick ones (unless the PM chose Coarse)
</vertical-slice-rules>

#### Map the open technical questions onto the slices

Every Dev Open Question from the source must end up visible and actionable in the tracker — never silently dropped:

- **Slice-specific question** → list it in that slice's `Open technical questions` section. **Force the slice to HITL** and **withhold the ready-for-agent label** — a slice with an unresolved question is not agent-ready.
- **Cross-cutting question** (not tied to one slice) → collect all such into a single discussion ticket: `[Discuss] Open technical questions — <feature>`. Link every slice it affects as **blocked by** this ticket.

The goal: a dev cannot pick up a slice without first seeing — and discussing — the open questions that bound it.

### 5. Propose an MVP slice when the breakdown is large

If the breakdown is large (rule of thumb: more than ~6 slices, or the PM flags it as big), don't just hand over everything flat. Propose a **phased cut** so the PM can prioritise what ships first:

- **MVP (Phase 1)** — the minimal set of slices that delivers a thin but genuinely shippable product (the smallest end-to-end thing a real user could use).
- **Phase 2+** — everything else, grouped sensibly.

Present the cut and ask the PM to confirm or re-balance it (move slices between phases). Each published issue records its phase in the `Phase` field. This is a prioritisation aid, not a hard gate — the PM owns the call.

### 6. Quiz the user

Present the proposed breakdown as a numbered list. For each slice show:

- **Title** — short descriptive name
- **Phase** — MVP / Phase 2+ (if you proposed a cut in step 5)
- **Type** — HITL / AFK
- **Blocked by** — which slices or discussion tickets must complete first
- **Open questions** — any Dev Open Questions this slice carries
- **User stories covered** — if the source has them

Ask:

- Does the granularity feel right? (too coarse / too fine — re-run step 2 if so)
- Is the MVP cut right? Should anything move phase?
- Are the dependency relationships correct?
- Should any slices be merged or split?
- Are the correct slices marked HITL vs AFK?

Iterate until the user approves.

### 7. Publish the issues to the issue tracker

For each approved slice, publish a new issue using the template below, in dependency order (blockers and the `[Discuss]` ticket first, so you can reference real identifiers). Apply the ready-for-agent triage label **only** to AFK slices with **no** open questions; withhold it from HITL/open-question slices.

<issue-template>
## Parent

A reference to the parent issue/epic (if the source was an existing issue, otherwise omit).

## Phase

MVP / Phase 2+ (omit if no phased cut was made).

## What to build

A concise description of this vertical slice. Describe the end-to-end behaviour, not layer-by-layer implementation.

Avoid specific file paths or code snippets — they go stale fast. Exception: a prototype snippet that encodes a decision more precisely than prose (state machine, reducer, schema, type shape) — inline the decision-rich parts and note it came from a prototype.

## Acceptance criteria

- [ ] Criterion 1
- [ ] Criterion 2

## Open technical questions

Questions to resolve **with dev before building** (omit this section if none). While any remain open, this slice is HITL and not ready-for-agent.

- [ ] Question 1 — and the functional constraint that bounds it
- [ ] Question 2

## Blocked by

- A reference to the blocking ticket or the `[Discuss]` ticket (if any)

Or "None — can start immediately" if no blockers.

</issue-template>

Do NOT close or modify any parent issue.
