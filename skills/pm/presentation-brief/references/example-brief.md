# Example brief — Project Atlas Director Kickoff

> Worked example. Fictional company and project — illustrative only.
> Shows all 8 sections + representative slide entries.

This example illustrates:
- Mixed audience (company directors — business + tech)
- 60-min duration, no pre-read assumed
- Bilingual (English headlines + process names in the room's working language)
- Primary deliverable = live-fill grid
- Includes timeline slide with no exact dates (TBD)

---

```markdown
---
date: 2026-05-29
type: deck-brief
audience: Company directors
purpose: Live-walkthrough deck for Project Atlas Director Kickoff
source: https://example.atlassian.net/wiki/spaces/ATLAS/pages/000000/director-kickoff-pre-read
tool: Claude design (slide builder)
---

# Brief — Project Atlas Director Kickoff Deck (2026-05-29)

Paste this whole brief into Claude design as the project prompt.

---

## 1. Project context (paste verbatim into tool)

> Build a slide deck for a **60-minute** live director-level alignment session called
> **Project Atlas — Director Kickoff**. **Directors receive no pre-read — the deck must
> carry full context itself**: what the current ops platform is, what Atlas is, why
> directors are in the room. Atlas = internal codename for the **next-stage rebuild of the
> core operations platform**: spec-first, concrete end-to-end flow, no external vendor
> involved. This project sharpens implementation strategy before build. The deck is both
> orientation and working document — it must drive a live authority-mapping exercise as its
> primary deliverable. Every slide supports orientation, a decision, a discussion, or shared
> diagram understanding. No filler slides.

## 2. Meeting frame

| Field | Value |
|---|---|
| Date | Friday 2026-05-29, afternoon |
| Duration | **60 minutes total** |
| Pre-read | **None** — deck is sole context source |
| Audience | Company directors / department heads (mixed business + tech) |
| Format | Live walk-through (bilingual) |
| Primary outcome | Filled **Authority Grid** — named decision-maker per process box |
| Explicit non-goal | Resolving any flow conflict in the room |
| Facilitator | Platform Lead + PM |

### Time budget (60 min)

| Block | Slides | Min |
|---|---|---|
| Open + frame | 1–2 | 2 |
| Background | 3 | 2 |
| Agenda | 4 | 1 |
| Why now | 5 | 3 |
| Scope | 6 | 2 |
| End-to-end flow | 7 | 8 |
| Conflict overview | 8 | 3 |
| Conflict deep dives (3) | 9–11 | 15 (5 each) |
| **Authority grid — live fill** | 12 | **15** |
| Way of working | 13 | 3 |
| Implementation timeline | 14 | 2 |
| Close | 15 | 2 |
| Buffer | — | 2 |

## 3. Tone & voice

- Exec-grade, decision-driving. Not tutorial.
- Plain declarative sentences. Frame as risk + ask.
- Preserve domain terms verbatim in the room's working language — do not translate operational
  vocabulary into generic English.
- Bilingual expected. Headings in the broadest-reach language; process names in the working language.

## 4. Visual direction

- Clean exec deck. Lots of whitespace. ≤ 30 words per slide body.
- Palette: dark navy primary, white background, orange/amber accent, red reserved for blockers.
- Typography: script-safe for the working language (name explicit fonts if non-Latin script).
- Icons: 🏢 Org · 📦 Asset · 👤 Customer · 🔀 Convergence · ⚠️ Conflict · ✅ Done · 🔒 Blocked
- Footer: `Atlas · Director Kickoff · 2026-05-29 · slide N/total`

## 5. Deck structure — 15 slides (60 min)

> Directors come cold — slides 1–6 must establish full context before any conflict drill-down.

### Slide 1 — Title

- **Title**: Project Atlas — Director Kickoff
- **Subtitle**: Rebuilding the ops platform · End-to-end · Happy path
- **Footer**: 2026-05-29 · Owner: Platform Lead · PM
- **Visual**: Hero — single bold word "Atlas" with horizon-line graphic.

### Slide 2 — Why we're here (90s)

- **Headline**: We need one thing from this hour
- **Body** (3 bullets):
  - Atlas = codename for next-stage platform strategy: spec-first, no external vendor.
  - This project = **sharpen implementation strategy** so build can start with confidence.
    Design currently **blocked** on undecided business flows.
  - **Today's ask**: name the decision-maker per process box. That's it.
- **Visual**: 3-icon row — 🗺️ Strategy · 🔒 Blocked · 🗝️ Authority
- **Speaker note**: Reinforce: we will not resolve flow conflicts today. We name owners
  so workshops can.

// ... Slides 3-11 follow the same pattern: Headline · Body · Visual · Speaker note ...

### Slide 12 — Authority Grid (live fill) — **primary deliverable**

- **Headline**: For each process box, name the decision-maker
- **Body**: Editable table — 4 columns × 6 rows. Show empty fields prominently.

| Process box | Director / sponsor | Decision-maker | Workshop date |
|---|---|---|---|
| Lead → booking (steps 2–3) |   |   |   |
| Verification + contract sequence (steps 4–6) |   |   |   |
| Customer audit position (step 6) |   |   |   |
| Partner match + agreement (step 7) |   |   |   |
| External submission (step 9) |   |   |   |
| Contract issue → handover (steps 12–17) |   |   |   |

- **Footer note**: Empty rows after session = explicit follow-up owners for the lead to chase.
- **Visual treatment**: Real grid (not bullets). Highlight current row during live fill —
  design so presenter can plausibly fill it on-screen.

### Slide 14 — Implementation timeline (high-level)

- **Headline**: Major activities before MVP launch
- **Body**: Horizontal phase timeline — show order + status, **no exact dates**.

  | Phase | What happens | Status |
  |---|---|---|
  | 1. Strategy sharpening | Authority mapping + flow confirmation | **In progress** |
  | 2. Spec finalize | Per-flow workshops → signed decision records | Next |
  | 3. Build | Internal dev cycle on the Atlas stack | Upcoming |
  | 4. UAT | Ops teams validate against real cases | Upcoming |
  | 5. Pilot | Limited pilot flow end-to-end | Upcoming |
  | 6. **MVP launch** | Full pre-handover ops live on Atlas | Upcoming |
  | 7. Post-MVP | After-handover ops (separate scope) | After MVP |

- **Caveat box** (prominent, accent color):
  > **Exact dates not yet determined.** Timeline depends on speed of confirmation cycles
  > with operation teams. Schedule updates as each phase locks.
- **Speaker note**: Do not commit to dates in the room.

### Slide 15 — Close

- **Headline**: What happens next
- **Body** (3 bullets):
  - Authority grid → workshop calendar within 48h.
  - Each workshop → signed flow decision record.
  - Atlas design unblocks one flow at a time.
- **Footer block**:
  - **Full context**: Confluence — Atlas Director Kickoff page
  - **Flow source**: Miro board (link in footer)
  - **Owner**: Platform Lead · **PM**

---

## 6. Hard constraints for the design tool

- Do not invent process steps, dates, decision-makers, or names beyond what is in this brief.
- Do not translate preserved domain terms.
- Do not add slides outside the 15 listed (no "Questions?" filler, no "Thank you" slide).
- Keep every slide body ≤ 30 words. Lean on the speaker.
- Status column in Authority Grid (slide 12) must render as empty editable cells.
- Do not invent dates on the timeline slide (Slide 14). Phases only.
- All diagram references stay as link text in footer; no screenshots requiring zoom.

## 7. Source material (Confluence page — for tool's context, not given to directors)

Use only as reference. The 15-slide structure above is canonical; the source is provided
so the tool can pull exact phrasing where useful. Directors do not receive this — the deck
must self-contain.

**Source URL**: https://example.atlassian.net/wiki/spaces/ATLAS/pages/000000/director-kickoff-pre-read

\```
[Full source page text pasted here verbatim — TL;DR, tracks, conflicts, asks]
\```

## 8. Privacy note

- Director audience is internal company leadership.
- Do not include named individuals until the grid is filled live.
- Deck output not for external share — internal only.

## Sources

- Confluence — Director Kickoff Pre-read 2026-05-29
- Miro — Atlas flow diagram (internal board)
- Related meeting note — kickoff agenda + conflict raw source
- Related project charter
```

---

## What this example demonstrates

| Pattern | Where to see it |
|---|---|
| Cold-audience handling (no pre-read) | Background slide + frame slide; time budget includes 4 min for orientation |
| Bilingual room | §3 working-language rule + §4 script-safe font requirement + slide phrasing rule |
| Primary deliverable slide | Slide 12 — live-fill grid w/ empty cells, 15 min allocation |
| Timeline with TBD dates | Slide 14 — phase boxes + status labels, no dates, caveat callout |
| Domain-specific constraint | §6 "Do not invent dates on the timeline slide" |
| Source-fidelity preservation | §3 no-translation rule + §6 reproduce-terms rule |
| Internal-only distribution | §8 privacy note specifying internal-only |

Use this as a structural reference, not a copy target. The actual brief content varies per source.
