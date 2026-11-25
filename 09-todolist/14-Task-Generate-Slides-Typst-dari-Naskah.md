---
title: "Todolist Coding Typst: Generate Slide Progres Bimbingan #01 (Edisi Perdana)"
tags:
  - todolist
  - typst
  - slides
  - progress
  - coding
status: "READY FOR EXECUTION"
target_output: "Slides/02-Progress/01-Minggu-01-Baseline-DEAM/progres_m01.pdf (5 Slide)"
ssot_source: "proposal-penelitian-andryano-123140205/chapters/"
staging_note: "10-Slides/Progress/03-Staging-Materi-Naskah-ke-Slides.md"
---

# Todolist Coding Typst: Generate Slide Progres Bimbingan #01

> **Tujuan:** Memutakhirkan berkas [`Slides/02-Progress/01-Minggu-01-Baseline-DEAM/progres_m01.typ`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Slides/02-Progress/01-Minggu-01-Baseline-DEAM/progres_m01.typ) sebagai dek Bimbingan Perdana (`#01`) menggunakan materi terkurasi di [[10-Slides/Progress/03-Staging-Materi-Naskah-ke-Slides]] yang bersumber dari [`proposal-penelitian-andryano-123140205/chapters/`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/proposal-penelitian-andryano-123140205/chapters/).

---

## Tahap 1: Sinkronisasi Aset & Verifikasi Tema

- [ ] Jalankan skrip sinkronisasi aset eksperimen agar grafik terbaru tersedia di `Slides/assets/experiments/`:
  ```powershell
  powershell -File "Slides\scripts\sync_experiment_assets.ps1"
  ```
- [ ] Verifikasi keberadaan berkas gambar `Slides/assets/experiments/baseline_deam_traversal_plot.png`.
- [ ] Periksa fungsi komponen yang tersedia di [`Slides/templates/itera_theme.typ`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Slides/templates/itera_theme.typ) (`#cover-slide`, `#slide-header`, `#card-box`, `#status-badge`, `#memory-recall`).

---

## Tahap 2: Pemutakhiran Kode Typst `progres_m01.typ` (5 Slide)

- [ ] **Slide 1 (`#cover-slide`):** Perbarui judul menjadi *Validasi Proposal Bab I–III & Replikasi Awal Baseline DEAM*, perbarui `created-date` dan `meeting-date` sesuai jadwal bimbingan aktual, serta pastikan nama pembimbing (`Hafiz Budi Firmansyah, S.Kom., M.Sc.`) dan NIM (`123140205`) benar.
- [ ] **Slide 2 (Matriks Status Progres):** Isi 3 `#card-box` (`DONE`, `IN_PROGRESS`, `BLOCKED`) sesuai bagian Slide 2 pada [[10-Slides/Progress/03-Staging-Materi-Naskah-ke-Slides]]:
  - `DONE`: replikasi 1.802 klip DEAM / 540 *batch run* (Tabel 3.1), penyusunan `chapter-1.tex` s.d. `chapter-3.tex` (*Dual Evaluation*), dan revalidasi literatur 2022–2025.
  - `IN_PROGRESS`: finalisasi slide Sempro (`sempro_slides.typ`) dan pengecekan akhir `thesis.tex`.
  - `BLOCKED`: persetujuan kerangka *Dual Evaluation* sebelum pendaftaran Sempro.
- [ ] **Slide 3 (Bukti Empiris DEAM & Tabel 3.1):** Pertahankan `#image("/assets/experiments/baseline_deam_traversal_plot.png")` di kolom kiri, lalu ganti/lengkapi kolom kanan dengan angka Tabel 3.1 (`Cosine 0,9781`, `Euclidean 0,9876`, `Manhattan 0,9762`), temuan 98,11% pergeseran internal DEAM ($\Delta = 0,1937$), dan penurunan korelasi rute lintas kuadran (`0,6628`–`0,7189`).
- [ ] **Slide 4 (Arsitektur 2-Tahap & Evaluasi Ganda):** Buat slide baru dengan 2 `#card-box` sejajar untuk merangkum:
  - Kiri: Pipeline 2-tahap (KNN + *Dynamic Trajectory Alignment* + $\mathcal{BJC}$), metrik $\mathcal{S}$, $\mathcal{E}$, $\mathcal{CBJC}$, 540 *batch run*, uji Wilcoxon ($p < 0,05$).
  - Kanan: Protokol *Blind A/B Listening Test* ($N \ge 30$, klip 30 detik, Likert 5 poin, *Cronbach's Alpha* $\ge 0,70$, korelasi Spearman).
- [ ] **Slide 5 (Poin Keputusan & Rencana Pekan Depan):** Perbarui slide penutup menjadi daftar 3 keputusan yang dimintakan persetujuan Pak Hafiz dan 3 *action items* menuju pendaftaran Sempro.

---

## Tahap 3: Kompilasi & Audit Visual PDF

- [ ] Jalankan kompilasi Typst dari root `Slides` (atau pakai `.\run_watch.ps1 -Target 01`):
  ```powershell
  & "D:\Typst\typst-x86_64-pc-windows-msvc\typst.exe" compile --root "Slides" "Slides\02-Progress\01-Minggu-01-Baseline-DEAM\progres_m01.typ" "Slides\02-Progress\01-Minggu-01-Baseline-DEAM\progres_m01.pdf"
  ```
- [ ] Pastikan kompilasi selesai dengan *exit code 0* tanpa error maupun warning font/asset.
- [ ] Buka `progres_m01.pdf` dan pastikan jumlah halaman tepat **5 halaman** (tidak ada elemen kartu atau `#memory-recall` yang meluber ke halaman ke-6).
- [ ] Pastikan seluruh angka di slide cocok dengan `proposal-penelitian-andryano-123140205/chapters/chapter-1.tex` dan `chapter-3.tex`.

---

## Tahap 4: Tindak Lanjut ke Slide Sempro (Opsional Setelah Bimbingan)

- [ ] Setelah mendapat persetujuan Pak Hafiz pada sesi Bimbingan #01, catat keputusan di [[03-Bimbingan/01-Notulensi-Bimbingan]].
- [ ] Terapkan revisi (jika ada) ke `proposal-penelitian-andryano-123140205/chapters/`, lalu sinkronkan ke [`Slides/01-Sempro/sempro_slides.typ`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Slides/01-Sempro/sempro_slides.typ).
