---
title: "Developing a Benchmark for Emotional Analysis of Music"
author: "Anna Aljanaki, Yi-Hsuan Yang, Mohammad Soleymani"
year: 2017
citekey: "aljanaki2017developing"
dataset: "DEAM (Database for Emotion Analysis in Music) - 1.802 klip musik (45 detik)"
metode: "Continuous Dynamic Crowdsourcing Annotation (2 Hz) via MTurk"
tags:
  - literatur
  - paper-review
status: "read"
---

# 📖 Developing a Benchmark for Emotional Analysis of Music

- **Penulis:** `Anna Aljanaki, Yi-Hsuan Yang, Mohammad Soleymani` (2017)
- **Citekey LaTeX:** `\cite{aljanaki2017developing}`
- **Dataset:** `DEAM (Database for Emotion Analysis in Music) - 1.802 klip musik (45 detik)`
- **Metode Utama:** `Continuous Dynamic Crowdsourcing Annotation (2 Hz) via MTurk`

---

## 🎯 Masalah & Tujuan Riset
- **Permasalahan:** Ketiadaan dataset musik skala besar dengan anotasi emosi kontinu berfrekuensi tinggi yang terverifikasi dan bebas hak cipta menghambat kemajuan Music Emotion Recognition (MER) dinamis.
- **Tujuan:** Membangun benchmark komprehensif untuk analisis emosi musik dengan anotasi dimensi Valence dan Arousal secara kontinu setiap 0,5 detik.

---

## 🔬 Arsitektur & Metodologi
- **Representasi Emosi:** 2D Valence-Arousal kontinu (skala [-1, 1]) dengan frekuensi sampling 2 Hz (90 titik waktu per lagu 45 detik).
- **Algoritma / Pendekatan:** Pengumpulan data melalui antarmuka slider dinamis Amazon Mechanical Turk, agregasi inter-annotator agreement, dan baseline regresi akustik (SVR dan Random Forest).
- **Metrik Evaluasi:** Root Mean Squared Error (RMSE) dan Pearson's Correlation Coefficient (r) untuk prediksi Valence dan Arousal kontinu.

---

## 💡 Temuan Utama & Hasil
- DEAM menyediakan reliabilitas anotasi yang tinggi pada dimensi Arousal (korelasi > 0,6) dan mencatat variasi dinamis mood intra-lagu yang sangat kaya di seluruh korpus 1.802 klip.

---

## ⚠️ Limitasi & Gap Riset (Peluang untuk TA Kita)
> [!IMPORTANT]
> **Apa kelemahan paper ini yang diselesaikan oleh TA kita?**
- Hanya menyediakan dataset benchmark dan model prediksi emosi; tidak merancang algoritma rekomendasi playlist atau sequencing lagu.

---

## 🔗 Relevansi dengan Tugas Akhir
- Dataset utama yang digunakan pada Tugas Akhir ini untuk mengekstrak vektor mood trajectory dinamis per lagu.
- Terkait dengan: [[Matriks-Sintesis]] | [[01-Dataset-DEAM-dan-Eksplorasi|Dataset-DEAM]] | [[Bab-2-Tinjauan-Pustaka]]
