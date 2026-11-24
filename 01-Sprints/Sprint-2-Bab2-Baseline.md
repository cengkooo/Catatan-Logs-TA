---
title: "Sprint 2: Bab 2 & Baseline (RE-BASELINE 16 NOV)"
status: "IN PROGRESS"
tags:
  - sprint
  - bab2
  - baseline
window: "2026-11-18 → 2026-11-23"
deadline: 2026-11-23
---

# 🔬 Sprint 2: Bab 2 & Baseline

> [!danger] Re-baseline 16 Nov 2026 — overdue 9 hari
> Sprint ini seharusnya selesai **14 Nov**. Per 16 Nov: **0 dari 4 task**. Dipadatkan ke 18–23 Nov.
> Rencana induk: [[EMERGENCY-SEMPRO]] · Sheet: tab **🚨 EMERGENCY 16-25 NOV**

- **Status:** `IN PROGRESS`
- **Window:** 18 – 23 Nov 2026
- **Output:** Draf Bab 2 (`chapters/bab2.tex`) + Skrip baseline PoC
- **Dashboard:** [[Master-Dashboard]] | [[Roadmap-Sempro]]

---

## 🎯 Target & Checklist Kerja

- [ ] **T-05** Studi literatur → *Rab 18 Nov 10:00–11:00, 16:30–18:30 & Kam 19 Nov 07:00–09:00*
  - Output: matriks **15 paper Q1/Q2 (2021–2026)** di [[Matriks-Sintesis]] + 2 hlm Bab 2
- [ ] **T-06** Bedah Mood Trajectory & Trajectory Alignment (Gaur 2020) → *Rab 18 Nov 19:30–21:45*
  - Output: diagram konsep vektor trajectory per segmen lagu + 1 hlm kajian model 2-tahap
- [ ] **T-07** Baseline KNN Gaur & Donnelly (Replikasi 2-Tahap) → *Sab 21 Nov 07:00–11:00 + 13:00–15:30*
  - Output: script KNN kandidat + kriteria akustik jalan, 1 run playlist vs random (subsample 20%), metrik awal
- [ ] **T-08** ACC & Izin Sempro → *Sen 23 Nov 19:30–21:45*
  - Output: ACC naskah utuh + **TTD lembar pengesahan**
  - Fallback: slot bimbingan **Rab 25 Nov 14:00**

---

## ⏱️ Alokasi Waktu (dari Google Calendar)

| Blok | Agenda | Output |
| :--- | :--- | :--- |
| Rab 10:00–11:00 | T-05 matriks (5 paper) | 5 baris matriks |
| Rab 16:30–18:30 | T-05 literatur (10 paper) | sintesis 1 hlm |
| Rab 19:30–21:45 | T-06 arsitektur & loss | diagram + 1 hlm |
| Kam 07:00–09:00 | T-05 final + nulis Bab 2 | matriks 15 + 2 hlm |
| Sab 07:00–11:00 | T-07 setup pipeline | script jalan |
| Sab 13:00–15:30 | T-07 Benchmark Run Baseline | 1 run Q3->Q1 + metrik |
| Sen 19:30–21:45 | **T-08 ACC & TTD** | ACC + TTD |

---

## 📝 Catatan Perkembangan Sprint
- **Risiko R-02:** kuota GPU/Colab. Mitigasi: subsample 20%, checkpoint ke Drive, cukup 1 run untuk sempro.
- **Jangan** mengejar hasil SOTA. Proposal butuh **pipeline terbukti jalan**, bukan akurasi tinggi.
- Paper kunci: [[Gaur2020-Mood-Arc]] · [[DEAM-Dataset]]
