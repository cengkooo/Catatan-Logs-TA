---
title: "FMA: A Dataset for Music Analysis"
author: "Michaël Defferrard, Kirell Benzi, Pierre Vandergheynst, Xavier Bresson"
year: 2017
citekey: "defferrard2017fma"
dataset: "Free Music Archive (FMA) - 106.574 trek musik"
metode: "Open Large-Scale Music Information Retrieval Benchmark"
tags:
  - literatur
  - paper-review
status: "read"
---

# 📖 FMA: A Dataset for Music Analysis

- **Penulis:** `Michaël Defferrard, Kirell Benzi, Pierre Vandergheynst, Xavier Bresson` (2017)
- **Citekey LaTeX:** `\cite{defferrard2017fma}`
- **Dataset:** `Free Music Archive (FMA) - 106.574 trek musik`
- **Metode Utama:** `Open Large-Scale Music Information Retrieval Benchmark`

---

## 🎯 Masalah & Tujuan Riset
- **Permasalahan:** Dataset musik publik sering terbentur batasan hak cipta sehingga hanya menyediakan audio klip beberapa detik atau fitur terkomputasi saja tanpa audio mentah.
- **Tujuan:** Menyediakan dataset musik skala raksasa yang legal, berkualitas tinggi, dan disertai fitur audio lengkap untuk riset MIR.

---

## 🔬 Arsitektur & Metodologi
- **Representasi Emosi:** Metadata genre, artis, dan fitur audio librosa (MFCC, Spectral, Chroma).
- **Algoritma / Pendekatan:** Standardisasi ekstraksi fitur spektral audio dan penyusunan partisi data hierarkis (FMA small, medium, large, full).
- **Metrik Evaluasi:** Baseline klasifikasi genre dengan berbagai model machine learning (SVM, kNN, CNN).

---

## 💡 Temuan Utama & Hasil
- Menjadi dataset standar terbuka nomor satu untuk benchmarking algoritma audio musik di dunia MIR.

---

## ⚠️ Limitasi & Gap Riset (Peluang untuk TA Kita)
> [!IMPORTANT]
> **Apa kelemahan paper ini yang diselesaikan oleh TA kita?**
- FMA berfokus pada hierarki genre dan metadata umum, tidak memiliki anotasi kontinu Valence-Arousal per 0,5 detik seperti DEAM.

---

## 🔗 Relevansi dengan Tugas Akhir
- Sebagai literatur perbandingan dataset pada Bab 3 untuk memperjelas alasan pemilihan DEAM dibanding FMA.
- Terkait dengan: [[Matriks-Sintesis]] | [[Dataset-DEAM]] | [[Bab-2-Tinjauan-Pustaka]]
