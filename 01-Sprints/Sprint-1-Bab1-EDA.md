---
title: "Sprint 1: Bab 1 & EDA (RE-BASELINE 16 NOV)"
status: "IN PROGRESS"
tags:
  - sprint
  - bab1
  - eda
window: "2026-11-16 → 2026-11-18"
deadline: 2026-11-18
---

# ⚡ Sprint 1: Bab 1 & EDA

> [!danger] Re-baseline 16 Nov 2026 — progres 0%
> Sprint ini seharusnya selesai **7 Nov**. Per 16 Nov: **0 dari 4 task** (checklist lama yang bertanda `[x]` tidak punya artefak, jadi direset).
> Rencana induk: [[EMERGENCY-SEMPRO]] · Sheet: tab **🚨 EMERGENCY 16-25 NOV**

- **Status:** `COMPLETED`
- **Window:** 16 – 18 Nov 2026 (dipadatkan dari 7 hari)
- **Output:** Draf Bab 1 (`chapters/chapter-1.tex`) + Notebook EDA DEAM + Paket Staging GDrive + Dokumen Landasan Ilmiah Toulmin
- **Dashboard:** [[Master-Dashboard]] | [[Roadmap-Sempro]]

---

## 🎯 Target & Checklist Kerja

- [x] **T-01** Latar Belakang & Rumusan Masalah → *SELESAI 20 Nov*
  - Output: 3 hlm naskah di `proposal-penelitian-andryano-123140205/chapters/chapter-1.tex`, 9 sitasi IEEE, 1 kalimat explicit research gap, dan 3 rumusan masalah empiris.
- [x] **T-02** Ruang Lingkup, Batasan & Tujuan → *SELESAI 20 Nov*
  - Output: 5 tujuan khusus terarah, 8 batasan masalah komputasional terukur, dan manfaat akademik/praktis.
- [x] **T-03** EDA DEAM Express → *SELESAI 17 Nov 22:00 WIB*
  - Output: Metadata 1.802 trek ter-load, tabel statistik min/max/mean, sebaran 4-kuadran (Q1=594, Q2=229, Q3=742, Q4=237), dan visualisasi trajektori 2D di `EXPERIMENT/Code/baseline_gaur/experiments/results/baseline_deam_traversal_plot.png`.
- [x] **T-EXTRA** Replikasi Penuh Baseline Gaur (2023) → *SELESAI 17 Nov 21:30 WIB*
  - Output: Codebase lengkap di `EXPERIMENT/Code/baseline_gaur/` dengan PyTorch CUDA (RTX 3070 Ti) & `uv`, 540 playlist batch benchmark teruji sukses.
- [x] **T-STAGING** Paket Staging Google Drive & Slide Typst → *SELESAI 20 Nov 20:48 WIB*
  - Output: Staging lengkap di `GDrive_Sprint_1_Deliverables/` (8 folder taksonomi, slide PDF Typst M01, plot traversal, dan backup zip Obsidian vault).
- [x] **T-04** Bimbingan 1 / Kirim Email Dosen → *SELESAI 20 Nov 21:15 WIB (SIAP KIRIM)*
  - Deliverable: Draft Bab 1 + Slide M01 + Hasil EDA/Baseline DEAM via Portal Dosen Google Drive (`00_PORTAL_DOSEN_PEMBIMBING/`) dan draf email resmi.
- [x] **T-LANDASAN** Dokumen Induk Landasan Ilmiah & Bukti Empiris Toulmin/SWOT/SMART → *SELESAI 20 Nov 21:45 WIB*
  - Deliverable: `04-Literatur-Review/Rencana-Penguatan-Latar-Belakang-Bukti-Asumsi-Hipotesis.md` (26 KB) & `04-Literatur-Review/Matriks-Sintesis.md` (21 paper IEEE).

---

## ⏱️ Alokasi Waktu (dari Google Calendar)

| Blok | Agenda |
| :--- | :--- |
| Sen 16:30–18:30 | T-01 Latar Belakang |
| Sen 19:30–21:45 | T-01 lanjutan (research gap) |
| Sel 06:00–07:00 | NULIS & BACA |
| Sel 13:00–15:30 | T-02 Scope & Tujuan |
| Sel 16:30–18:30 | T-03 EDA part 1 |
| Sel 19:30–21:45 | T-03 EDA part 2 |
| Rab 06:00–07:00 | NULIS & BACA |
| Rab 10:00–11:00 | T-05 (mulai literatur) |
| Rab **14:00–15:30** | **Bimbingan 1 — Pak Hafiz** |

---

## 📝 Catatan Perkembangan Sprint
- **Dataset:** DEAM (1802 klip, 45 detik, anotasi 2 Hz).
- **Risiko:** EDA bisa melebar. Batasi: 1 tabel + 2 grafik, lalu **berhenti**.
- **Definition of done:** draft Bab 1 bisa dikirim ke pembimbing tanpa malu.
