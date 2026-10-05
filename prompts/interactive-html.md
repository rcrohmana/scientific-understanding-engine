# Module: Interactive HTML Explainer

Use only when parameter manipulation builds understanding a static plot cannot (see escalation test in `references/representation-selection.md`).

Before building: if the host offers a page-design skill (e.g. `artifact-design`) or a charting skill (e.g. `dataviz`), load it and follow its page contract (theming, allowed CDNs, size). This module governs the scientific content.

## Required sections (when relevant)

1. **Scientific question** — one line at the top.
2. **System sketch** — small SVG or diagram of what is being modeled.
3. **Controls** — one per real model variable. Each control shows: symbol, name, unit, range, current value, and a source tag: `reported` / `measured` / `calculated` / `assumed` / `default` / `illustrative` / `hypothetical`.
4. **Governing equations** — the exact equations the code evaluates, with symbol table.
5. **Plots** — driven by the same function that computes the readouts.
6. **Calculated outputs** — key numbers with sensible precision.
7. **"What changed and why"** — 1–3 sentences that update with the controls, explaining the physical reason for the change (not just restating the number).
8. **Assumptions, limitations, uncertainty** — visible on the page, not hidden in a tooltip. Include "What this model does NOT represent".

## Wiring rules (anti simulation theater)

- One `model(params)` function computes everything. Plots and readouts call it; nothing is hard-coded.
- Every control changes an argument of `model`. No decorative controls.
- Ranges stay within the model's validity; clamp or warn outside it.
- Guard numerical edge cases (division by zero, empty domain, non-monotonic tangent search).
- Default values are labeled `default` or `illustrative` unless they come from the user's source.
- Show units in every label. Display precision follows the inputs.

## Verification before delivery

- Run the `model` function headless (e.g. `node -e` on the extracted function, or Python port) at 2–3 parameter sets and check limiting cases and known results.
- Open or preview the page if a browser tool exists; otherwise say it was not visually checked.

## Build defaults

- Single self-contained HTML (inline CSS/JS). Plain `<canvas>` or SVG is enough for most plots; use a charting library only when it adds clear value (zoom, many series).
- Mobile-friendly: controls stack above plot on narrow screens.
- No network calls for data; no secrets.

## Anti-pattern: HTML textbook

A page that is mostly paragraphs with styling is not interactive. Text on the page should be short and tied to what the user is manipulating.

Reference implementation: `examples/buckley-leverett-explainer.html` (described in `examples/interactive-example.md`).
