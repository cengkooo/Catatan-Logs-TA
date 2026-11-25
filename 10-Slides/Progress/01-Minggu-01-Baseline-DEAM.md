---
title: "Outline Slide Bimbingan Mingguan #01: Replikasi Baseline Gaur & Eksplorasi DEAM"
tags:
  - bimbingan
  - slides
  - typst
  - progres
  - minggu-01
---

# Outline Slide Bimbingan Mingguan #01

> **Tanggal Pembuatan:** 20 November 2026  
> **Jadwal Bimbingan:** 21 November 2026  
> **Dosen Pembimbing:** Hafiz Budi Firmansyah, S.Kom., M.Sc.  
> **Lokasi File Typst:** [`Slides/02-Progress/01-Minggu-01-Baseline-DEAM/progres_m01.typ`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Slides/02-Progress/01-Minggu-01-Baseline-DEAM/progres_m01.typ)  
> **PDF Terkompilasi:** [`Slides/02-Progress/01-Minggu-01-Baseline-DEAM/progres_m01.pdf`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Slides/02-Progress/01-Minggu-01-Baseline-DEAM/progres_m01.pdf)

---

## 1. Matriks Status Progres (Target vs Realisasi)

| Kategori | Butir Capaian / Pekerjaan | Status | Catatan / Bukti |
| :--- | :--- | :---: | :--- |
| **Tercapai (Done)** | 1. Replikasi pipeline KD-Tree $k$-NN pada dataset DEAM (1.802 klip lagu) | Selesai | `EXPERIMENT/Code/baseline_gaur/src/stage1_knn.py` |
| | 2. Ekstraksi 15 fitur audio via Librosa | Selesai | `deam_extractor.py` |
| | 3. Penyusunan draf Bab I dan Bab II di Obsidian | Selesai | [[06-Naskah-Draft/]] |
| **Sedang Berjalan (In Progress)** | 1. Benchmarking 4 kuadran (Smoothness PCC & Evenness RMSE) | Berjalan | `run_quadrant_experiments.py` |
| | 2. Finalisasi diagram pipeline metodologi 2 tahap di Bab III | Berjalan | Draf Bab III |
| **Temuan Kunci / Kendala (Blocked)** | 1. Titik tengah statis Gaur tidak mencerminkan emosi dinamis per detik lagu | Diskusi | Butuh justifikasi batas transisi kontinu |

---

## 2. Bukti Teknis & Temuan Eksperimen (Deep Dive)

- **Plot Grafik yang Ditampilkan:** [`Slides/assets/experiments/baseline_deam_traversal_plot.png`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Slides/assets/experiments/baseline_deam_traversal_plot.png)
- **Script Pembangkit Plot:** `EXPERIMENT/Code/baseline_gaur/experiments/run_quadrant_experiments.py`
- **Catatan Analisis:**
  - Pipeline berhasil memetakan titik lagu pada ruang Valence-Arousal ($V-A$).
  - Pada plot traversal, garis oranye merepresentasikan kueri alur dan titik biru menunjukkan lagu terpilih; titik lagu masih melompat jauh dari garis ideal di area kuadran berdensitas rendah.
  - Solusi yang diusulkan adalah *continuous trajectory alignment* untuk meminimalkan lompatan transisi antar-ujung lagu.

---

## 3. Konsultasi Kendala & Usulan Solusi (Diskusi Bimbingan)

- **Masalah Teknis yang Dihadapi:**
  - Anotasi DEAM berdurasi 45 detik dengan sampling 2 Hz (90 time-steps). Perlu dipastikan apakah sampling 2 Hz sudah memadai atau memerlukan teknik *smoothing* tambahan.
- **Opsi Solusi yang Diajukan ke Dosen:**
  - **Opsi A:** Menggunakan *moving average window* 1 detik (2 titik data).
  - **Opsi B:** Menggunakan *cubic spline interpolation* kontinu.
- **Keputusan / Arahan Dosen:**
  - _[Belum tercatat di file ini; lihat [[03-Bimbingan/01-Notulensi-Bimbingan]] untuk pembaruan notulensi]_

---

## 4. Rencana Kerja Pekan Depan (Next Week Action Items)

1. [ ] **Modul Trajectory:** Membuat fungsi kalkulasi jarak transisi ujung lagu $d(t_{\text{end}}^i, t_{\text{start}}^{i+1})$.
2. [ ] **Benchmarking:** Menuntaskan tabel perbandingan *Smoothness* dan *Evenness* antara baseline dan metode usulan.
3. [ ] **Naskah TA:** Menuntaskan draf Bab III Metodologi.
- **Target Tanggal Bimbingan Berikutnya:** `2026-11-27` (Kamis, Tentatif)
