---
title: "Music Emotion Recognition: The Role of Individuality"
author: "Yi-Hsuan Yang, Ya-Fan Su, Yu-Ching Lin, Homer H. Chen"
year: 2007
citekey: "yang2007music"
dataset: "Subjective Listening Experiment (koleksi musik populer)"
metode: "Support Vector Regression (SVR) Modeling Individual Perception Variance"
tags:
  - literatur
  - paper-review
status: "read"
---

# 📖 Music Emotion Recognition: The Role of Individuality

- **Penulis:** `Yi-Hsuan Yang, Ya-Fan Su, Yu-Ching Lin, Homer H. Chen` (2007)
- **Citekey LaTeX:** `\cite{yang2007music}`
- **Dataset:** `Subjective Listening Experiment (koleksi musik populer)`
- **Metode Utama:** `Support Vector Regression (SVR) Modeling Individual Perception Variance`

---

## 🎯 Masalah & Tujuan Riset
- **Permasalahan:** Persepsi emosi musik memiliki unsur subjektivitas yang tinggi antar individu sehingga model emosi umum sering dianggap tidak akurat oleh sebagian pendengar.
- **Tujuan:** Mempelajari sejauh mana variasi individual mempengaruhi persepsi emosi musik dan bagaimana memodelkannya secara komputasional.

---

## 🔬 Arsitektur & Metodologi
- **Representasi Emosi:** Ruang 2D Valence-Arousal Thayer.
- **Algoritma / Pendekatan:** SVR personalisasi yang menggabungkan model emosi konsensus umum dengan bobot profil preferensi pendengar individual.
- **Metrik Evaluasi:** $R^2$ score dan korelasi antara prediksi model personal vs persepsi aktual subjek.

---

## 💡 Temuan Utama & Hasil
- Meskipun ada variasi subjektif pada Valence, respons Arousal dan gradien perubahan mood memiliki konsensus tinggi antar pendengar.

---

## ⚠️ Limitasi & Gap Riset (Peluang untuk TA Kita)
> [!IMPORTANT]
> **Apa kelemahan paper ini yang diselesaikan oleh TA kita?**
- Ukuran sampel subjek terbatas pada eksperimen laboratorium kecil.

---

## 🔗 Relevansi dengan Tugas Akhir
- Membenarkan penggunaan nilai rata-rata agregat dari dataset DEAM karena tren trajektori makro terbukti memiliki konsensus tinggi.
- Terkait dengan: [[Matriks-Sintesis]] | [[01-Dataset-DEAM-dan-Eksplorasi|Dataset-DEAM]] | [[Bab-2-Tinjauan-Pustaka]]
