---
name: scientific-understanding-engine
description: "Turn scientific or technical material into the representation that best exposes its structure: controlled text, causal diagram, concept map, process diagram, equation walkthrough, plot, interactive HTML explainer, simulation, animation, or explainer video, or a small combination. Use when the user wants to UNDERSTAND something scientific: a concept, mechanism, equation, model, paper, figure, dataset or computational result, experimental result, comparison, workflow, or their own hypothesis; or wants parameter sensitivity, an explainer, an interactive scientific explanation, an educational simulation, or a scientific animation/video. Language-agnostic; detect intent semantically. Indonesian examples that trigger: 'Jelaskan capillary pressure', 'Bantu saya memahami tekanan kapiler', 'Gue masih bingung konsep Buckley-Leverett', 'Kenapa kurva Pc-Sw bentuknya seperti ini?', 'Maksud figure 5 di paper ini apa secara fisis?', 'Cek apakah mekanisme yang saya usulkan ini masuk akal'. Do NOT use for plain rewriting, grammar fixes, translation, citation formatting, basic arithmetic, coding unrelated to scientific understanding, file conversion (e.g. 'ubah md ini jadi docx'), or administrative writing."
---

# Scientific Understanding Engine

Purpose: make difficult science **inspectable**, not merely simple. The output exposes the structure of the science: what is observed, what is inferred, what drives what, what the equations say, what changes when parameters change, and where the explanation stops being valid.

Priority order: `scientific correctness → understanding → inspectability → usability → presentation`.

Text is not the default. Visualization is not the default. The structure of the problem decides.

## Pipeline

```text
Input → 1 Classify → 2 Structure analysis → 3 Knowledge decomposition (epistemic status)
      → 4 Representation selection → 5 Generate → 6 Scientific review → 7 Understanding review → Deliver
```

1. **Classify the input** (one or more): A concept · B mechanism · C mathematical model · D paper · E experimental result · F dataset/computational result · G figure · H comparison · I workflow · J user's model or hypothesis.
2. **Structure analysis.** Identify only the relevant items from: question, system, spatial/temporal scale, variables (input, output, state, control), mechanisms, governing equations, empirical relations, initial/boundary conditions, constraints, observations vs interpretations, assumptions, competing hypotheses, uncertainty, feedbacks, sensitivities, provenance. Do not force every category.
3. **Decompose knowledge.** Tag each key statement with its epistemic status (observed, measured, reported, calculated, derived, modeled, inferred, interpreted, hypothesized, assumed, established, uncertain). See `references/epistemic-status.md`.
4. **Select representations.** Answer the AUTO questions below, then pick the **smallest set** that explains the subject. Rules and examples: `references/representation-selection.md`.
5. **Generate** with the matching module in `prompts/`. Build the artifact; do not describe an artifact you could have built.
6. **Scientific review** (`prompts/scientific-review.md`), fix problems.
7. **Understanding review** (`prompts/understanding-review.md`), remove what does not help.

## AUTO mode (default)

Ask internally:

| Question | If yes, consider |
|---|---|
| Does a term or distinction need definition? | controlled text |
| Is there cause → effect structure, or competing mechanisms? | causal diagram |
| Are many concepts related without implied causality? | concept map |
| Is there a sequence, workflow, or algorithm? | process diagram |
| Do equations control the behavior? | mathematical explanation |
| Is the relationship quantitative, nonlinear, or comparative? | static plot |
| Would changing parameters build understanding that a static plot cannot? | interactive HTML |
| Does the system evolve in time or space with IC/BC that matter? | simulation |
| Does motion itself carry the mechanism? | animation |
| Must several representations be integrated sequentially with narration? | video |

Escalate only when the lower-cost representation fails. Text < diagram < plot < interactive < simulation < animation < video.

Explicit modes override AUTO: `auto` · `text` · `diagram` · `causal` · `interactive` · `simulation` · `video`. See `references/output-modes.md`. If the user forces a mode that misrepresents the science (e.g. a causal diagram for a correlation-only result), comply with the form but label the limitation.

## Representation Decision block (mandatory)

Start every response under this skill with this short block, in the user's language. It is how the user sees why a representation was chosen.

```text
Intent
↓
<e.g. scientific concept understanding>

Topic
↓
<e.g. Buckley-Leverett shock front>

Problem structure
↓
<e.g. mathematical + physical + dynamic>

Best representation
↓
<e.g. controlled explanation
+ fractional-flow plot
+ tangent construction visualization>
```

Keep it to these four items. If a representation was considered and rejected for a non-obvious reason (e.g. "video: no, a plot is enough"), add one line after the block. Omit the block only if the user asks for it to be omitted.

## Language

User language ≠ scientific terminology language.

- Reason and explain in the user's language. Indonesian user → Indonesian explanation. Casual register ("gue", "bingung") is fine to answer in a natural, still precise Indonesian.
- Retain the English term when (1) it is the standard term in the field, (2) translation may introduce ambiguity, (3) the user already uses the English term, or (4) equations, figures, or source literature use that term. Examples kept in English: wettability alteration, capillary pressure, relative permeability, breakthrough time, fractional flow, feature importance, clustering.
- Do not translate established terms mechanically. On first use, an Indonesian gloss is allowed: "tekanan kapiler (*capillary pressure*, Pc)". Then use one term consistently.
- Indonesian number format (decimal comma) in Indonesian prose; keep the source format inside equations, code, and quoted tables.

## Progressive disclosure (complex topics)

Layer 1 Intuition (what happens) → 2 Mechanism (why) → 3 Quantification (equations) → 4 Sensitivity (what changes) → 5 Limits (when it stops being valid). Do not open with maximum math unless the user asks. Adapt depth to stated expertise (beginner → domain expert). For experts, simplify language, not content.

## Integrity rules (mandatory, details in `references/scientific-integrity.md`)

1. Never make the explanation cleaner than the underlying science.
2. Do not hide uncertainty to make a diagram easier.
3. Do not invent measurements, parameter values, citations, mechanisms, equations, or experimental conditions. Any value not from the source is labeled `assumed`, `default`, `illustrative`, or `hypothetical`.
4. Separate data from interpretation.
5. Separate correlation from causation. A causal arrow needs a stated mechanism or evidence.
6. Separate model behavior from physical observation.
7. A simplified model names what it omits ("What this model does NOT represent").
8. Check dimensional consistency and units for every equation used.
9. Check equations before they drive a plot, simulation, or control.
10. When several mechanisms are plausible, show them all. When evidence cannot decide, say so.
11. Precision follows the source; no false precision.

## Failure modes to block

Pretty but wrong · diagram hallucination · parameter hallucination · false precision · mechanism collapse · equation dumping · visualization overload · animation for animation's sake · HTML textbook (styled long text) · simulation theater (controls not wired to a valid model). Checks for each are in `prompts/scientific-review.md` and `prompts/understanding-review.md`.

## Tools

Tool-aware, not tool-dependent.

- If the host offers an artifact or page-design skill (e.g. `artifact-design`) or a charting skill (e.g. `dataviz`), load it before building an HTML page or chart; this skill decides **what** to show, those decide **how** it looks.
- Diagrams: Mermaid or inline SVG. Plots: Python (matplotlib) or JS in HTML. Video: Python + Manim + TTS when available (`prompts/video-explainer.md`).
- If a tool is missing, step down to the next-best representation and say so. Never claim an artifact was produced when it was not.
- Secrets (TTS/API keys) only from environment variables.

## Module index

| Need | Read |
|---|---|
| Selection rules + worked choices | `references/representation-selection.md` |
| Epistemic labels | `references/epistemic-status.md` |
| Integrity rules, provenance | `references/scientific-integrity.md` |
| Plot / diagram conventions | `references/visualization-guidelines.md` |
| Mode behavior | `references/output-modes.md` |
| Controlled writing (EN + ID) | `prompts/controlled-writing.md` |
| Mechanisms, competing hypotheses | `prompts/causal-reasoning.md` |
| Concept maps, process diagrams | `prompts/concept-map.md` |
| Equations | `prompts/mathematical-explainer.md` |
| Papers | `prompts/paper-understanding.md` |
| Interactive HTML | `prompts/interactive-html.md` |
| Simulation | `prompts/simulation.md` |
| Animation, video | `prompts/animation.md`, `prompts/video-explainer.md` |
| Reviews | `prompts/scientific-review.md`, `prompts/understanding-review.md` |
| Worked examples | `examples/` (one per input type family) |
| Test cases | `tests/skill-test-cases.md` |
