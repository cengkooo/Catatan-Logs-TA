---
title: "Music Mood Detection Based on Audio and Lyrics with Deep Neural Net"
author: "Rémi Delbouys, Romain Hennequin, Jimena Royo-Letelier, et al."
year: 2018
citekey: "delbouys2018mood"
dataset: "DMDD (Deezer Mood Detection Dataset) - 18.644 lagu"
metode: "Multimodal Deep Neural Networks (CNN Mel-Spectrogram + Bi-LSTM Lyrics)"
tags:
  - literatur
  - paper-review
status: "read"
---

# 📖 Music Mood Detection Based on Audio and Lyrics with Deep Neural Net

- **Penulis:** `Rémi Delbouys, Romain Hennequin, Jimena Royo-Letelier, et al.` (2018)
- **Citekey LaTeX:** `\cite{delbouys2018mood}`
- **Dataset:** `DMDD (Deezer Mood Detection Dataset) - 18.644 lagu`
- **Metode Utama:** `Multimodal Deep Neural Networks (CNN Mel-Spectrogram + Bi-LSTM Lyrics)`

---

## 🎯 Masalah & Tujuan Riset
- **Permasalahan:** Deteksi mood musik berbasis audio tunggal sering kehilangan konteks semantik yang terdapat pada lirik, sementara analisis lirik saja mengabaikan dinamika melodi dan timbre.
- **Tujuan:** Membangun model deep learning multimodal terpadu yang memprediksi koordinat Valence dan Arousal dari kombinasi audio mel-spektrogram dan teks lirik.

---

## 🔬 Arsitektur & Metodologi
- **Representasi Emosi:** 2D Valence-Arousal regresi berbasis tag Last.fm yang dipetakan ke koordinat Warriner et al.
- **Algoritma / Pendekatan:** 2D Convolutional Neural Network (CNN) untuk fitur spektrogram audio dan Bidirectional LSTM / fastText untuk embedding teks lirik.
- **Metrik Evaluasi:** Mean Squared Error (MSE) dan $R^2$ score regresi Valence dan Arousal.

---

## 💡 Temuan Utama & Hasil
- Kombinasi multimodal mel-spectrogram dan lirik meningkatkan skor $R^2$ secara signifikan dibanding model unimodal, terutama untuk dimensi Valence.

---

## ⚠️ Limitasi & Gap Riset (Peluang untuk TA Kita)
> [!IMPORTANT]
> **Apa kelemahan paper ini yang diselesaikan oleh TA kita?**
- Anotasi emosi bersifat global dan statis per lagu (1 titik rata-rata), tidak merekam dinamika transisi emosi dalam lagu.

---

## 🔗 Relevansi dengan Tugas Akhir
- Menjelaskan sumber dataset DMDD yang digunakan oleh Gaur & Donnelly (2020), memperkuat argumentasi gap riset mengenai kelemahan representasi statis.
- Terkait dengan: [[Matriks-Sintesis]] | [[01-Dataset-DEAM-dan-Eksplorasi|Dataset-DEAM]] | [[Bab-2-Tinjauan-Pustaka]]
