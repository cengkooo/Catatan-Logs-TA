---
title: "Musical Audio Similarity with Self-supervised Convolutional Neural Networks"
author: "Carl Thomé, Sebastian Piwell, Oscar Utterbäck"
year: 2022
citekey: "thome2022musical"
dataset: "Large-Scale Unlabeled Music Audio"
metode: "Self-Supervised Contrastive CNNs for Audio Similarity"
tags:
  - literatur
  - paper-review
status: "read"
---

# 📖 Musical Audio Similarity with Self-supervised Convolutional Neural Networks

- **Penulis:** `Carl Thomé, Sebastian Piwell, Oscar Utterbäck` (2022)
- **Citekey LaTeX:** `\cite{thome2022musical}`
- **Dataset:** `Large-Scale Unlabeled Music Audio`
- **Metode Utama:** `Self-Supervised Contrastive CNNs for Audio Similarity`

---

## 🎯 Masalah & Tujuan Riset
- **Permasalahan:** Pengukuran kemiripan audio musik membutuhkan data teranotasi masif yang mahal untuk diperoleh secara manual.
- **Tujuan:** Membangun model representasi kemiripan audio musik tanpa supervisi (self-supervised) berbasis augmentasi sinyal suara.

---

## 🔬 Arsitektur & Metodologi
- **Representasi Emosi:** Karakteristik akustik umum (timbre, tempo, harmoni).
- **Algoritma / Pendekatan:** SimCLR contrastive framework pada spektrogram audio musik dengan augmentasi pitch shifting dan time masking.
- **Metrik Evaluasi:** Normalized Discounted Cumulative Gain (NDCG) dan korelasi dengan penilaian kemiripan manusia.

---

## 💡 Temuan Utama & Hasil
- Embedding tanpa supervisi mampu mengelompokkan trek musik dengan karakteristik akustik mirip secara efektif.

---

## ⚠️ Limitasi & Gap Riset (Peluang untuk TA Kita)
> [!IMPORTANT]
> **Apa kelemahan paper ini yang diselesaikan oleh TA kita?**
- Kemiripan akustik umum tidak menjamin kesesuaian trajektori mood dinamis antartrek.

---

## 🔗 Relevansi dengan Tugas Akhir
- Mendukung perancangan tahap filtering sekunder (acoustic feature similarity) dalam pipeline rekomendasi playlist.
- Terkait dengan: [[Matriks-Sintesis]] | [[Dataset-DEAM]] | [[Bab-2-Tinjauan-Pustaka]]
