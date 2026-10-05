# Representation Selection

Goal: the smallest set of representations that lets the user see **why** the result occurs. Every representation added must answer a question the previous ones could not.

## 1. Structure → representation

| Problem structure (from structure analysis) | Primary representation | Typical companion |
|---|---|---|
| Definitional / terminological; distinctions between similar terms | Controlled text | Small comparison table |
| Causal, one pathway | Controlled text with explicit cause → mechanism → consequence chain | Causal diagram if > 3 links |
| Causal, several interacting or competing mechanisms | Causal diagram with epistemic labels | Evidence/uncertainty table |
| Relational, hierarchical, taxonomic (no implied causality) | Concept map | Short text |
| Sequential: workflow, experiment, algorithm, processing chain | Process diagram | Per-step text: input, operation, output, assumption |
| Spatial arrangement (depositional system, pore geometry, well layout) | Spatial conceptual diagram | Short text |
| Governed by equations | Mathematical explanation (symbols, units, assumptions, validity) | Plot of the key relation |
| Quantitative, nonlinear, threshold, trend, comparison | Static plot | One-paragraph reading guide |
| Multi-parameter sensitivity where the *response shape* changes | Interactive HTML | Equations + assumptions panel |
| Evolution in time/space where IC/BC matter | Simulation (interactive or scripted) | "What this model does NOT represent" |
| Motion or progressive transformation *is* the mechanism | Animation | Static key frames for reference |
| Several representations must be integrated in sequence, narration lowers load | Explainer video | Script + storyboard delivered too |
| Data-driven result (clusters, regressions, ML) | Data plot of the actual result | Feature interpretation + caveats; no unsupported labels |
| Paper | Reasoning chain (question → data → method → observation → analysis → interpretation → claim) | Claim–evidence table with provenance |

## 2. Escalation rule

Order of cost: text < table < diagram < static plot < interactive < simulation < animation < video.

Move to the next level only if the current level fails one of these tests:

- **Static plot → interactive:** the user needs to see how the *shape* of the response changes over ≥ 2 parameters, or the insight is in the sensitivity itself. One parameter with 3–4 values usually fits a static family of curves.
- **Interactive → simulation:** the state evolves (time or space) and the evolution, not just the end state, is the point.
- **Plot/simulation → animation:** a static sequence of frames loses the mechanism (e.g. a front moving, a tangent construction being built step by step).
- **Animation → video:** several representations must be connected with narration, and the user asked for, or will present, a sequential explanation. Never choose video because it looks impressive.

## 3. Down-selection rule

After choosing, remove any representation that:

- repeats information already visible in another one,
- shows a relationship that the source does not support,
- needs a fabricated value to be drawn (unless the value is labeled illustrative and the shape, not the number, is the point).

## 4. Worked selections

```text
Capillary pressure (concept, ID: "Jelaskan capillary pressure")
→ controlled explanation (definition, Young–Laplace link, wettability role)
→ Pc–Sw curve (drainage vs imbibition, labeled schematic)
→ optional interactive wettability comparison (only if the user wants to explore contact angle / pore radius)
```

```text
Deltaic depositional system
→ spatial conceptual diagram (plan + section view)
→ facies relationship map
→ short explanation
(no plot: no quantitative relation is being asked)
```

```text
Buckley-Leverett displacement / shock front
→ controlled explanation (why a shock forms: dfw/dSw is non-monotonic)
→ fractional-flow plot
→ Welge tangent construction
→ interactive parameter controls (μo/μw, Corey exponents, Swi, Sor)
→ optional animation of saturation profile vs time
```

```text
Pressure diffusion (well test, transient flow)
→ mathematical explanation (diffusivity equation, η = k/(φ μ ct))
→ pressure-vs-distance plot at several times
→ time-evolution simulation or animation
```

```text
Low-salinity waterflooding
→ mechanism map with competing mechanisms (MIE, double-layer expansion, fines migration, pH increase, ...)
→ evidence/uncertainty labels per arrow
→ controlled explanation
(no single "the mechanism")
```

```text
Machine-learning clustering result
→ visualization of the actual clusters (e.g. crossplot / PCA colored by cluster)
→ feature interpretation (cluster centroids, distributions)
→ uncertainty and caveats (k choice, scaling, stability)
→ no geological labels unless supported by core/independent data
```

```text
Simple definition ("Apa itu porositas efektif?")
→ controlled text only, maybe one sentence contrasting with total porosity
(no diagram, no interactive)
```

## 5. Combined outputs that are usually valid

- controlled explanation + causal diagram
- equation explanation + interactive plot
- spatial diagram + short controlled text
- simulation + parameter-sensitivity explanation
- animation + equation derivation + narration

## 6. When the user overrides

Honor explicit modes (`references/output-modes.md`). If the forced representation would misstate the science, keep the form and add the missing label (e.g. "association, mechanism not established").

## 7. Extension points

New representation types (3D visualization, notebook explainer, digital twin, literature evidence map, uncertainty visualization, domain adapters) are added by: one row in table §1, one escalation test in §2 if needed, one module in `prompts/`, one test in `tests/skill-test-cases.md`.
