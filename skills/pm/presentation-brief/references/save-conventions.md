# Save conventions

> Where to save the brief. Follow the project's own convention if one exists; otherwise ask.

## Filename pattern (universal)

```
YYYY-MM-DD-<topic-slug>-deck-brief.md
```

- `YYYY-MM-DD` = date of the **presentation**, not the date of the brief (use the prep date if the presentation date is TBD).
- `topic-slug` = lowercase, hyphenated, ≤ 40 chars.
- Suffix `-deck-brief.md` distinguishes the brief (the input spec) from the built deck (the deliverable) and from meeting notes.

## Detecting a project's convention

Before asking, look for an established convention:

1. **Project docs** — read `CLAUDE.md` / `AGENTS.md` / `README.md` at the repo root. Many projects state where briefs, decks, or presentations live.
2. **Existing folders** — look for `decks/`, `presentations/`, `briefs/`, `docs/decks/`, or `writing/`. Match where similar artifacts already sit.
3. **Artifact split** — keep the brief (input spec) separate from the built deck (`.pdf` / `.html` output). A common pattern: briefs in one `deck-briefs/` (or `briefs/`) folder routed by artifact type, with built decks filed by audience.

Save the brief where its siblings live, keeping the `-deck-brief.md` suffix + presentation date.

## Unknown project

Ask the user for a save path. Offer 2–3 reasonable defaults based on:

- Where similar artifacts live in the repo (look for `decks/`, `presentations/`, `briefs/`, `writing/`, `docs/`)
- Current working directory + topic
- Whether the project has a docs convention (`CLAUDE.md` / `AGENTS.md` may say)

If nothing reasonable exists, default to `decks/YYYY-MM-DD-<topic>-deck-brief.md` and create the folder.

## Privacy check before save

Before writing the file, scan source content for:

- Names of customers, candidates, employees
- Compensation figures
- Financial projections not yet disclosed
- Vendor / contract terms
- Internal codenames or URLs

If present, add a §8 Privacy note in the brief stating the distribution boundary. Never save a brief with PII to a folder synced to a shared / public location without explicit user confirmation.
