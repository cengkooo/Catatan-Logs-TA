---
title: "An Exploration of Mood Arc in Music Playlists"
author: "Manas Gaur & Austin Donnelly"
year: 2020
citekey: "gaur2020mood"
dataset: "Deezer Mood Detection Dataset (DMDD)"
metode: "2-Stage Pipeline: KNN + Acoustic Feature Filtering"
tags:
  - literatur
  - paper-review
status: "read"
---

# 📖 An Exploration of Mood Arc in Music Playlists

- **Penulis:** `Manas Gaur & Austin Donnelly` (2020)
- **Citekey LaTeX:** `\cite{gaur2020mood}`
- **Dataset:** `DMDD (Deezer Mood Detection Dataset) - 18.644 lagu`
- **Metode Utama:** `2-Stage Pipeline (KNN Retrieval + Acoustic Filtering)`

---

## 🎯 Masalah & Tujuan Riset
- **Permasalahan:** Layanan streaming kebanyakan menyusun playlist dengan mood seragam statis, padahal pengguna sering menginginkan transisi mood bertahap (*mood arc*).
- **Tujuan:** Merancang pipeline dua tahap untuk menghasilkan playlist dengan kurva mood yang mulus (*smooth*).

---

## 🔬 Arsitektur & Metodologi
1. **Tahap 1:** KNN mencari kandidat lagu di ruang 2D Valence-Arousal yang dekat dengan titik target kurva.
2. **Tahap 2:** Penyaringan kandidat menggunakan kemiripan fitur akustik (tempo, danceability, energy).
3. **Evaluasi:** Mengukur metrik *Smoothness* dan *Evenness*.

---

## ⚠️ Limitasi & Gap Riset (Peluang TA Kita)
> [!IMPORTANT]
> **Limitasi Mendasar:**
> Dataset DMDD hanya menyediakan label $V-A$ **statis (satu nilai rata-rata per lagu)** yang diambil dari tag Last.fm.
> Dua lagu dengan titik rata-rata sama bisa memiliki karakter yang sangat berbeda (satu lagu tenang lalu meledak berenergi, satu lagi konstan).
> **Solusi TA Kita:** Mengganti titik statis dengan anotasi dinamis dataset DEAM dan menambahkan kriteria *Trajectory Alignment*.
