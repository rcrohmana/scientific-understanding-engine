# Module: Causal Reasoning

Use for mechanisms (input class B), experimental results needing explanation (E), and user hypotheses (J).

## Step 1 — Separate observation from explanation

List what is **observed/measured** first, with source and status. Only then list explanations.

## Step 2 — Build chains

Established or well-supported link:

```text
Cause
↓
Intermediate physical / chemical / biological mechanism
↓
Observable consequence
```

Incomplete evidence:

```text
Observation
↓
Possible mechanism   (status: hypothesized / inferred)
↓
Prediction that would support the mechanism   (measurable, specific)
```

Multiple explanations:

```text
Observation
├── Hypothesis A — supporting evidence / against / missing test
├── Hypothesis B — ...
└── Hypothesis C — ...
```

Never collapse the tree into one branch unless evidence discriminates. If evidence discriminates, show the discriminating evidence.

## Step 3 — Justify each arrow

For every arrow, write one line: mechanism or evidence, and status. Use the arrow semantics in `references/visualization-guidelines.md` (→ causal, ↔ feedback, ⇢ inferred, — association). Remove arrows that have no justification.

## Step 4 — Check physical consistency

- Direction: does the cause push the effect the stated way? (Sign check.)
- Magnitude: can the mechanism plausibly produce the observed size of effect? If unknown, say so.
- Time scale: is the mechanism fast/slow enough for the observed timing?
- Conservation: mass, charge, energy balance not violated.
- Confounders: what else changed at the same time?

## Step 5 — Evidence table

| Mechanism | Status | Supporting evidence | Evidence against | Discriminating test |
|---|---|---|---|---|

## Checking a user's proposed mechanism (class J)

1. Restate the mechanism as a chain.
2. Run Step 4 on each link.
3. Report per link: consistent / inconsistent / cannot be judged with given information.
4. Suggest alternative mechanisms the user did not mention.
5. Name the observation that would falsify the proposal.

Do not validate a mechanism to please the user. Do not reject it without a specific reason.

## Diagram output

Mermaid `flowchart` with status in edge labels and a legend. Provide an indented-text fallback.
