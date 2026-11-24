---
tier: "Tier 2: Methodological Benchmarks & Audio Similarity"
title: "Bedah Kritis: Agreement Among Human and Automated Estimates of Similarity in a Global Music Sample"
author: "Hideo Daikoku et al."
year: 2022
citekey: "daikoku2022agreement"
venue: "Music & Science, Vol. 5, pp. 1–16"
quartile: "Q1 Scopus (Interdisciplinary Musicology & Cognitive Science)"
dataset: "Global Music Sample (100 lagu lintas budaya dari berbagai benua)"
metode: "Human Listening Triad Test vs Automated MIR Algorithms (Essentia, Librosa, MIRtoolbox)"
gap_utama: "Belum terujinya seberapa jauh metrik kesamaan musik otomatis hasil komputasi sejalan dengan persepsi pendengaran manusia nyata secara lintas budaya."
tags:
  - literatur
  - paper-review
  - human-agreement
  - user-study
  - mir-evaluation
status: "audited"
aliases:
  - Daikoku2022-Human-Automated-Similarity
  - Human Automated Similarity Daikoku
---
# 📖 Bedah Kritis: Konsensus Manusia vs Algoritma (Daikoku et al., 2022)
## *Agreement Among Human and Automated Estimates of Similarity in a Global Music Sample*

> **Objek Bedah:** Jurnal Q1 Music & Science (39 KB text)  
> **Kedudukan dalam TA:** **Justifikasi Ilmiah Pelaksanaan User Listening Study (Bab III Subbab 3.5)**

---

## 🧭 Step 0 & 1: Konteks & Abstrak Kuantitatif
* **Konteks:** Menguji secara empiris apakah metrik jarak fitur otomatis (Euclidean distance fitur MIR) benar-benar dipersepsikan sama oleh telinga pendengar manusia.
* **Hasil Kuantitatif Konkret:**
  * Korelasi antara estimasi otomatis algoritma dan persepsi manusia berada pada tingkat sedang (*moderate correlation*, Pearson $r = 0.42 - 0.58$).
  * Pendengar manusia sangat peka terhadap perubahan mendadak pada tempo dan dinamika energi, yang sering kali tidak terdeteksi oleh metrik rata-rata global algoritma.

---

## 💡 Step 9 & 10: Sintesis & Research Gap
1. **Fakta Terbukti:** Metrik komputasional murni tidak pernah 100% identik dengan persepsi subjektif manusia; selalu terdapat disparitas perseptual.
2. **Kegunaan Praktis untuk TA:** Menjadi justifikasi mutlak mengapa Skenario 2 (Integrasi *User Listening Study* dengan $N \ge 30$ responden dan uji beda Wilcoxon) sangat bernilai tinggi di hadapan dewan penguji sidang.
