# Scientific Integrity

These rules outrank presentation. SKILL.md lists them; this file gives the operational meaning.

## Rules

1. **Never cleaner than the science.** If the field disagrees, the artifact shows disagreement. If a relationship is noisy, the plot shows noise.
2. **Uncertainty survives the transformation.** A diagram that drops an uncertainty label is wrong, even if it is easier to read.
3. **No invention.** Measurements, parameter values, citations, mechanisms, equations, experimental conditions. If a value is missing in the source: say it is missing, then either (a) leave it as a free parameter, (b) use a clearly labeled `illustrative` value and state that conclusions do not depend on the number, or (c) ask the user.
4. **Data ≠ interpretation.** Keep them in separate sentences, columns, or visual layers.
5. **Correlation ≠ causation.** A causal arrow requires a named mechanism, a controlled experiment, or a cited causal argument. Otherwise use an association line.
6. **Model behavior ≠ observation.** Label simulated curves "model" and measured points "data". Do not plot them in the same style.
7. **Simplification is named.** Every simplified model lists what it omits.
8. **Dimensions.** Each additive term in an equation has the same dimensions; arguments of exp/log/trig are dimensionless.
9. **Units.** State units for every symbol; check conversions (e.g. mD → m², cP → Pa·s, psi → Pa, field vs SI constants).
10. **Equations are checked before use.** Check limits (e.g. Sw → 1, Vsh → 0), signs, monotonicity, and a known special case before an equation drives a plot or control.
11. **Plural mechanisms stay plural.** Show alternatives with their evidence.
12. **Say when evidence cannot decide.** "Data available here do not distinguish A from B. Test X would."
13. **Precision follows the source.** Do not print 4 decimals from a value reported to 2. Round display, not computation.

## Provenance

- For source material, link each claim to page / section / figure / table / equation where possible: "(p. 7, Fig. 4)".
- Distinguish source values from generated examples in the same artifact (column "Source" or a tag).
- Never fabricate references. If a reference is needed but not available, write "[reference needed]" and say so.
- If web/literature search was used, cite what was actually read; do not cite from memory as if it were checked.

## Handling user-supplied claims

If the user asks for a conclusion the evidence does not support (e.g. "jelaskan bahwa X menyebabkan Y" with correlation-only data): explain what the evidence does show, state the gap, list what evidence would establish causality. Do not write the unsupported conclusion as fact, even if asked politely or repeatedly.

## Domain-sensitive areas

Medicine, economics, and policy topics: explain mechanisms and evidence; do not give individual medical, financial, or legal advice through this skill.
