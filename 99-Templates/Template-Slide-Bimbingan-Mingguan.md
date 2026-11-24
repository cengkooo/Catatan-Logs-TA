---
title: "Template Naskah Slide Bimbingan Mingguan"
tags:
  - template
  - bimbingan
  - slides
  - typst
  - progres
---

# 📅 Outline Slide Bimbingan Mingguan #{{minggu}}

> **Tanggal Pembuatan:** {{date}}  
> **Jadwal Bimbingan:** {{meeting_date}}  
> **Dosen Pembimbing:** Nama Dosen Pembimbing, S.Kom., M.T.  
> **Lokasi File Typst:** `Slides/02-Progress/{{folder_minggu}}/progres_m{{minggu}}.typ`  
> **PDF Terkompilasi:** `Slides/02-Progress/{{folder_minggu}}/progres_m{{minggu}}.pdf`  

---

## 🎯 1. Matriks Status Progres (Target vs Realisasi)

| Kategori | Butir Capaian / Pekerjaan | Status | Catatan / Bukti |
| :--- | :--- | :---: | :--- |
| **Selesai (*Done*)** | 1. Replikasi modul KD-Tree | 🟢 | `stage1_knn.py:54` |
| | 2. Ekstraksi 15 fitur akustik DEAM | 🟢 | `deam_extractor.py` |
| **Berjalan (*In Progress*)** | 1. Batch traversal kuadran | 🟡 | `run_quadrant_experiments.py` |
| **Terkendala (*Blocked*)** | 1. Lompatan emosi intralagu pada baseline statis | 🔴 | Butuh arahan solusi smoothing |

---

## 🔬 2. Bukti Teknis & Temuan Eksperimen (*Deep Dive*)

- **Plot Grafik yang Ditampilkan:** `Slides/assets/experiments/{{nama_plot.png}}`
- **Script Pembangkit Plot:** `EXPERIMENT/Code/baseline_gaur/experiments/run_quadrant_experiments.py`
- **Catatan Analisis:**
  - [Tuliskan apa temuan utama dari grafik].
  - [Apa arti temuan ini terhadap gap penelitian di Bab I & II].

---

## 💡 3. Konsultasi Kendala & Usulan Solusi (Diskusi Bimbingan)

- **Masalah Teknis yang Dihadapi:**
  - [Jelaskan kendala secara konkret].
- **Opsi Solusi Mandiri yang Diajukan ke Dosen:**
  - **Opsi A:** [Deskripsi + argumen teknis].
  - **Opsi B:** [Deskripsi + konsekuensi komputasi].
- **Keputusan / Arahan Dosen (Diisi saat sesi bimbingan):**
  - _[Catat di sini dan salin ke [[03-Bimbingan/Notulensi-Bimbingan]]]_

---

## 🚀 4. Rencana Kerja Pekan Depan (*Next Week Action Items*)

1. [ ] [Target 1 - Teknis Kode]
2. [ ] [Target 2 - Eksperimen & Metrik]
3. [ ] [Target 3 - Naskah Proposal/Skripsi]
- **Target Tanggal Bimbingan Berikutnya:** `YYYY-MM-DD`
