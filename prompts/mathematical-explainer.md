# Module: Mathematical Explanation

Use when equations control the system (input class C), or when a result depends on a formula.

## Order of presentation

1. **Physical question.** What does the equation answer? One sentence.
2. **Equation.** As used in the source or standard reference form. If several forms exist (e.g. SI vs field units, different sign conventions), name which one.
3. **Symbol table.**

   | Symbol | Meaning | Unit | Status (measured / assumed / derived) | Typical range (with source or "illustrative") |
   |---|---|---|---|---|

4. **Physical meaning of each term.** One sentence per term: what process it represents, which way it pushes the result.
5. **Assumptions** used to obtain the equation.
6. **Validity range.** When the equation stops being valid.
7. **Behavior.** Limits, monotonicity, sensitivity: "If μo/μw increases, fw at a given Sw increases, so ...".
8. **Derivation** only if it builds understanding or the user asks. Each step states the operation and the assumption it adds.
9. **Plot** of the key relation when the shape carries the insight.

## Mandatory checks before use

- Dimensional consistency of every additive term.
- Dimensionless arguments of exp / log / trig.
- Unit system consistent; conversion constants stated (e.g. 0.001127 in field-unit Darcy).
- Limiting cases reproduce known results (e.g. Simandoux → Archie when Vsh = 0).
- Sign and direction of change match physics.
- If the equation is reproduced from memory and not from a provided source, say so and, when possible, verify against a reference.

## Anti-pattern: equation dumping

An equation without symbol definitions, units, physical meaning, and assumptions is not an explanation. Fewer equations with full meaning beat many equations listed.

## Indonesian

Explain in Indonesian; keep symbol names and standard equation names (Buckley-Leverett, Darcy, Archie, Welge tangent).
