---
title: "Staging Materi Naskah Proposal ke Slide Bimbingan #01 (Edisi Perdana)"
tags:
  - slides
  - progress
  - staging
  - latex-ssot
  - typst
date: 2026-11-25
---

# Staging Materi: `proposal-penelitian-andryano-123140205/chapters/` ke Slide Bimbingan #01

> **Acuan Utama (SSOT):** [`proposal-penelitian-andryano-123140205/chapters/`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/proposal-penelitian-andryano-123140205/chapters/) (`chapter-1.tex` s.d. `chapter-3.tex`)  
> **Referensi Sekunder:** [[06-Naskah-Draft/README]]  
> **Target Slide Typst:** [`Slides/02-Progress/01-Minggu-01-Baseline-DEAM/progres_m01.typ`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Slides/02-Progress/01-Minggu-01-Baseline-DEAM/progres_m01.typ) (Pembaruan Edisi Perdana untuk Presentasi ke Pak Hafiz)

---

## Pemetaan Materi per Slide (Target 5 Slide Padat)

### Slide 1: Cover & Fokus Pertemuan Bimbingan #01
- **Komponen Typst:** `#cover-slide(...)`
- **Judul:** Validasi Proposal Bab I sampai Bab III & Replikasi Awal Baseline DEAM
- **Subjudul:** Laporan Progres Bimbingan Tugas Akhir (Pertemuan #01)
- **Identitas:** Andryano Kadarisman (`123140205`), Pembimbing: Hafiz Budi Firmansyah, S.Kom., M.Sc.

---

### Slide 2: Matriks Status Progres (Bab I–III & Eksperimen Awal)
- **Komponen Typst:** `#slide-header(...)` + 3 `#card-box(...)` (`DONE`, `IN_PROGRESS`, `BLOCKED`) + `#memory-recall(...)`
- **Isi Kartu Tercapai (`DONE`):**
  - Replikasi baseline Gaur (2020/2024) pada 1.802 klip DEAM dan 540 *batch run* selesai (Tabel 3.1 pada `chapter-3.tex`).
  - Naskah LaTeX Bab I sampai Bab III (`chapter-1.tex` s.d. `chapter-3.tex`) selesai disusun dengan kerangka *Dual Evaluation*.
  - Penguatan literatur 2022–2025: Belaref et al. (2024), Wang et al. (2024 REMAST), Daikoku et al. (2022), Schweiger et al. (2025).
- **Isi Kartu Berjalan (`IN_PROGRESS`):**
  - Penyusunan slide Seminar Proposal 10 menit (14 slide) di `Slides/01-Sempro/sempro_slides.typ`.
  - Pemeriksaan akhir format UNESCO dan daftar pustaka `thesis.tex`.
- **Isi Kartu Butuh Arahan (`BLOCKED`):**
  - Persetujuan final kerangka *Dual Evaluation* (objektif + *Blind A/B Listening Test* $N \ge 30$) sebelum pendaftaran Sempro.

---

### Slide 3: Bukti Empiris Replikasi Baseline pada DEAM
- **Komponen Typst:** `#slide-header(...)` + `#grid(columns: (1.15fr, 1fr))` berisi `#image(...)` dan ringkasan Tabel 3.1
- **Aset Visual:** [`Slides/assets/experiments/baseline_deam_traversal_plot.png`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Slides/assets/experiments/baseline_deam_traversal_plot.png)
- **Data Tabel 3.1 (`chapter-3.tex:171-177`):**
  - Cosine: Linearity PCC `0,9781` | Evenness V-A `0,000349` | Langkah Audio `0,3506`
  - Euclidean: Linearity PCC `0,9876` | Evenness V-A `0,000238` | Langkah Audio `0,3106`
  - Manhattan: Linearity PCC `0,9762` | Evenness V-A `0,000290` | Langkah Audio `0,2895`
- **Temuan Kritis (`chapter-1.tex:15-17`):**
  - 98,11% klip DEAM mengalami pergeseran emosi internal ($\Delta = 0,1937$, rentang dinamis $0,5950$).
  - PCC tinggi ($> 0,97$) adalah artefak rute diagonal buatan (Q3 ke Q1); pada rute lintas kuadran (Q1 ke Q2/Q4) turun ke `0,6628` sampai `0,7189`.

---

### Slide 4: Arsitektur Pipeline 2-Tahap & Kerangka Evaluasi Ganda
- **Komponen Typst:** `#slide-header(...)` + 2 `#card-box(...)` sejajar (Kiri: Model Komputasional, Kanan: Evaluasi Ganda)
- **Kolom Kiri — Pipeline 2-Tahap (`chapter-3.tex` Subbab 3.3 & 3.5):**
  - Tahap 1: *KNN Candidate Retrieval* pada ruang $V-A$ di sekitar *waypoint*.
  - Tahap 2: *Dynamic Mood Trajectory Alignment* dengan penalti *Boundary Jump Cost* ($\mathcal{BJC}$).
  - Metrik objektif: *Boundary Smoothness* ($\mathcal{S}$, target turun $\ge 15\%$), *Evenness Index* ($\mathcal{E}$), dan $\mathcal{CBJC}$ pada 540 *batch run* + uji Wilcoxon ($p < 0,05$).
- **Kolom Kanan — Protokol User Listening Study (`chapter-3.tex` Subbab 3.6):**
  - *Blind A/B Listening Test* terhadap minimal $N = 30$ responden.
  - Stimulus sambungan transisi berdurasi 30 detik; skala Likert 5 poin (*perceived smoothness*, *acoustic continuity*, *emotional naturalness*).
  - Validasi reliabilitas *Cronbach's Alpha* ($\ge 0,70$) dan korelasi peringkat Spearman terhadap metrik objektif.

---

### Slide 5: Poin Keputusan Pembimbing & Rencana Pekan Depan
- **Komponen Typst:** `#slide-header(...)` + 2 `#card-box(...)` (Kiri: Poin Keputusan, Kanan: Action Items) + `#memory-recall(...)`
- **Poin Keputusan yang Diajukan ke Pak Hafiz:**
  1. Validasi 3 Rumusan Masalah & 3 Tujuan Penelitian pada `chapter-1.tex` (menggabungkan evaluasi komputasional dan *User Study*).
  2. Persetujuan protokol *User Listening Study* ($N \ge 30$, dieksekusi penuh pada TA 2).
  3. Kelayakan naskah `proposal-penelitian-andryano-123140205/thesis.pdf` untuk lanjut ke Seminar Proposal.
- **Rencana Kerja Setelah Bimbingan:**
  1. Finalisasi slide Sempro 14 halaman (`Slides/01-Sempro/sempro_slides.typ`) dengan target durasi 9 menit 30 detik.
  2. Revisi naskah LaTeX berdasarkan masukan Pak Hafiz.
  3. Pendaftaran Seminar Proposal sesuai syarat pada [[03-Bimbingan/03-Tracker-Prasyarat-Sempro]].
