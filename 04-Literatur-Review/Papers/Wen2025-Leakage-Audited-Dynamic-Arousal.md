---
title: "Known Music, Unknown Response: Leakage-Audited Dynamic Arousal Forecasting With Scheduled Future Music"
author: "Bin Wen, Dai-Qiao Zhang, Tien-Ping Tan"
year: 2025
citekey: "wen2025leakage"
dataset: "DEAM & PMEmo (Continuous Dynamic Annotations)"
metode: "Leakage-Audited Autoregressive Dynamic Emotion Forecasting"
tags:
  - literatur
  - paper-review
status: "read"
---

# 📖 Known Music, Unknown Response: Leakage-Audited Dynamic Arousal Forecasting With Scheduled Future Music

- **Penulis:** `Bin Wen, Dai-Qiao Zhang, Tien-Ping Tan` (2025)
- **Citekey LaTeX:** `\cite{wen2025leakage}`
- **Dataset:** `DEAM & PMEmo (Continuous Dynamic Annotations)`
- **Metode Utama:** `Leakage-Audited Autoregressive Dynamic Emotion Forecasting`

---

## 🎯 Masalah & Tujuan Riset
- **Permasalahan:** Banyak model peramalan emosi dinamis mengalami 'data leakage' karena menggunakan fitur masa depan yang belum terdengar untuk memprediksi respons emosional pendengar saat ini.
- **Tujuan:** Merancang arsitektur peramalan Arousal dinamis yang diaudit bebas dari kebocoran temporal masa depan dengan memanfaatkan scheduled future context.

---

## 🔬 Arsitektur & Metodologi
- **Representasi Emosi:** Continuous Dynamic Arousal time-series (frekuensi 2 Hz).
- **Algoritma / Pendekatan:** Encoder-decoder berbasis Transformer dan GRU dengan masked causal attention untuk mencegah kebocoran temporal.
- **Metrik Evaluasi:** Concordance Correlation Coefficient (CCC) dan RMSE peramalan dinamis kontinu.

---

## 💡 Temuan Utama & Hasil
- Respons arousal pendengar memiliki inersia temporal (kelambatan ~1-2 detik); audit kebocoran data terbukti krusial untuk evaluasi valid.

---

## ⚠️ Limitasi & Gap Riset (Peluang untuk TA Kita)
> [!IMPORTANT]
> **Apa kelemahan paper ini yang diselesaikan oleh TA kita?**
- Hanya meneliti dimensi Arousal pada klip tunggal, belum mengintegrasikan sequencing antarlagu dalam playlist.

---

## 🔗 Relevansi dengan Tugas Akhir
- Rujukan penting terkait pemrosesan deret waktu kontinu DEAM dan pertimbangan window pergeseran waktu emosi.
- Terkait dengan: [[Matriks-Sintesis]] | [[01-Dataset-DEAM-dan-Eksplorasi|Dataset-DEAM]] | [[Bab-2-Tinjauan-Pustaka]]
