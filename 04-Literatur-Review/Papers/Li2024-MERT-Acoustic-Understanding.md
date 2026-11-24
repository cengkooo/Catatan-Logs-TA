---
title: "MERT: Acoustic Music Understanding Model with Large-Scale Self-Supervised Training"
author: "Yizhi Li, Ruibin Yuan, Ge Zhang, Yinghao Ma, et al."
year: 2024
citekey: "li2024mert"
dataset: "20.000 jam audio musik + Benchmark downstream (DEAM, MTG-Jamendo)"
metode: "Self-Supervised Acoustic Foundation Model (RVQ-VAE + Masked Spectrogram)"
tags:
  - literatur
  - paper-review
status: "read"
---

# 📖 MERT: Acoustic Music Understanding Model with Large-Scale Self-Supervised Training

- **Penulis:** `Yizhi Li, Ruibin Yuan, Ge Zhang, Yinghao Ma, et al.` (2024)
- **Citekey LaTeX:** `\cite{li2024mert}`
- **Dataset:** `20.000 jam audio musik + Benchmark downstream (DEAM, MTG-Jamendo)`
- **Metode Utama:** `Self-Supervised Acoustic Foundation Model (RVQ-VAE + Masked Spectrogram)`

---

## 🎯 Masalah & Tujuan Riset
- **Permasalahan:** Representasi fitur musik buatan tangan (handcrafted) atau model audio umum (seperti Wav2Vec) gagal menangkap karakteristik harmoni dan melodi tonal musik.
- **Tujuan:** Membangun foundation model akustik musik berskala besar (MERT) dengan pretraining self-supervised yang optimal untuk tugas-tugas MIR hilir.

---

## 🔬 Arsitektur & Metodologi
- **Representasi Emosi:** Prediksi Valence-Arousal pada dataset DEAM serta klasifikasi genre dan instrumen.
- **Algoritma / Pendekatan:** Transformer akustik dengan pemodelan diskrit Residual Vector Quantization (RVQ-VAE) dan masked language modeling pada fitur spektral musik.
- **Metrik Evaluasi:** Koefisien determinasi $R^2$ dan RMSE pada dataset DEAM (downstream emotion regression).

---

## 💡 Temuan Utama & Hasil
- MERT mencapai rekor performa state-of-the-art pada regresi emosi DEAM mengungguli model konvensional.

---

## ⚠️ Limitasi & Gap Riset (Peluang untuk TA Kita)
> [!IMPORTANT]
> **Apa kelemahan paper ini yang diselesaikan oleh TA kita?**
- Kompleksitas komputasi model sangat besar untuk deployment inferensi cepat pada playlist matching sekuensial.

---

## 🔗 Relevansi dengan Tugas Akhir
- Memvalidasi reliabilitas dataset DEAM sebagai standar emas pengujian representasi emosi akustik modern.
- Terkait dengan: [[Matriks-Sintesis]] | [[Dataset-DEAM]] | [[Bab-2-Tinjauan-Pustaka]]
