---
title: "Feature Centric Based Deep Learning Approach for Music Mood Recognition with HuBERT Transformer Model"
author: "Yaoyu Sun"
year: 2025
citekey: "sun2025feature"
dataset: "DEAM & Emomusic"
metode: "HuBERT Transformer Architecture with Feature-Centric Fusion"
tags:
  - literatur
  - paper-review
status: "read"
---

# 📖 Feature Centric Based Deep Learning Approach for Music Mood Recognition with HuBERT Transformer Model

- **Penulis:** `Yaoyu Sun` (2025)
- **Citekey LaTeX:** `\cite{sun2025feature}`
- **Dataset:** `DEAM & Emomusic`
- **Metode Utama:** `HuBERT Transformer Architecture with Feature-Centric Fusion`

---

## 🎯 Masalah & Tujuan Riset
- **Permasalahan:** Model berbasis spectrogram konvensional gagal menangkap representasi representasi temporal frekuensi tinggi yang dibutuhkan untuk mengenali mood secara dinamis.
- **Tujuan:** Menerapkan model audio transformer HuBERT dengan rekayasa fitur berorientasi karakteristik musik untuk prediksi mood dinamis.

---

## 🔬 Arsitektur & Metodologi
- **Representasi Emosi:** 2D Valence-Arousal kontinu.
- **Algoritma / Pendekatan:** HuBERT pretrained audio encoder yang di-finetune dengan loss MSE dan korelasi CCC pada anotasi dinamis DEAM.
- **Metrik Evaluasi:** RMSE, Pearson r, dan Concordance Correlation Coefficient (CCC) pada dataset DEAM.

---

## 💡 Temuan Utama & Hasil
- Arsitektur HuBERT menghasilkan akurasi prediksi trajektori emosi tertinggi pada dataset DEAM dibandingkan model baseline CNN tradisional.

---

## ⚠️ Limitasi & Gap Riset (Peluang untuk TA Kita)
> [!IMPORTANT]
> **Apa kelemahan paper ini yang diselesaikan oleh TA kita?**
- Hanya berfokus pada evaluasi regresi model audio, tidak meneliti pembentukan playlist.

---

## 🔗 Relevansi dengan Tugas Akhir
- Menjadi bukti mutakhir (Nature Scientific Reports 2025) mengenai efektivitas dataset DEAM dalam mengekstraksi sinyal emosi dinamis.
- Terkait dengan: [[Matriks-Sintesis]] | [[Dataset-DEAM]] | [[Bab-2-Tinjauan-Pustaka]]
