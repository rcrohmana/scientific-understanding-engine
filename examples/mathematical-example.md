# Example: Mathematical model (input class C), Indonesian user

**Input:** "Gue masih bingung kenapa di Buckley-Leverett ada shock front."

**Why this selection:** the question is about *why* a discontinuity appears. The reason is in the shape of fw(Sw) and its derivative, so a plot with the tangent construction is the core. Interaction helps because the shape (and therefore Swf and breakthrough) changes with viscosity ratio and kr exponents. Video is not needed.

---

## Expected response (abridged)

```text
Intent
↓
pemahaman konsep ilmiah

Topic
↓
Buckley-Leverett shock front

Problem structure
↓
matematis + fisis + dinamis

Best representation
↓
controlled explanation
+ fractional-flow plot
+ tangent construction visualization
```

**Layer 1 — Intuisi.** Air didorong masuk ke batuan berisi minyak. Saturasi air yang lebih tinggi seharusnya bergerak lebih cepat. Kalau saturasi di belakang bergerak lebih cepat daripada saturasi di depannya, saturasi di belakang menyusul. Hasilnya adalah lompatan saturasi yang tajam: shock front.

**Layer 2 — Mekanisme.** Kecepatan setiap nilai Sw sebanding dengan dfw/dSw (bukan dengan fw). Pada kurva fw berbentuk S, dfw/dSw naik lalu turun. Saturasi pada bagian kurva yang naik (dekat Swi) bergerak lebih lambat daripada saturasi di atasnya. Saturasi-saturasi itu tidak bisa membentuk profil kontinu, sehingga profil menjadi lompatan.

**Layer 3 — Kuantifikasi** (derived dari kekekalan massa 1D):

∂Sw/∂tD + (dfw/dSw) ∂Sw/∂xD = 0,   fw = 1 / (1 + (kro/krw)(μw/μo))

| Simbol | Arti | Satuan / status |
|---|---|---|
| Sw | saturasi air | fraksi |
| fw | fractional flow air | fraksi |
| kro, krw | relative permeability | fraksi; dari data SCAL atau model Corey (assumed) |
| μw, μo | viskositas | cP (hanya rasio yang dipakai) |
| xD = x/L, tD = qt/(ALφ) | jarak dan waktu tak berdimensi | – ; tD dalam pore volume injected |

Asumsi: 1D, homogen, inkompresibel, immiscible, tekanan kapiler dan gravitasi diabaikan, saturasi awal seragam = Swi.

Saturasi front Swf dari Welge tangent, yaitu garis dari (Swi, 0) yang menyinggung fw:

dfw/dSw |Swf = fw(Swf) / (Swf − Swi)

Garis singgung yang sama memotong fw = 1 di S̄w saat breakthrough, dan tD,bt = S̄w − Swi.

**Layer 4 — Sensitivitas.** μo/μw naik → kurva fw bergeser ke kiri → Swf lebih kecil dan breakthrough lebih cepat. Artefak interaktif: `examples/buckley-leverett-explainer.html`.

**Layer 5 — Batas.** Front yang benar-benar tajam muncul karena Pc diabaikan. Dengan Pc, front menyebar dalam zona transisi. Heterogenitas dan viscous fingering bisa membuat breakthrough di lapangan lebih awal daripada prediksi 1D.

---

## What the example demonstrates

- The user's decision-block format, filled in Indonesian with English technical terms kept.
- Casual register ("gue masih bingung") answered in clear Indonesian, still precise.
- Equations come with symbols, units, assumptions, and the reason the shock forms (non-monotonic dfw/dSw).
- Interaction justified by a shape that changes, and linked to a verified page.
