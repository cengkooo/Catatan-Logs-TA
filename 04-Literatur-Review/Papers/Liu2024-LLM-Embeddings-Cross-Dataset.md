---
title: "Leveraging LLM Embeddings for Cross Dataset Label Alignment and Zero Shot Music Emotion Prediction"
author: "Renhang Liu, Abhinaba Roy, Dorien Herremans"
year: 2024
citekey: "liu2024leveraging"
dataset: "DEAM, PMEmo, Emomusic"
metode: "Large Language Model Text Embeddings for Zero-Shot Label Alignment"
tags:
  - literatur
  - paper-review
status: "read"
---

# 📖 Leveraging LLM Embeddings for Cross Dataset Label Alignment and Zero Shot Music Emotion Prediction

- **Penulis:** `Renhang Liu, Abhinaba Roy, Dorien Herremans` (2024)
- **Citekey LaTeX:** `\cite{liu2024leveraging}`
- **Dataset:** `DEAM, PMEmo, Emomusic`
- **Metode Utama:** `Large Language Model Text Embeddings for Zero-Shot Label Alignment`

---

## 🎯 Masalah & Tujuan Riset
- **Permasalahan:** Perbedaan skema pelabelan antar dataset emosi musik menghalangi transfer learning dan pemanfaatan korpus gabungan.
- **Tujuan:** Menggunakan semantic embedding dari LLM untuk menyelaraskan label emosi antar dataset dan melakukan prediksi zero-shot.

---

## 🔬 Arsitektur & Metodologi
- **Representasi Emosi:** Pemetaan semantik deskriptor emosi ke ruang koordinat Valence-Arousal kontinu.
- **Algoritma / Pendekatan:** Ekstraksi embedding teks prompt menggunakan LLM modern, dilanjutkan pemetaan proyeksi linier ke ruang afektif DEAM.
- **Metrik Evaluasi:** Zero-shot classification accuracy dan koefisien korelasi koordinat kontinu.

---

## 💡 Temuan Utama & Hasil
- Embedding LLM mampu menjembatani perbedaan istilah emosi antardataset secara akurat tanpa anotasi ulang manual.

---

## ⚠️ Limitasi & Gap Riset (Peluang untuk TA Kita)
> [!IMPORTANT]
> **Apa kelemahan paper ini yang diselesaikan oleh TA kita?**
- Hanya menyelaraskan label level dataset, bukan menangani urutan sekuensial playlist.

---

## 🔗 Relevansi dengan Tugas Akhir
- Memperkaya Bab 2 mengenai perkembangan mutakhir dalam harmonisasi representasi emosi musik.
- Terkait dengan: [[Matriks-Sintesis]] | [[01-Dataset-DEAM-dan-Eksplorasi|Dataset-DEAM]] | [[Bab-2-Tinjauan-Pustaka]]
