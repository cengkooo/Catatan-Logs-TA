---
title: "Towards Unified Music Emotion Recognition across Dimensional and Categorical Models"
author: "Jaeyong Kang, Dorien Herremans"
year: 2025
citekey: "kang2025unified"
dataset: "DEAM, Emomusic, MTG-Jamendo"
metode: "Cross-Modal Contrastive Multi-Task Representation Learning"
tags:
  - literatur
  - paper-review
status: "read"
---

# 📖 Towards Unified Music Emotion Recognition across Dimensional and Categorical Models

- **Penulis:** `Jaeyong Kang, Dorien Herremans` (2025)
- **Citekey LaTeX:** `\cite{kang2025unified}`
- **Dataset:** `DEAM, Emomusic, MTG-Jamendo`
- **Metode Utama:** `Cross-Modal Contrastive Multi-Task Representation Learning`

---

## 🎯 Masalah & Tujuan Riset
- **Permasalahan:** Adanya jurang pemisah antara model emosi dimensional (Valence-Arousal) dan model kategorikal (tag kata sifat) yang mempersulit unifikasi sistem pencarian musik.
- **Tujuan:** Membangun representasi terpadu yang memetakan sinyal audio musik ke dalam ruang bersama dimensional dan kategorikal secara konsisten.

---

## 🔬 Arsitektur & Metodologi
- **Representasi Emosi:** Penyelarasan ruang 2D Russell dengan 56 kategori tag suasana hati musik.
- **Algoritma / Pendekatan:** Contrastive learning dengan fungsi loss gabungan (loss kosinus untuk arah afek dan loss regresi koordinat).
- **Metrik Evaluasi:** Korelasi Pearson r pada DEAM dan Mean Average Precision (MAP) pada klasifikasi tag.

---

## 💡 Temuan Utama & Hasil
- Representasi bersama meningkatkan generalisasi lintas dataset dan stabilitas pemetaan koordinat emosi.

---

## ⚠️ Limitasi & Gap Riset (Peluang untuk TA Kita)
> [!IMPORTANT]
> **Apa kelemahan paper ini yang diselesaikan oleh TA kita?**
- Fokus pada penanaman representasi (embedding) level trek terisolasi, bukan sekuens playlist.

---

## 🔗 Relevansi dengan Tugas Akhir
- Mendukung argumentasi stabilitas koordinat Valence-Arousal dalam ruang metrik pencarian kandidat playlist.
- Terkait dengan: [[Matriks-Sintesis]] | [[01-Dataset-DEAM-dan-Eksplorasi|Dataset-DEAM]] | [[Bab-2-Tinjauan-Pustaka]]
