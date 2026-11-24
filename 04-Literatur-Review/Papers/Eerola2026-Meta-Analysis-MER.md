---
title: "A Meta-Analysis of Music Emotion Recognition Studies"
author: "Tuomas Eerola, Cameron J. Anderson"
year: 2026
citekey: "eerola2026metaanalysis"
dataset: "Meta-analisis 144 studi empiris MER (2000–2025)"
metode: "Systematic Quantitative Meta-Analysis & Random-Effects Modeling"
tags:
  - literatur
  - paper-review
status: "read"
---

# 📖 A Meta-Analysis of Music Emotion Recognition Studies

- **Penulis:** `Tuomas Eerola, Cameron J. Anderson` (2026)
- **Citekey LaTeX:** `\cite{eerola2026metaanalysis}`
- **Dataset:** `Meta-analisis 144 studi empiris MER (2000–2025)`
- **Metode Utama:** `Systematic Quantitative Meta-Analysis & Random-Effects Modeling`

---

## 🎯 Masalah & Tujuan Riset
- **Permasalahan:** Terdapat heterogenitas tinggi dalam metodologi, dataset, fitur akustik, dan performa model MER di literatur yang menyulitkan perbandingan objektif.
- **Tujuan:** Melakukan sintesis meta-analisis kuantitatif komprehensif terhadap 144 studi MER untuk mengidentifikasi faktor penentu akurasi prediksi emosi musik.

---

## 🔬 Arsitektur & Metodologi
- **Representasi Emosi:** Perbandingan dimensional (Valence-Arousal) vs kategori diskrit, baik statis maupun dinamis kontinu.
- **Algoritma / Pendekatan:** Model random-effects, meta-regresi untuk pengaruh arsitektur model (CNN, Transformer, RNN), fitur akustik, dan karakteristik dataset.
- **Metrik Evaluasi:** Ukuran efek korelasi gabungan (pooled correlation coefficient r) dan persentase varians dijelaskan ($R^2$).

---

## 💡 Temuan Utama & Hasil
- Arousal secara konsisten jauh lebih mudah diprediksi ($r pprox 0,78$) dibanding Valence ($r pprox 0,55$). Model dinamis kontinu memerlukan filter peredam bising perception latency.

---

## ⚠️ Limitasi & Gap Riset (Peluang untuk TA Kita)
> [!IMPORTANT]
> **Apa kelemahan paper ini yang diselesaikan oleh TA kita?**
- Fokus pada survei dan analisis literatur, bukan pembuatan algoritma sequencing playlist.

---

## 🔗 Relevansi dengan Tugas Akhir
- Menjadi rujukan primer terkini (2026) untuk justifikasi pemisahan perlakuan dimensi Valence dan Arousal serta kebutuhan trajectory filtering.
- Terkait dengan: [[Matriks-Sintesis]] | [[Dataset-DEAM]] | [[Bab-2-Tinjauan-Pustaka]]
