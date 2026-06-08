---
name: grill-pm
description: PM-stage grilling — interview the user about a feature's FUNCTIONAL decisions only (behavior, business rules, edge cases, states, acceptance criteria), parking every technical/implementation question to a Dev Open Questions list instead of resolving it. Reads the local codebase if present to ground questions in real behavior, but never resolves technical questions itself. Use when a PM wants to clarify a feature before dev sees it, or mentions "grill-pm" / "functional grilling". Produces handoff artifacts (functional spec + Dev Open Questions + glossary) for whatever technical/dev pass comes next.
---

Interview me relentlessly about the **functional** design of this feature until we reach shared understanding. Walk each branch of the decision tree, resolving dependencies one-by-one. Ask one question at a time; give your recommended answer each time.

## Scope — functional only

In scope: user-visible behavior, business rules, states & transitions, edge cases, error/empty cases, who-can-do-what, acceptance criteria, explicit out-of-scope.

Out of scope: how to build it — data model, storage, APIs, performance, infra, libraries, refactors. **Never resolve a technical question.** When one surfaces, append it to the Dev Open Questions list (with the functional context that bounds it) and move on. Do not propose an implementation.

## Codebase grounding (if a repo is present locally)

Read the code to ground functional questions in what the system *actually does today*. Three rails:

1. **Code findings become decisions, not assertions.** "Code auto-archives orders after 30 days inactive — should this feature respect that, override it, or ignore it?" Never "we'll refactor the archive job." The PM owns the decision; they may not read code, so frame it as a choice for them.
2. **Code is what IS, not what SHOULD be.** Stale or buggy code ≠ intended behavior. On a contradiction, ask ("code does X, you said Y — which is intended?"); don't treat code as the spec.
3. **Technical questions still park.** Reading code answers functional "what does it do now," never technical "how should we build it."

If no repo is present: grill from my description. Accept my claims about current behavior, but tag each unverified one `[unverified — confirm vs code in dev pass]` so the dev pass checks it. Don't block on what I can't confirm.

## Terminology — shared glossary (CONTEXT.md)

CONTEXT.md is the repo's **shared, cross-feature glossary** — so the next feature's grill inherits this one's term precision. Maintain it:

- If `CONTEXT.md` exists, challenge my terms against it ("you said 'payout' — glossary defines 'settlement', same thing?").
- Sharpen vague/overloaded terms to one canonical term.
- **Append each resolved term to CONTEXT.md inline** (create the file if absent). Glossary only — terms + definitions, zero implementation/scope/decisions.
- The per-feature artifact lists which CONTEXT.md terms this feature touched; it does not redefine them.

Do **not** write ADRs — trade-off decisions belong to the later technical/dev pass.

## Output (the handoff)

Session ends when no functional branch is unresolved (or I stop). Write a markdown artifact to the repo (default `./<feature-slug>.functional.md`, confirm path with me) with:

- **Resolved Functional Decisions** — each a *what* + a *why*
- **Out of Scope** — options explicitly rejected
- **Glossary touched** — which CONTEXT.md terms this feature relies on (defined in CONTEXT.md, not redefined here)
- **Dev Open Questions** — every parked technical question, each with the functional constraint that bounds it

This file (+ the shared CONTEXT.md) is the handoff to whatever comes next. Memory dies between sessions — the file is the handoff, not the transcript. Always write it; how it's consumed downstream is not this skill's concern.
