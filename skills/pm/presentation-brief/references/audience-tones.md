# Audience tone presets

> Pick one preset based on who's in the room. Customize 1–2 rules if the room is non-standard. The presets shape §3 (Tone & voice) of the brief and bleed into §5 slide phrasing.

## Common rules (apply to all presets)

- Concise & professional, **not too formal**. No "we are honored to present", "kindly note", "happy to share", "without further ado".
- Plain declarative sentences. State facts, not feelings about facts.
- No filler slides ("Questions?", "Thank you", "About us" — unless explicitly required).
- Preserve domain terms verbatim. Do not translate operational vocabulary.
- Match output language to room's working language. For bilingual rooms, specify which goes where.

---

## Preset: Exec / Director

**Audience**: C-level, directors, department heads. Mix of business and technical fluency. Decision-making authority.

**Tone rules**:
- Lead with the ask. First slide = what you need from them.
- Frame as **risk + ask**, not narrative or complaint about other teams.
- Every slide supports orientation, decision, discussion, or shared diagram understanding. No exposition.
- Bullets ≤ 3 per slide. Body ≤ 30 words.
- Show one chart per slide. Decision matrices > narrative text.
- Speaker notes ≤ 2 sentences — lean on the speaker, not the slide.

**Example phrasings**:
- ✅ "We need one thing from this hour: name the decision-maker per process box."
- ❌ "Today I want to walk you through some challenges we've been encountering with..."
- ✅ "Design is blocked on undecided business flows."
- ❌ "There appear to be some opportunities for improvement in our flow definitions."

**Visual**: Clean. Lots of whitespace. Dark navy primary + single accent.

---

## Preset: Engineering / Technical

**Audience**: Engineers, tech leads, architects. High technical fluency. Wants depth and rationale.

**Tone rules**:
- Show the system. Diagrams over prose.
- Include the why behind decisions, not just the what. Trade-offs explicit.
- Code blocks, schema fragments, API examples allowed and encouraged.
- Numbers + measurements over adjectives ("p99 latency 340ms" not "slow").
- Speaker notes can be longer (≤ 4 sentences) — technical context warrants it.

**Example phrasings**:
- ✅ "Pool reuses N open DB connections — skip handshake per request, drop p99 by ~120ms."
- ❌ "We added connection pooling to make things faster."
- ✅ "Trade-off: stronger consistency costs 2× write latency."
- ❌ "We chose to prioritize consistency."

**Visual**: Code-friendly. Mermaid / Graphviz diagrams. Mono font for code. Color for state diff (added · removed · unchanged).

---

## Preset: Ops / Cross-functional

**Audience**: Operations leads, PMs, business analysts. Domain-fluent but not necessarily technical. Mixed seniority.

**Tone rules**:
- Process diagrams over architecture diagrams.
- Use the domain vocabulary the audience already uses. Do not invent new terms.
- Show the human in the loop — who does what, when.
- Concrete examples > abstract definitions. Walk through one real case.
- Bilingual is common; specify which language for which element.

**Example phrasings**:
- ✅ "Buyer pays reservation fee → CS confirms in 2hr → booking opens."
- ❌ "Initiate transaction commitment via the reservation workflow."
- ✅ "Show the current hand-off step in the team's own working language, verbatim."
- ❌ Rephrasing an operational term into generic English the team never uses.

**Visual**: Swimlane diagrams. Role-coded colors. Status badges. Annotated screenshots if showing UI.

---

## Preset: External client / Customer-facing

**Audience**: Client, prospect, partner org. Often less domain fluency. Trust + clarity matter.

**Tone rules**:
- Lead with value, not features.
- Avoid internal jargon, codenames, team acronyms.
- Concrete outcomes + numbers. Case studies where possible.
- Slightly warmer than exec tone — but still no "we are honored".
- Branded visual treatment if brand assets exist.

**Example phrasings**:
- ✅ "Cuts your team's reconciliation time from 4 hours to 20 minutes per week."
- ❌ "Implements an automated reconciliation pipeline using our proprietary FlowSync engine."
- ✅ "Live for 6 months at 3 partner sites."
- ❌ "Production-deployed across multiple early-access customers."

**Visual**: Branded palette. Logo on title + close. Customer logos / testimonials if applicable.

---

## Preset: Mixed audience (most common)

**Audience**: Some directors, some ops, some engineering. Range of fluency.

**Tone rules**:
- Default to the least-fluent listener for body text.
- Reserve depth for speaker notes and appendix slides.
- Use a Background slide (Slide 3 pattern) to level-set in 30 seconds.
- Explicit glossary slide if domain terms > 5.

**Example phrasings**:
- ✅ "The platform today: internal ops system covering fragments of the end-to-end journey. The next stage: spec-first, no external vendor."
- ❌ Either jargon-heavy or condescending-explainer.

**Visual**: Exec preset visual + ops preset diagrams.

---

## Preset: Board / Investor

**Audience**: Board members, investors. High financial fluency. Limited time + attention.

**Tone rules**:
- Numbers first. Trend > snapshot.
- Every slide ties to a strategic narrative arc (typically: scoreboard · what's working · what's not · ask).
- No internal codenames without translation.
- Honest about misses. "Missed by X because Y. Fix is Z. New target W by date."
- One ask per deck. State it on Slide 1 and Slide N.

**Example phrasings**:
- ✅ "Revenue +18% QoQ vs +12% target. Driven by pilot conversion at 34%."
- ❌ "We had a strong quarter across multiple dimensions of growth."

**Visual**: Chart-heavy. Consistent metric framing (%, $, vs target). Minimal text.

---

## Language pairings (bilingual rooms)

When the source is bilingual, decide which element gets which language and keep it consistent. A common split:

| Element | Language |
|---|---|
| Slide headlines | The room's broadest-reach language (scannable for everyone) |
| Domain terms | Original language, verbatim (contract names, operational terms) |
| Process box names | Whichever language the room actually uses for them |
| Speaker notes | Presenter's working language (or bilingual if the presenter is) |
| Footer / metadata | The room's broadest-reach language |

If the deck uses a non-Latin script (e.g., Thai, Japanese, Arabic), name script-safe fonts explicitly in §4 (for Thai: Sarabun, IBM Plex Sans Thai, Noto Sans Thai) and verify glyphs do not fall back to a missing-glyph box.
