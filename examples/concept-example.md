# Example: Concept (input class A), Indonesian user

**Input:** "Jelaskan capillary pressure."

**Why this selection:** definitional topic with one quantitative relation (Pc vs Sw) whose *shape* carries the meaning. Text alone hides the hysteresis and entry pressure; an interactive page would add little unless the user wants to explore contact angle or pore size.

---

## Expected response (abridged)

```text
Intent
↓
pemahaman konsep

Topic
↓
capillary pressure (tekanan kapiler)

Problem structure
↓
definisi + fisika antarmuka + relasi kuantitatif Pc–Sw

Best representation
↓
penjelasan terkontrol
+ persamaan Young–Laplace (dengan arti fisis)
+ kurva Pc–Sw skematik (drainage vs imbibition)
```

Interaktif tidak dipilih: satu kurva skematik sudah menunjukkan bentuknya. Bisa ditambah kalau ingin mengeksplorasi pengaruh contact angle.

**Layer 1 — Intuisi.** Di pori yang sempit, batas antara dua fluida yang tidak bercampur melengkung. Lengkungan itu menahan tekanan. Selisih tekanan di kedua sisi batas disebut capillary pressure (Pc).

**Layer 2 — Mekanisme.** Pc = P<sub>non-wetting</sub> − P<sub>wetting</sub>. Fluida wetting lebih suka menempel di permukaan batuan. Supaya fluida non-wetting masuk ke pori, tekanannya harus melebihi tekanan fluida wetting sebesar Pc. Pori yang lebih kecil membuat lengkungan lebih tajam, sehingga Pc lebih besar.

**Layer 3 — Kuantifikasi** (established, model tabung kapiler silindris):

Pc = 2 σ cos θ / r

| Simbol | Arti | Satuan |
|---|---|---|
| σ | interfacial tension antara dua fluida | N/m |
| θ | contact angle, diukur melalui fasa wetting | derajat |
| r | jari-jari pore throat | m |
| Pc | capillary pressure | Pa |

Cek dimensi: (N/m)/m = N/m² = Pa. Asumsi: pori berbentuk tabung silindris, antarmuka berbentuk bola. Batuan nyata tidak memenuhi asumsi ini, jadi persamaan ini menjelaskan arah pengaruh (σ, θ, r), bukan nilai Pc batuan nyata.

**Kurva Pc–Sw** (skematik, tanpa nilai):

- Pada drainage (fasa non-wetting mendesak fasa wetting), Pc naik saat Sw turun. Fasa non-wetting mula-mula mengisi pori besar (Pc rendah), lalu pori yang makin kecil (Pc tinggi).
- Entry pressure: Pc minimum agar fasa non-wetting mulai masuk ke pori terbesar.
- Kurva menjadi hampir vertikal mendekati irreducible water saturation.
- Kurva imbibition berada di bawah kurva drainage (hysteresis). Penyebab yang umum dikutip: contact angle hysteresis dan trapping fasa non-wetting.

**Layer 5 — Batas.** Bentuk dan nilai Pc–Sw harus diukur pada sampel (mis. mercury injection, porous plate, centrifuge). Konversi antar sistem fluida memakai σ cos θ, dan konversi ini juga membawa asumsi.

---

## What the example demonstrates

- Decision block first, in Indonesian; English term kept (capillary pressure, drainage, imbibition, entry pressure) per language rules.
- Equation with symbols, units, dimension check, assumptions, and validity.
- Schematic curve described without invented numbers.
- No unnecessary interactive page; the rejection is stated in one line.
