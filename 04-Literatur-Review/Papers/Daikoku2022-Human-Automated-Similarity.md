---
title: "Agreement Among Human and Automated Estimates of Similarity in a Global Music Sample"
author: "Hideo Daikoku, Shenghao Ding, Emmanouil Benetos, et al."
year: 2022
citekey: "daikoku2022agreement"
dataset: "Global Music Sample (koleksi musik lintas budaya dunia)"
metode: "Empirical Perceptual Evaluation vs Algorithmic MIR Distances"
tags:
  - literatur
  - paper-review
status: "read"
---

# 📖 Agreement Among Human and Automated Estimates of Similarity in a Global Music Sample

- **Penulis:** `Hideo Daikoku, Shenghao Ding, Emmanouil Benetos, et al.` (2022)
- **Citekey LaTeX:** `\cite{daikoku2022agreement}`
- **Dataset:** `Global Music Sample (koleksi musik lintas budaya dunia)`
- **Metode Utama:** `Empirical Perceptual Evaluation vs Algorithmic MIR Distances`

---

## 🎯 Masalah & Tujuan Riset
- **Permasalahan:** Sering terjadi diskrepansi antara metrik jarak algoritmik MIR dengan persepsi keselarasan lagu menurut pendengar manusia.
- **Tujuan:** Mengukur derajat kesepakatan (agreement) antara penilaian kemiripan oleh manusia dan metrik kemiripan otomatis MIR.

---

## 🔬 Arsitektur & Metodologi
- **Representasi Emosi:** Persepsi kemiripan afektif, ritmis, dan melodis.
- **Algoritma / Pendekatan:** Analisis korelasi Spearman antara jarak Euclidean/Cosinus fitur MFCC, Chroma, Rhythm dan penilaian subjektif manusia.
- **Metrik Evaluasi:** Inter-rater reliability (Krippendorff's alpha) dan korelasi peringkat Spearman.

---

## 💡 Temuan Utama & Hasil
- Metrik otomatis sangat konsisten pada ritme dan tempo, namun rentan bias pada transisi mood afektif.

---

## ⚠️ Limitasi & Gap Riset (Peluang untuk TA Kita)
> [!IMPORTANT]
> **Apa kelemahan paper ini yang diselesaikan oleh TA kita?**
- Studi evaluasi persepsi murni, tidak membangun model playlist.

---

## 🔗 Relevansi dengan Tugas Akhir
- Memperkuat urgensi metrik Smoothness dan Evenness sebagai representasi matematis dari persepsi transisi pendengar.
- Terkait dengan: [[Matriks-Sintesis]] | [[Dataset-DEAM]] | [[Bab-2-Tinjauan-Pustaka]]
