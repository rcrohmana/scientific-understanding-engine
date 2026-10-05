# Module: Scientific Consistency Review

Run on every artifact before delivery. Fix problems; do not just list them. Report remaining unresolved issues to the user.

## Checklist

**Physics**
- [ ] Causal relationships physically plausible; signs and directions correct.
- [ ] Conservation principles (mass, energy, charge, volume balance) respected.
- [ ] Time and length scales consistent with the mechanism.

**Mathematics**
- [ ] Equations match the source or a standard reference; form (units system, sign convention) named.
- [ ] Symbols consistent across text, equations, plots, and code.
- [ ] Limiting cases checked.

**Units**
- [ ] Every symbol has a unit; additive terms dimensionally consistent.
- [ ] Conversions correct; field-unit constants stated.

**Evidence**
- [ ] Each conclusion supported by cited evidence or labeled as interpretation/hypothesis.
- [ ] Provenance (page/figure/table/equation) attached where source material exists.

**Epistemology**
- [ ] Observation, calculation, model output, and interpretation visibly separated.
- [ ] No forbidden silent conversion (`references/epistemic-status.md`).

**Causality**
- [ ] Every causal arrow justified; association shown as association.
- [ ] Competing mechanisms shown when plausible; "evidence insufficient" stated where true.

**Assumptions & parameters**
- [ ] Hidden assumptions exposed.
- [ ] Every number has a source tag; no invented values; missing values stated as missing.
- [ ] Values physically plausible; displayed precision ≤ source precision.

**Model boundaries**
- [ ] Limitations and "What this model does NOT represent" present for models/simulations.

## Failure-mode scan

| Failure mode | Check |
|---|---|
| Pretty but wrong | Re-derive one key number or curve point independently. |
| Diagram hallucination | Each arrow has a one-line justification. |
| Parameter hallucination | Each number traced to source or labeled illustrative/assumed. |
| False precision | Compare displayed decimals to source decimals. |
| Mechanism collapse | Count plausible mechanisms in literature/source vs shown. |
| Simulation theater | Change each control; confirm model output changes accordingly and correctly. |

If an item cannot be checked (no source, no execution tool), say which item and why.
