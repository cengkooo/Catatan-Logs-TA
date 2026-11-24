---
tier: "Tier 3: Contextual & Auxiliary Reference"
title: "Bedah Kritis: Music Mood Detection Based on Audio and Lyrics with Deep Neural Net (Delbouys et al., 2018)"
author: "Régis Delbouys et al. (Deezer Research)"
year: 2018
citekey: "delbouys2018music"
venue: "Proceedings of the 19th International Society for Music Information Retrieval Conference (ISMIR 2018)"
quartile: "Top-Tier MIR Conference (Peringkat #1 Dunia Bidang MIR)"
dataset: "DMDD (Deezer Mood Detection Dataset) — 18.644 trek berpasangan audio dan lirik"
metode: "Multimodal Fusion: Convolutional Neural Network (Audio) + Recurrent Neural Network / LSTM (Lyrics)"
gap_utama: "Keterbatasan performa model berbasis audio tunggal dalam membedakan emosi yang memiliki kemiripan energi akustik namun berbeda makna semantik."
tags:
  - literatur
  - paper-review
  - multimodal
  - dmdd
  - deezer
  - ismir
status: "audited"
aliases:
  - Delbouys2018-Music-Mood-Audio-Lyrics
  - DMDD Delbouys
---
# 📖 Bedah Kritis: Deteksi Mood Audio & Lirik (Delbouys et al., 2018)
## *Music Mood Detection Based on Audio and Lyrics with Deep Neural Net*

> **Objek Bedah:** Naskah ISMIR 2018 (31 KB text)  
> **Kedudukan dalam TA:** **Asal-Usul Korpus DMDD yang Dipakai Baseline Gaur (Bab II Subbab 2.2)**

---

## 🧭 Step 0 & 1: Konteks & Abstrak Kuantitatif
* **Konteks:** Tim Deezer Research merilis korpus DMDD (18.644 lagu) untuk membuktikan bahwa menggabungkan sinyal audio dengan teks lirik meningkatkan akurasi klasifikasi mood.
* **Hasil Kuantitatif Konkret:**
  * Model multimodal audio-lirik meraih skor **AUC-ROC = 0.884**, mengungguli audio-only (0.852) dan lyrics-only (0.793).
  * Menghasilkan anotasi biner/skalar statis pada 4 kuadran mood untuk keseluruhan trek.

---

## 💡 Step 9 & 10: Sintesis & Research Gap
1. **Fakta Terbukti:** Fusi multimodal audio dan lirik meningkatkan kemampuan pembedaan emosi secara signifikan dibanding analisis audio murni.
2. **Keterbatasan Utama untuk TA Kita:** Delbouys dkk. hanya menyediakan **satu label statis rata-rata** per trek pada dataset DMDD. Inilah akar penyebab mengapa baseline Gaur (2023) yang menggunakan DMDD tidak mampu menyelaraskan transisi intro/outro lagu.
