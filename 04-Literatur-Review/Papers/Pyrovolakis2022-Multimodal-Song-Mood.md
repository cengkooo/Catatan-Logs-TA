---
title: "Multi-Modal Song Mood Detection with Deep Learning"
author: "Konstantinos Pyrovolakis, Paraskevi Tzouveli, et al."
year: 2022
citekey: "pyrovolakis2022multimodal"
dataset: "Multimodal Song Dataset (Audio WAV + Teks Lirik)"
metode: "Hybrid CNN-BiLSTM with Cross-Modal Attention Mechanism"
tags:
  - literatur
  - paper-review
status: "read"
---

# 📖 Multi-Modal Song Mood Detection with Deep Learning

- **Penulis:** `Konstantinos Pyrovolakis, Paraskevi Tzouveli, et al.` (2022)
- **Citekey LaTeX:** `\cite{pyrovolakis2022multimodal}`
- **Dataset:** `Multimodal Song Dataset (Audio WAV + Teks Lirik)`
- **Metode Utama:** `Hybrid CNN-BiLSTM with Cross-Modal Attention Mechanism`

---

## 🎯 Masalah & Tujuan Riset
- **Permasalahan:** Interaksi modalitas suara dan lirik lagu bersifat non-linier dan kompleks sehingga fusi konvensional (concatenation) sering kehilangan korelasi silang.
- **Tujuan:** Mengembangkan jaringan multimodal dengan cross-attention untuk mendeteksi mood lagu secara lebih akurat.

---

## 🔬 Arsitektur & Metodologi
- **Representasi Emosi:** 4 Kuadran emosi Russell (Happy, Sad, Angry, Relaxed).
- **Algoritma / Pendekatan:** 1D/2D CNN untuk representasi audio, BiLSTM untuk representasi kata pada lirik, dan cross-modal attention layer.
- **Metrik Evaluasi:** F1-Score, Presisi, Recall, dan Akurasi klasifikasi 4 kuadran.

---

## 💡 Temuan Utama & Hasil
- Mekanisme attention antarmodalitas memberikan bobot lebih dinamis pada instrumen ketika lirik bersifat netral.

---

## ⚠️ Limitasi & Gap Riset (Peluang untuk TA Kita)
> [!IMPORTANT]
> **Apa kelemahan paper ini yang diselesaikan oleh TA kita?**
- Menggunakan kategorisasi kuadran diskrit statis per lagu, mengabaikan kurva gradien halus.

---

## 🔗 Relevansi dengan Tugas Akhir
- Bahan perbandingan di Bab 2 untuk menunjukkan keterbatasan klasifikasi kuadran diskrit dibanding pendekatan kontinu.
- Terkait dengan: [[Matriks-Sintesis]] | [[01-Dataset-DEAM-dan-Eksplorasi|Dataset-DEAM]] | [[Bab-2-Tinjauan-Pustaka]]
