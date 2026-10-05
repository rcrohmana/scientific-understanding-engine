# Example: Interactive HTML (reference implementation)

File: `examples/buckley-leverett-explainer.html` — self-contained, no external libraries, Indonesian UI with English technical terms, decimal comma in displayed numbers.

## Why interactive here

The insight is how the *shape* of fw(Sw) moves with μo/μw and Corey exponents, and how that moves Swf, breakthrough time, and recovery at breakthrough. A static family of curves covers one parameter; this case has several that interact. Escalation test passed (`references/representation-selection.md` §2).

## How it meets `prompts/interactive-html.md`

| Requirement | Implementation |
|---|---|
| Scientific question | Header line |
| Controls = real model variables | Swi, Sor, nw, no, krw°, kro°, μw, μo, plus tD for the profile time; each is an argument of `blModel()` |
| Source tag per control | All tagged `illustrative`, with a visible note that defaults are not field data |
| Single source of truth | `blModel(p)` computes fw, dfw/dSw, Welge tangent, Swf, tD,bt, S̄w,bt, RF, M, and the profile; plots and table read only from it |
| Equations shown | Exactly the equations the code evaluates |
| What changed and why | Text updates after each change and branches on which control moved: Swi/Sor → change of movable span 1 − Swi − Sor; mobility parameters → shift of fw (mentions M only when M changed); concave fw → no-shock (rarefaction) explanation |
| Assumptions + "does NOT represent" | Visible panels; "Model edukasi. Bukan untuk prediksi engineering." |

## Verification performed (headless, Node)

| Check | Result |
|---|---|
| Analytic case: Swi = Sor = 0, nw = no = 2, krw° = kro° = 1, μw = μo → Swf = 1/√2 ≈ 0.7071, tD,bt ≈ 0.8284 | model 0.7070, 0.8284 |
| Tangency: dfw/dSw at Swf equals chord slope | equal to 3 decimals at default and 4 other parameter sets |
| Mass balance at tD = 0.3: ∫(Sw − Swi) dxD = tD | 0.2996–0.3000 for 5 parameter sets, including concave fw (nw = no = 1) |
| μo 2 → 10 cP | Swf 0.58 → 0.41, tD,bt 0.46 → 0.31 PV (direction matches physics) |
| Full page script with stub DOM | runs, fills 7 table rows |
| Explanation text per control (stub DOM: Swi 0.20→0.30, Sor 0.20→0.10, μo 2→10, nw 2→3) | each sentence names the correct physical reason; Swi case: tD,bt 0.46 → 0.39 PV = 0.465 × 0.50/0.60 (span scaling) |
| Render in headless Edge (final file) | plots, labels, and panels render without overlap; screenshot reviewed |

Bugs found during verification and fixed: (1) the explanation text attributed every tD,bt drop to fw shifting left, which is wrong for a Swi change; (2) found by the mass-balance check: when fw is concave (dfw/dSw > 0 at 1 − Sor), the profile lacked the plateau at the injection end.

## Known limits of the page

- Corey kr only; no tabulated SCAL input.
- Initial saturation fixed at Swi (no mobile initial water).
- Profile plot clips at xD = 1; after breakthrough the outlet behavior (water-cut curve) is not plotted.
