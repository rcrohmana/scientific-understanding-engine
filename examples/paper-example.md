# Example: Paper understanding (input class D)

> **Fictional input.** The "paper" below is constructed for this example only. It does not summarize any real publication. Page/figure numbers refer to the fictional paper.

**Input:** "Bantu saya memahami paper ini" + PDF. The paper reports core-flood experiments with low-salinity brine on four sandstone plugs and concludes that "multi-component ion exchange (MIE) is the mechanism of incremental recovery".

---

## Expected response (abridged)

```text
Intent
↓
memahami alur penalaran paper

Topic
↓
low-salinity waterflood core flood, klaim mekanisme MIE

Problem structure
↓
eksperimen → observasi → interpretasi mekanisme; evidence perlu diuji

Best representation
↓
rantai penalaran
+ tabel klaim–evidence dengan lokasi
+ penjelasan terkontrol
```

**Rantai penalaran**

```text
Pertanyaan: apakah brine salinitas rendah menambah recovery? (p.1, §1)
   ↓
Data: 4 plug sandstone, brine tinggi lalu rendah (p.3, Table 1)
   ↓
Metode: secondary + tertiary core flood; Ca²⁺ dan Mg²⁺ diukur di effluent (p.4, §2.3)
   ↓
Observasi: tambahan recovery pada 3 dari 4 plug (p.6, Fig. 4); Ca²⁺ effluent naik (p.7, Fig. 5)
   ↓
Interpretasi: kenaikan Ca²⁺ = bukti MIE (p.8, §4.1)
   ↓
Kesimpulan: MIE adalah mekanisme (p.10, §5)
```

| Klaim | Lokasi | Evidence | Status | Kekuatan | Celah / alternatif |
|---|---|---|---|---|---|
| Low-salinity menambah recovery | Fig. 4 | 3 dari 4 plug | observed | moderat (n kecil, tanpa ulangan) | plug ke-4 tidak dijelaskan |
| Ca²⁺ effluent naik | Fig. 5 | pengukuran effluent | measured | kuat untuk observasinya | pelarutan mineral juga menaikkan Ca²⁺ |
| MIE adalah mekanisme | §5 | korelasi Ca²⁺ dan recovery | interpreted | lemah | double-layer expansion, fines migration, kenaikan pH tidak diuji |

**Parameter yang tidak dilaporkan:** temperatur aging, komposisi mineral lempung, laju injeksi pada tahap tertiary. Tanpa data ini, mekanisme alternatif tidak bisa disingkirkan.

**Pembacaan yang didukung evidence:** paper menunjukkan tambahan recovery dan perubahan kimia effluent. Paper belum menunjukkan bahwa MIE, dan bukan mekanisme lain, yang menyebabkan tambahan recovery.

---

## What the example demonstrates

- Reasoning chain, not section-by-section summary.
- Provenance on every item.
- Author's interpretation labeled as interpretation; strength graded.
- Missing parameters stated as missing, not filled in.
- Alternatives named as "outside this paper" knowledge, not attributed to the authors.
