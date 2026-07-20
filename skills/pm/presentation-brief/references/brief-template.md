# Brief template — full structure

> Fill section-by-section. Do not reorder. Do not add new top-level sections.
> `{{double-braces}}` = placeholder for skill to fill.
> `// comment` = guidance, delete from output.

---

```markdown
---
date: {{YYYY-MM-DD of presentation}}
type: deck-brief
audience: {{e.g., company directors, Engineering leads, External client}}
purpose: {{one-line: what the deck enables in the room}}
source: {{URL or path to primary source}}
tool: {{Claude design | Gamma | Beautiful.ai | Slidev | etc.}}
---

# Brief — {{Deck Title}} ({{YYYY-MM-DD}})

Paste this whole brief into {{tool}} as the project prompt.

---

## 1. Project context (paste verbatim into tool)

> {{2–4 sentence framing block}}. State: what the deck is for, who is in the room, what context they do/don't have, what the primary deliverable is. Include any non-obvious constraint (no vendor, no pre-read, bilingual room, decision required, etc). End with "No filler slides."

## 2. Meeting frame

| Field | Value |
|---|---|
| Date | {{day-of-week YYYY-MM-DD, time-of-day}} |
| Duration | **{{N}} minutes total** |
| Pre-read | {{None — deck is sole context source | Yes — link to <source>}} |
| Audience | {{role + count + relevant background}} |
| Format | {{Live walk-through · Async share · Webinar · etc.}} |
| Primary outcome | {{What is true at end that wasn't true at start}} |
| Explicit non-goal | {{What this session does NOT resolve}} |
| Facilitator | {{Name · Role}} |

### Time budget ({{N}} min)

| Block | Slides | Min |
|---|---|---|
| {{Block name}} | {{slide #s}} | {{min}} |
| ... | ... | ... |
| Buffer / slack | — | {{min}} |

// Total of Min column must equal N. Include a buffer of 2–4 min.

## 3. Tone & voice

- {{Tone preset name — e.g., Exec / Engineering / Ops / External}}
- {{3–5 tone rules — declarative, plain, no filler, etc.}}
- Preserved domain terms (do not translate): `{{term1}}`, `{{term2}}`, ...
- Language: {{primary language}}; {{secondary if bilingual + where it appears}}

## 4. Visual direction

- Style: {{e.g., clean exec deck · technical · data-dense · marketing-polished}}
- Palette: {{primary · background · accent · red-reserved-for}}
- Typography: {{sans-serif | serif}}; must render {{scripts/languages}} cleanly.
- Icons: {{icon set + how to use}}
- Diagrams: {{SVG flow · screenshots · charts}}. If a canonical source diagram exists (Miro / Figma / Mermaid), use a simplified abstraction on-slide and link the canonical source in the footer.
- Footer on every content slide: `{{project · session · date · slide N/total}}` (small, muted).

## 5. Deck structure — {{N}} slides ({{duration}})

> Build exactly these slides in this order. Speaker notes ≤ 2 sentences each. {{Audience-specific note — e.g., "Directors come cold — slides 1–6 must establish full context."}}

### Slide 1 — {{Title}}

- **Title**: {{...}}
- **Subtitle**: {{...}}
- **Footer**: {{date · owner · co-owner}}
- **Visual**: {{description}}

### Slide 2 — {{Headline as slide topic}}

- **Headline**: {{1-sentence headline shown on slide}}
- **Body** (bullets, max 3): {{≤30 words total}}
- **Visual**: {{description}}
- **Speaker note**: {{≤2 sentences}}

// ... repeat for every slide
// For "live fill" slides (decision grids, status tables), use a real markdown table
//   with empty cells. Note it explicitly: "Empty cells render as editable on-slide."
// For comparison slides (3 alternatives, 2 options), use a 2-3 column layout
//   with identical structure across columns.

### Slide N — Close

- **Headline**: What happens next
- **Body**: {{3 bullets — concrete next steps with owner}}
- **Footer block**:
  - {{Full-context link if applicable}}
  - {{Canonical diagram source}}
  - **Owner**: {{Name}} · **Co-owner**: {{Name}}

---

## 6. Hard constraints for the design tool

- Do not invent facts, names, dates, or steps beyond what is in this brief.
- Do not translate preserved domain terms (see §3).
- Do not add slides outside the {{N}} listed (no "Questions?" filler, no "Thank you" slide).
- Keep every slide body ≤ 30 words.
- {{Domain-specific constraint — e.g., "Status column in Authority Grid must render as empty editable cells"}}
- {{Source-fidelity constraint — e.g., "Where the source uses a Thai contract name, reproduce it exactly"}}

## 7. Source material ({{source type}} — for tool's context, not given to audience)

Use only as reference. The {{N}}-slide structure above is the canonical brief; the source is provided so the tool can pull exact phrasing where useful. {{Audience}} {{does/does not}} receive this.

**Source URL**: {{full URL}}

```
{{Paste full source text here — verbatim. Preserve domain terms. Section structure of original is OK to flatten.}}
```

## 8. Privacy note

- {{Audience scope — internal only, external client, public, etc.}}
- {{PII handling — what to redact, what to keep}}
- {{Distribution — Confluence-only, no external share, etc.}}

## Sources

- {{Source URL — title}}
- {{Related canonical artifact — e.g., Miro link, Figma file}}
- {{Wikilinks to related notes if vault context applies}}
```

---

## Section-by-section guidance

### §1 — Project context

This block gets pasted verbatim into the tool as the project prompt. Treat it as 1 paragraph the tool reads first.

Must include:
- What deck is for
- Audience + their starting context
- Primary deliverable (what the room produces)
- Any non-obvious constraint that shapes every slide ("no pre-read", "bilingual", "decision required")

Should NOT include:
- Slide structure (that's §5)
- Tone details (that's §3)
- Source content (that's §7)

### §2 — Meeting frame

Time budget table is the load-bearing artifact. It enforces that slide count × time-per-slide = duration. Build this BEFORE drafting slides.

`Primary outcome` and `Explicit non-goal` together prevent scope creep mid-meeting. Always fill both.

### §3 — Tone & voice

Pick an audience preset from `audience-tones.md`. Customize 1-2 rules if the room is non-standard.

Domain terms list = explicit instruction to the tool to NOT translate. List every term that has operational meaning in source language.

### §4 — Visual direction

Specify palette + typography + footer. If audience has a brand, use it. If not, default to: dark navy primary, white background, single accent (orange/amber), red reserved for blockers only.

For decks with Thai/CJK content, name Thai-script-safe fonts explicitly (e.g., Sarabun, IBM Plex Sans Thai, Noto Sans Thai).

### §5 — Deck structure

The biggest section. Each slide gets the same 4 fields: Headline · Body · Visual · Speaker note.

Slide types:
- **Title slide**: hero word + subtitle + date/owner footer
- **Frame slide**: "We need one thing from this hour" — sets the ask
- **Background slide**: 30-second context, used when no pre-read
- **Agenda slide**: numbered table with minutes per block, highlight the primary deliverable row
- **Diagram slide**: simplified abstraction of canonical diagram, link source in footer
- **Conflict / option slide**: 2–3 column comparison with identical structure
- **Live-fill grid slide**: empty markdown table that gets filled in the room
- **Way-of-working slide**: numbered process (cadence, attendees, sign-off, escalation)
- **Timeline slide**: phase boxes, status labels, no dates if dates are TBD
- **Close slide**: 3 next-step bullets + footer with links

### §6 — Hard constraints

This block prevents the tool from producing generic slide-deck filler. Always include the no-invention rule, no-translation rule, and no-extra-slides rule. Add source-specific constraints as needed.

### §7 — Source material

Paste the full source verbatim. This gives the tool the same context the human author had. Mark it as tool-only if audience does not receive it.

### §8 — Privacy note

Optional but recommended for any internal / PII-bearing content. State the distribution boundary explicitly.
