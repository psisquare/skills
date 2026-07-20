---
name: presentation-brief
description: Build a structured brief that another AI slide-builder (Claude design, Gamma, Beautiful.ai, etc.) can use to generate a presentation. Input can be the current chat context, a URL (Confluence, Notion, NotebookLM, Drive), a local file, or pasted text. Output is a single markdown brief with project context, time budget, tone, visual direction, slide-by-slide structure, and source material. Use this skill whenever the user says "build deck brief", "presentation brief for [tool]", "brief for Claude design", "create a brief to make a deck from [source]", or invokes `/deck-brief`. Use it any time the user asks for a "brief", "deck spec", or "presentation spec" intended for a downstream slide-generation tool. Do NOT use this skill to generate slides directly — its output is a brief, not slides.
---

# Presentation Brief Builder

## What this produces

A single markdown file with this exact structure (no extra sections, no missing ones):

1. **Frontmatter** — date, type, audience, purpose, source, tool
2. **§1 Project context** — paste-verbatim block for the slide-builder tool
3. **§2 Meeting frame** — date, duration, pre-read status, audience, format, primary outcome, non-goal, facilitator + **Time budget table**
4. **§3 Tone & voice** — matched to audience
5. **§4 Visual direction** — palette, typography, icons, footer convention
6. **§5 Deck structure — N slides** — each: headline · body · visual · speaker note
7. **§6 Hard constraints** — what the tool must NOT do
8. **§7 Source material** — full text the tool can quote from
9. **§8 Privacy note** — if PII / internal-only
10. **Sources** footer

A worked example of this exact structure exists in `references/example-brief.md`.

## Default voice for the brief itself

- Directive, structural. The brief tells the tool what to do.
- The brief is NOT the same as the deck. Brief tone = instructions. Deck tone = whatever audience needs.
- Concise, no filler. Tables + bullets over paragraphs.

## Workflow

### Step 1 — Gather inputs

Required to proceed:

| Input | Source |
|---|---|
| **Source content** | Current chat context, URL, file path, or pasted text |
| **Audience** | Who is in the room (role, fluency, prior context) |
| **Duration** | Total minutes for the live session |
| **Outcome** | What must be true at end (decision · alignment · inform · brainstorm) |
| **Pre-read status** | Will the audience have read anything before? |
| **Language / tone** | Output language + register match |
| **Save location** | Folder + filename for the brief |

If any required input is **not supplied or inferable**, ask via `AskUserQuestion`. Always ask:

- **Audience** if unspecified (tone/voice/style/language matches audience)
- **Language** if the source is bilingual (e.g., English + a second working language)
- **Save location** if no project convention is visible (see `references/save-conventions.md`)

Group asks into one `AskUserQuestion` call with ≤4 questions. Do not ask one at a time.

### Step 2 — Fetch source

If source is a URL or external system, fetch first:

| Source | Tool |
|---|---|
| Confluence page | Atlassian MCP `getConfluencePage` (markdown format) |
| Notion page | Notion MCP `notion-fetch` |
| NotebookLM source | NotebookLM MCP `source_get_content` |
| Google Drive file | Google Drive MCP `read_file_content` |
| Web URL | `WebFetch` |
| Local file | `Read` |
| Chat context | Already in conversation — extract relevant turns |

Quote source verbatim where it carries domain terms (contract names, codenames, KPI definitions, terms in another language). Do not paraphrase domain vocabulary.

### Step 3 — Plan slide count + time budget

Read `references/slide-time-budget.md` for the time-per-slide-type rules.

Quick defaults (60-min session, exec audience, no pre-read):

- Open + frame: 2 min
- Background / context: 2 min
- Agenda: 1 min
- Why now / scope: 5 min combined
- Core diagram / flow: 6–8 min
- Discussion / decision: 15+ min (the primary deliverable slide)
- Way of working / next steps: 3–5 min
- Close: 2 min
- Buffer: 2–4 min

Build the time-budget table in §2 before drafting slides. Confirm slide count fits duration before writing slide-by-slide.

### Step 4 — Set audience-matched tone

Read `references/audience-tones.md` to pick a tone preset based on audience.

Hard rules regardless of preset:

- Concise & professional, **not too formal**. No "we are honored", "kindly note", "happy to share". Just declarative.
- Match output language to audience working language. For bilingual rooms, specify which goes where: headings in one, domain terms in the other.
- Preserve domain terms verbatim. Never translate operational vocabulary into generic English.

### Step 5 — Draft brief from template

Copy structure from `references/brief-template.md`. Fill section by section. Do not reorder sections. Do not add new top-level sections.

Slide-by-slide rules:

- Each slide: **Headline · Body · Visual · Speaker note** in that order.
- Slide body ≤ 30 words.
- Speaker note ≤ 2 sentences.
- Use real markdown tables for any grid-style slide (e.g., status table, decision matrix) — not bullet imitations.
- If a slide is the "primary deliverable" (live-fill grid, decision capture), mark it explicitly and call it out in §6 constraints.

### Step 6 — Hard constraints (§6 block)

Always include these in the constraints block:

- Do not invent facts, names, dates, or steps beyond what is in the brief.
- Do not translate preserved domain terms.
- Do not add slides outside the listed N (no "Questions?" filler, no "Thank you" slide).
- Keep every slide body under the word cap.
- Any "live fill" slide must render editable empty cells.

Add domain-specific constraints when the source warrants (e.g., "do not invent dates on the timeline slide").

### Step 7 — Save + report

- Save to the path established in Step 1.
- Report file path + one-paragraph summary of what was built.
- Offer 2–3 targeted refinement options (e.g., "tighten Slide X", "add appendix slide", "spin a [language] variant").

## Output location conventions

If the user is working inside a known project, follow that project's convention — check the project's `CLAUDE.md` / `AGENTS.md`, or look for an existing `decks/`, `presentations/`, `briefs/`, or `writing/` folder. Otherwise ask. Read `references/save-conventions.md` for the filename pattern and detection rules.

## What this skill does NOT do

- Generate slides directly. Use Claude design / Gamma / Beautiful.ai / Slidev for that.
- Build decks bypassing the brief step. The brief is the artifact.
- Translate the source. This skill briefs; hand translation to a dedicated writing/translation pass.

## References

- `references/brief-template.md` — full template w/ all 8 sections + placeholders
- `references/audience-tones.md` — tone presets (exec · engineering · ops · external · mixed · board)
- `references/slide-time-budget.md` — slide-type → minutes mapping + slide count formulas
- `references/save-conventions.md` — filename pattern + how to detect a project's save convention
- `references/example-brief.md` — worked example (fictional director kickoff, 60 min, mixed audience)
