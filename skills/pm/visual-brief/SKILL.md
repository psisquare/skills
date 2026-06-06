---
name: visual-brief
description: Turn any implementation concept (PRD, plan, architecture, postmortem) into a story-scroll HTML one-pager humans actually understand. Use when user wants to "explain visually", "make a visual brief", "HTML one-pager", "handoff doc", "visualize this PRD/plan/architecture", or when a written ticket needs a human-friendly companion artifact.
---

# visual-brief

Dense reference docs fail at human communication. This skill produces a **story-scroll HTML page**: one visceral hook, ≤6 narrative beats, one idea per section, technical detail pushed below an explicit divider. Output is a single self-contained `.html` file (zero external deps — system font stacks) that opens in any browser.

## Core principle

**Distillation is the work; HTML is the easy part.** The failure mode is a reference card — every fact, equal weight, jargon chips. The fix is ruthless hierarchy: one "aha", few beats, everything else → appendix.

## Workflow

1. **Audience.** Ask if unclear: devs-new-to-domain / mixed dev+stakeholder / non-technical. Sets jargon budget and how much lands in the appendix. Mixed = default: plain story top, dev appendix bottom.

2. **Find the aha.** The single moment that makes a reader *feel* the problem. Best shape: real numbers with a contrast flip (good case → bad case), a before/after, or a "this is what users actually see". Never lead with architecture.

3. **Mine real data.** Pull numbers, names, statuses from the actual source (repo, ticket, spec). Verify arithmetic. **Never invent demo numbers** — fabricated data destroys trust in a handoff artifact.

4. **Pick beats.** ≤6 sections, each = one idea, each mapped to one visual idiom from [references/idioms.md](references/idioms.md):

   | Concept | Idiom |
   |---|---|
   | quantity/money flow | waterfall bars |
   | wrong vs right, before/after | contrast cards |
   | user journey, sequence | numbered timeline |
   | work status | progress bar + slice cards |
   | pipeline, event chain | arrow funnel |
   | system structure | node-arrow diagram |
   | scope, risks | boundary panels |
   | alternatives, variants | tabs |
   | optional detail | toggle/disclosure |

5. **Build.** Start from [assets/skeleton.html](assets/skeleton.html) — locked design system (warm paper, orange accent, serif display + system sans body + mono labels). **Thai-content exception:** system serif has weak Thai glyph coverage cross-platform — for Thai-language briefs, add Google Fonts `IBM Plex Sans Thai` (body) + `Mitr` (display) and point `--sans`/`--display` at them; accept the one external dep. Story sections first, then dark divider ("End of story — technical detail below"), then appendix. Content in English unless user specifies otherwise. Tabs/toggles allowed (vanilla JS in skeleton); page must still read sensibly if JS is stripped.

6. **Verify render.** Screenshot with headless Chrome (or Chromium/Edge — any Chromium binary takes the same flags), eyeball layout, fix overflow/wrap issues:
   ```bash
   # macOS: "/Applications/Google Chrome.app/Contents/MacOS/Google Chrome"
   # Linux: google-chrome / chromium  ·  Windows: chrome.exe
   <chrome-binary> --headless --disable-gpu --screenshot=/tmp/brief.png \
     --window-size=900,4400 --hide-scrollbars "file://$PWD/brief.html"
   ```
   If no Chromium binary available, skip — open the file and ask the user to eyeball instead.

7. **Deliver.** Save to the project's docs folder (e.g. `docs/<topic>/brief.html`), send file + preview PNG to user. Footer must link source-of-truth (ticket, ADR, spec) — the brief is the map, never the territory.

## Anti-patterns (each one observed in a real failed v1)

- **Reference-card density** — every fact at equal weight. Cut or demote to appendix.
- **Leading with architecture** — readers need to feel the problem before seeing boxes and arrows.
- **Jargon chips** — `HITL`, `DEV DONE`, event names in the story half. Plain words top, jargon appendix.
- **Invented numbers** — always mine and verify from source.
- **Mono-font body text** — mono is for labels/code/data only.
- **More than ~6 beats** — past that it's a wiki page, not a brief.

## File map

- [references/idioms.md](references/idioms.md) — copy-paste HTML/CSS for every idiom, with when-to-use notes
- [assets/skeleton.html](assets/skeleton.html) — design tokens, base styles, beat scaffolding, tab/toggle JS
