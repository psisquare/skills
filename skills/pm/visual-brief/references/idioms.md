# Visual idiom library

Copy-paste blocks for `skeleton.html`. All use the design tokens defined there (`--accent`, `--line`, `--card`, etc.). Each idiom: when to use, then markup. Widths in bars are data-proportional — compute them from real numbers.

---

## 1. Waterfall bars — quantity/money flow

**Use for:** anything that starts as one amount and gets eaten by deductions (revenue → fees → profit; budget → costs; latency budget; token budget). Strongest hook when paired twice: good case in light card, bad case in dark `.flip` card right below — the contrast IS the story.

```html
<div class="wf">
  <div class="wf-title">Real case · item sold at $390 · cost $215</div>
  <div class="wf-row"><span class="lbl">Sale price</span><div class="bar full" style="width:100%"></div><span class="amt">$390</span></div>
  <div class="wf-row"><span class="lbl">Platform fees</span><div class="bar fee" style="width:17.4%"></div><span class="amt neg">−$68</span></div>
  <div class="wf-row"><span class="lbl">Item cost</span><div class="bar cost" style="width:55.1%"></div><span class="amt neg">−$215</span></div>
  <div class="wf-row wf-sum"><span class="lbl">True profit</span><div class="bar win" style="width:27.4%"></div><span class="amt pos">+$107</span></div>
  <div class="wf-note">Looks fine? Wait —</div>
</div>

<div class="flip"><!-- same rows, dark card; use .bar.lose + .punch line for the gut punch -->
  <div class="wf-title">Same item · all surcharges + 30% flash sale</div>
  <!-- rows... -->
  <div class="punch">Every order sells. Every order loses money.</div>
</div>
```

Bar widths = value ÷ max value × 100%. Sum row gets `wf-sum` (heavy top border, bigger type).

---

## 2. Contrast cards — wrong vs right, before vs after

**Use for:** correction rules, myth-busting, migration before/after, "the prototype did X, the real system must do Y".

```html
<div class="rules">
  <div class="rule">
    <b>PRIME is a discount, never a fee</b>
    <span class="no">✕ prototype charged 6–8% for it</span><br>
    <span class="yes">✓ only optional program charge is Xtra 8.56%</span>
  </div>
  <!-- 2–4 more .rule cards -->
</div>
```

Red left-border carries the "warning" semantics. Keep each card to one rule, ≤2 lines per side.

---

## 3. Numbered timeline — user journey, sequence, rollout phases

**Use for:** how a user moves through the product, deployment sequences, incident timelines. Final step can take `.dot.gold` to mark the payoff.

```html
<div class="journey">
  <div class="jstep"><div class="jcol"><div class="dot">1</div></div>
    <div class="jline"><b>User sees the fee-hike post</b><span>the acquisition window opens</span></div></div>
  <div class="jstep"><div class="jcol"><div class="dot gold">2</div></div>
    <div class="jline"><b>Every CTA leads to signup</b><span>/auth?ref=... → main app</span></div></div>
</div>
```

---

## 4. Progress + slice cards — work status

**Use for:** "what's built / what's left" in a handoff. Progress bar first (instant read), then one card per work slice, plain-language title, jargon in the small desc line. Link cards to tracker.

```html
<div class="progress">
  <div class="pbar"><i style="width:86%"></i></div>
  <div class="pbar-lbl"><span>6 / 7 done</span><span>QA + ship remaining</span></div>
</div>
<div class="slices">
  <a class="slice" href="https://tracker/TICKET-1"><span class="ck">✅</span>
    <span><b>Fee calculation brain</b><span class="desc">engine + official rate tables · 39 tests</span></span>
    <span class="chip done">DONE</span></a>
  <a class="slice" href="https://tracker/TICKET-7"><span class="ck">⬜</span>
    <span><b>Final QA, then ship</b><span class="desc">mobile-first checklist on preview → merge → prod</span></span>
    <span class="chip wait">REMAINING</span></a>
</div>
```

---

## 5. Arrow funnel — pipeline, event chain

**Use for:** analytics funnels, data pipelines, request lifecycles. Terminal step gets `.gold`. Belongs in the appendix when steps carry technical event names.

```html
<div class="funnel">
  <div class="fstep"><span class="fe">$pageview</span><div class="fd">consent-gated</div></div>
  <div class="fstep"><span class="fe">calc_submit</span><div class="fd">category, profit_sign</div></div>
  <div class="fstep gold"><span class="fe">sign_up</span><div class="fd">+ person props</div></div>
</div>
```

---

## 6. Node-arrow diagram — system structure

**Use for:** architecture. **Appendix material by default** — story half should describe the system in words/journey first. `.node.hot` = the component under discussion; `.node.dark` = external boundary or outcome.

```html
<div class="arch">
  <div class="arch-row">
    <div class="node"><div class="nt">Rate tables</div><div class="ns">docs/research/ · official</div></div>
    <div class="arrow">→</div>
    <div class="node hot"><div class="nt">engine</div><div class="ns">src/lib/trueprofit/ · pure fns</div></div>
  </div>
  <div class="arch-sub"><!-- consumer row: same .node markup --></div>
  <div class="arch-note"><span>📌 one fee brain — both consumers import the same module, can never drift</span></div>
</div>
```

---

## 7. Boundary panels — scope, risks, gates

**Use for:** scope boundaries, open risks, launch gates. Marker is set per-panel via class: `.panel.in` (✓), `.panel` (✕ default), `.panel.risk` (⚠), `.panel.gate` (□).

**Dev-spec scope beat** — pair in-scope ✓ against out-of-scope ✕ side by side; the boundary line is what reviewers need to debate. Every out-of-scope item gets a one-word reason in parens (why cut: backend, later phase, other team).

```html
<div class="cols">
  <div class="panel in"><h4>In scope (v1)</h4><ul>
    <li>Manual price entry + fee calculation</li>
    <li>Category picker with search</li></ul></div>
  <div class="panel"><h4>Out of scope (v1)</h4><ul>
    <li>Link-paste autofetch (needs scraper backend)</li>
    <li>Historical price tracking (phase 2)</li></ul></div>
</div>
<div class="cols">
  <div class="panel risk"><h4>Open risks</h4><ul>
    <li><b>Accuracy is reputation</b> — one wrong cross-check = public backlash</li></ul></div>
  <div class="panel gate"><h4>Open questions</h4><ul>
    <li>Who owns rate-table updates after launch?</li></ul></div>
</div>
```

For high-stakes gates in the story half, use full-width `.gate` cards instead (amber left-border, `.gate.risk` for red).

---

## 8. Tabs — alternatives, variants, per-platform detail

**Use for:** comparing 2–4 variants (per-platform behavior, option A/B/C, env configs). JS in skeleton. Default tab must be the one most readers need; all panels render in DOM (still readable without JS via `noscript`-friendly stacking — panels just all show).

```html
<div class="tabs" data-tabs>
  <div class="tab-bar">
    <button class="tab active" data-tab="a">Option A</button>
    <button class="tab" data-tab="b">Option B</button>
  </div>
  <div class="tab-panel active" data-panel="a">…content…</div>
  <div class="tab-panel" data-panel="b">…content…</div>
</div>
```

---

## 9. Toggle / disclosure — optional depth

**Use for:** "show the math", raw payloads, edge-case detail that <20% of readers need. Native `<details>` — zero JS, accessible.

```html
<details class="more">
  <summary>Show the full fee math</summary>
  <div class="more-body">…tables, formulas…</div>
</details>
```

---

## 10. Stat strip — key numbers at a glance

**Use for:** 3–4 numbers that anchor the domain (dataset size, rates, latency targets). Mono font, one line of context under each.

```html
<div class="nums">
  <div class="num"><div class="v">1,436</div><div class="l">leaf categories × 2 shop types</div></div>
  <div class="num"><div class="v">3.21% + $0.03</div><div class="l">payment fee per order</div></div>
</div>
```

---

## 11. Screenshot frame — real UI, design mocks

**Use for:** showing devs the actual UI they're building toward — Figma exports, design mocks, current-state screenshots for redesigns. A real picture beats any diagram when the work is visual. Browser-chrome bar signals "this is a screen"; caption states what to notice, not what's visible.

```html
<figure class="shot">
  <div class="shot-bar"><i></i><i></i><i></i><span>checkout — step 2 of 3</span></div>
  <img src="data:image/png;base64,..." alt="Checkout payment step with fee breakdown panel" width="1200" height="800">
  <figcaption>Fee breakdown expands inline — no modal. This is the main change from current prod.</figcaption>
</figure>

<!-- before/after or design-vs-prod: pair two shots -->
<div class="shot-grid">
  <figure class="shot"><div class="shot-bar"><i></i><i></i><i></i><span>current prod</span></div>
    <img src="data:image/png;base64,..." alt="..."></figure>
  <figure class="shot"><div class="shot-bar"><i></i><i></i><i></i><span>target design</span></div>
    <img src="data:image/png;base64,..." alt="..."></figure>
</div>
```

**Embed rules — keep the brief self-contained:**

- Inline as base64 data URI; never link external image URLs (Figma links rot, files move).
- Compress before embedding — target ≤300 KB per image, ≤1 MB total page:
  ```bash
  sips -Z 1200 shot.png --out shot-small.png            # macOS resize
  magick shot.png -resize 1200x -quality 80 shot.jpg     # ImageMagick; photos → jpg
  base64 -i shot-small.png | wc -c                       # check payload size
  ```
- Set `width`/`height` attributes from the actual image to avoid layout shift.
- JPEG for photographic content; PNG only for crisp UI with text.
- **Never mock up a fake screenshot** — same rule as invented numbers. No design available → say so and use contrast cards or a timeline instead.
- Max 2–3 shots in the story half; more belong in appendix or paired inside tabs (idiom 8) for per-platform variants.

---

## Composition rules

- Hero = idiom 1, 2, or 3 — whichever carries the aha. Never 6 (architecture).
- Story half: max 1 idiom per beat. Appendix: pack as needed.
- Dark `.flip`/`.appx-cut` cards are emphasis — max 2 dark moments per page or they stop landing.
- Every external claim links out (tracker, ADR, spec) — brief is the map, not the territory.
