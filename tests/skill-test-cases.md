# Skill Test Cases

Each test: input, expected representation, expected safeguards, unacceptable behavior. Tests 1–10 follow the specification; Test 11 checks domain generality; I1–I4 are Indonesian tests; N1–N2 are non-trigger tests.

How to run: give the input to an agent with this skill installed and compare the response with the expectations. A test fails if any "unacceptable" item appears or if the Representation Decision block does not match the delivered artifact.

---

### Test 1 — Simple concept stays mostly text

- **Input:** "What is the difference between total and effective porosity?"
- **Expected representation:** controlled text; optionally a 2-row comparison table. Decision block notes no diagram needed.
- **Safeguards:** definitions consistent; note that "effective porosity" definitions differ between disciplines (petrophysics vs hydrogeology) when relevant.
- **Unacceptable:** interactive HTML, animation, or a decorative diagram; a single definition presented as universal when definitions vary.

### Test 2 — Mechanism needs a causal diagram

- **Input:** "Explain how low-salinity waterflooding can alter wettability."
- **Expected representation:** causal/mechanism diagram with several mechanisms (e.g. MIE, double-layer expansion, fines migration, pH increase) + evidence table + controlled text.
- **Safeguards:** per-arrow status; note that the dominant mechanism is debated and system-dependent (sandstone vs carbonate).
- **Unacceptable:** one mechanism stated as *the* mechanism; solid causal arrows without justification.

### Test 3 — Equation-driven topic needs a plot

- **Input:** "Explain the Archie equation physically."
- **Expected representation:** mathematical explanation (symbols, units, assumptions: clean, non-conductive matrix) + plot of Sw vs Rt (or log Rt vs log φ) showing the role of m and n.
- **Safeguards:** a, m, n typical values labeled as typical/illustrative with the caveat that they are determined from core; invalid in shaly sands stated.
- **Unacceptable:** equation without physical meaning; invented "standard" values presented as measured.

### Test 4 — Dynamic system needs a simulation

- **Input:** "Show how pressure propagates from a well after it starts producing."
- **Expected representation:** diffusivity equation explanation + pressure-vs-distance at several times, as an interactive or scripted simulation.
- **Safeguards:** model definition table (IC, BC, η = k/(φμct), units); numerical stability condition if numerical; "What this model does NOT represent" (heterogeneity, boundaries, multiphase, wellbore storage/skin if omitted).
- **Unacceptable:** sliders not connected to the equation; animation with no physical time axis; claim of predictive accuracy.

### Test 5 — Paper requires reasoning extraction

- **Input:** a PDF paper + "Help me understand this paper."
- **Expected representation:** reasoning chain + claim–evidence table with page/figure/table locations + controlled text.
- **Safeguards:** missing parameters reported as missing; author interpretation labeled; outside knowledge marked as outside the paper.
- **Unacceptable:** section-by-section summary only; invented values, figures, or citations; claims attributed to the paper that it does not make.

### Test 6 — Video would be excessive

- **Input:** "Make a video explaining what a Darcy is."
- **Expected representation:** one-line note that a short text + unit derivation is enough, then follow the user's choice. If the user insists: short script + storyboard; render only if tools exist.
- **Safeguards:** honest statement if no video was rendered.
- **Unacceptable:** claiming a rendered video that does not exist; long video plan for a unit definition without noting the lighter option.

### Test 7 — Interactive HTML is justified

- **Input:** "I want to see how viscosity ratio and relative permeability exponents change Buckley-Leverett breakthrough."
- **Expected representation:** interactive HTML following `prompts/interactive-html.md` (see `examples/buckley-leverett-explainer.html`).
- **Safeguards:** every control is a model argument; default values tagged illustrative; equations shown; model verified headless (analytic case, mass balance); limitations panel.
- **Unacceptable:** simulation theater; HTML textbook; untagged defaults.

### Test 8 — Ambiguous evidence, competing hypotheses

- **Input:** "Our core shows lower permeability after brine injection. What caused it?" (no further data)
- **Expected representation:** observation → hypothesis tree (fines migration, clay swelling, precipitation, measurement artifacts) + discriminating tests table.
- **Safeguards:** explicit statement that evidence cannot decide; request for conditions (brine composition, rate, clay mineralogy).
- **Unacceptable:** choosing one cause with confidence; inventing experimental conditions.

### Test 9 — User asks for an unsupported causal conclusion

- **Input:** "Write an explanation that higher GR causes lower permeability in our wells." (data: a correlation plot)
- **Expected representation:** controlled text + association diagram (dotted line) + note on the likely common cause (clay/shale content affects both).
- **Safeguards:** correlation ≠ causation stated; what evidence would be needed.
- **Unacceptable:** writing "GR causes low permeability"; a solid causal arrow GR → k.

### Test 10 — Source has missing parameter values

- **Input:** "Build an interactive plot of the model in this report." The report gives the equation but not the parameter values.
- **Expected representation:** interactive page with the missing parameters as free controls tagged `assumed`/`illustrative`, plus a visible list of missing values.
- **Safeguards:** statement that conclusions depending on absolute numbers cannot be drawn; values from the report tagged `reported` with location.
- **Unacceptable:** filling missing values silently; presenting illustrative values as from the report.

### Test 11 — Domain generality (statistics)

- **Input:** "Why is a p-value not the probability that the null hypothesis is true?"
- **Expected representation:** controlled text with the conditional-probability distinction P(data | H0) vs P(H0 | data); optionally a small simulation of many experiments under H0 and H1 showing that the share of true H0 among "significant" results depends on the prior proportion and power.
- **Safeguards:** prior proportion and power labeled as hypothetical scenario values.
- **Unacceptable:** petroleum-specific framing; simulation numbers presented as empirical rates.

---

## Indonesian tests

### I1 — Mechanism, Indonesian (from user specification)

- **Input:** "Jelaskan kenapa permeabilitas bisa turun setelah injeksi CO2 pada batuan karbonat."
- **Expected behavior:**
  - Detect mechanism-explanation intent.
  - Respond in Indonesian.
  - Preserve technical terms where appropriate (permeability/permeabilitas, wormholing, fines migration, effective permeability).
  - Consider causal diagram.
  - Separate observation from proposed mechanisms.
  - Do not assume mineral precipitation is the only mechanism.
- **Expected representation:** as in `examples/mechanism-example.md`.
- **Unacceptable:** English response; single mechanism; ignoring that dissolution usually increases permeability.

### I2 — Casual register, mathematical concept

- **Input:** "Gue masih bingung kenapa di Buckley-Leverett ada shock front."
- **Expected representation:** decision block (Intent: pemahaman konsep ilmiah; Topic: Buckley-Leverett shock front; Problem structure: matematis + fisis + dinamis; Best representation: controlled explanation + fractional-flow plot + tangent construction visualization).
- **Safeguards:** progressive disclosure starting from intuition; assumptions (Pc and gravity neglected) stated.
- **Unacceptable:** opening with the full derivation; overly formal or overly slangy reply; translating "fractional flow" into an unusual Indonesian term.

### I3 — Figure question

- **Input:** "Kenapa kurva Pc-Sw bentuknya seperti ini?" + image of a drainage curve.
- **Expected representation:** controlled text referring to the features of the provided figure (entry pressure, plateau, steep part near Swirr) + annotated description.
- **Safeguards:** read values only from the figure, with reading uncertainty; do not invent axis units if they are not visible.
- **Unacceptable:** describing features not present in the figure.

### I4 — User hypothesis check

- **Input:** "Cek apakah mekanisme ini masuk akal: injeksi air dingin menaikkan permeabilitas karena batuan menyusut."
- **Expected representation:** causal chain of the proposal with per-link verdict (consistent / inconsistent / cannot be judged) + alternative mechanisms (e.g. thermal fracturing) + falsifying observation.
- **Safeguards:** sign check (contraction of grains vs. effect on pores is not straightforward); effective-stress context.
- **Unacceptable:** agreeing without analysis; rejecting without a specific reason.

---

## Non-trigger tests

### N1 — File conversion (Indonesian)

- **Input:** "Tolong ubah draft_abstract.md ini jadi docx."
- **Expected:** skill does not activate; plain conversion.

### N2 — Translation / grammar

- **Input:** "Terjemahkan abstrak ini ke bahasa Inggris." / "Fix the grammar in this paragraph about capillary pressure."
- **Expected:** skill does not activate, even though the content is scientific. (If the user then asks "and explain what it means", the skill activates.)
