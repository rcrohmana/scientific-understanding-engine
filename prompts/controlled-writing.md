# Module: Controlled Scientific Writing

Default style for all prose in this skill: about 80% ASD-STE100-inspired. The goal is controlled scientific readability. It is **not** STE compliance, and the output must never claim compliance.

## Rules

1. Short sentences. Target ≤ 20 words for procedural/causal statements, ≤ 25 for descriptive ones. Break longer sentences unless breaking them loses a qualifier.
2. One main idea per sentence.
3. Explicit subject. Say what does the action: "Water displaces oil", not "Displacement occurs".
4. Consistent terminology. Choose one term per concept and keep it. Do not alternate synonyms for style ("shale volume" / "clay content" / "Vsh" are not interchangeable).
5. Define each technical term at first use, in one sentence.
6. Explicit causality: use "because", "so", "causes", "increases", "decreases". Name the direction of change.
7. Controlled pronouns. Replace "it/this/ini/itu" with the noun when more than one candidate referent exists.
8. Few modifiers. Remove "very", "significantly" (unless statistical), "sangat", "cukup". Keep quantitative qualifiers.
9. Preserve uncertainty words that carry meaning: "may", "likely", "is not known", "diduga", "belum terbukti". Do not delete them for brevity.
10. No rhetoric: no "fascinating", "crucial", "plays a key role", "tidak dapat dipungkiri", "perlu diketahui bahwa".
11. Do not oversimplify. If a short sentence would become false, use a longer sentence or two sentences.

## Indonesian application

ASD-STE100 is defined for English; its dictionary does not apply to Indonesian. Transfer the principles, not the word list:

- Short sentences, one idea, explicit subject ("Air mendesak minyak", not "Terjadi pendesakan").
- Prefer active verbs over nominalizations ("tekanan turun" rather than "terjadinya penurunan tekanan").
- Avoid stacked "yang ... yang ..." clauses; split the sentence.
- Keep English technical terms per SKILL.md language rules; italicize only at first gloss if the target document style asks for it.
- Decimal comma in Indonesian prose.

## Template

```text
[Term] is [definition in one sentence].            ← define
[Cause] [verb of change] [effect].                  ← one causal link per sentence
This happens because [mechanism].                   ← mechanism
[Observable consequence] shows this effect.         ← observation link
This explanation assumes [assumption].              ← assumption
It does not hold when [limit].                      ← validity
```

Indonesian:

```text
[Istilah] adalah [definisi satu kalimat].
[Penyebab] [menaikkan/menurunkan] [akibat].
Hal ini terjadi karena [mekanisme].
[Gejala yang teramati] menunjukkan efek ini.
Penjelasan ini mengasumsikan [asumsi].
Penjelasan ini tidak berlaku jika [batas].
```

## Example

Weak: "Capillary pressure, which is very important in reservoirs, basically arises due to interfacial phenomena that occur when fluids meet in pores."

Controlled: "Capillary pressure (Pc) is the pressure difference between the non-wetting phase and the wetting phase across their interface. Pc exists because the interface between two immiscible fluids is curved in a narrow pore. A smaller pore radius gives a larger curvature, so Pc increases. In a water-wet rock, Pc rises as water saturation decreases, because the remaining water occupies smaller pores."
