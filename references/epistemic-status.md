# Epistemic Status

Every key statement, value, arrow, and curve carries one status. The label tells the user how much to trust it and where it came from.

| Label (EN) | Label (ID, optional) | Meaning | Example |
|---|---|---|---|
| Observed | Teramati | Seen directly, qualitative | Core shows calcite cement in pore throats |
| Measured | Terukur | Instrument value with units, ideally with uncertainty | k = 120 mD (core plug, Klinkenberg-corrected) |
| Reported | Dilaporkan | Value or claim stated by a source, not checked here | "Paper reports 15% IOR (Table 3)" |
| Calculated | Dihitung | Computed from measured/reported inputs with a known equation | Sw from Archie with given Rw, a, m, n |
| Derived | Diturunkan | Follows mathematically from stated premises | Welge tangent condition from BL theory |
| Modeled | Dimodelkan | Output of a model; depends on model assumptions | Simulated recovery factor |
| Inferred | Disimpulkan | Reasoned from evidence, not directly observed | Permeability loss likely from fines migration |
| Interpreted | Diinterpretasi | Meaning assigned to data by an analyst | "Cluster 2 = shaly sand" |
| Hypothesized | Hipotesis | Proposed, testable, not yet supported | MIE is the dominant mechanism here |
| Assumed | Diasumsikan | Taken as true for the analysis | Incompressible fluids; Pc neglected |
| Established | Mapan | Widely accepted, repeatedly confirmed | Darcy's law for laminar flow in porous media |
| Uncertain | Belum pasti | Evidence conflicting or insufficient | Which LSWF mechanism dominates in carbonates |

Parameter values in artifacts additionally use: `default` (tool's starting value, no source), `illustrative` (chosen only to show shape), `hypothetical` (scenario value).

## Forbidden silent conversions

- interpretation → fact
- correlation → causation
- model output → observation
- assumption → measured parameter
- hypothesis → established mechanism
- reported → verified (if you did not check it, it stays "reported")

## How to show status

- **Text:** a short tag the first time a claim appears: "(measured)", "(interpretasi penulis)", "(hipotesis)". Do not tag every sentence; tag claims whose status matters.
- **Diagrams:** line style per status (solid = established/measured, dashed = inferred/hypothesized, dotted = association only) with a legend. See `visualization-guidelines.md`.
- **Tables:** a "Status" column.
- **Interactive/simulation:** every parameter shows its source tag next to the control.

## Test

If the user asked "how do we know this?" for any element, the artifact should already show the answer or say "not known".
