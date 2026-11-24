---
title: "Bedah Kritis: Leveraging LLM Embeddings for Cross Dataset Label Alignment and Zero Shot Music Emotion Prediction"
author: "Xuan Liu et al."
year: 2024
citekey: "liu2024leveraging"
venue: "IEEE International Conference on Multimedia and Expo (ICME 2024)"
quartile: "International Conference on Multimedia (Core B+ / IEEE)"
dataset: "DEAM, PMEmo, Emotify, AMG1608"
metode: "Text Embeddings dari Large Language Models (LLM / text-embedding-ada-002) + Zero-Shot Cross-Dataset Alignment"
gap_utama: "Inkompatibilitas taksonomi anotasi antar dataset MER yang menghambat transfer learning dan evaluasi lintas korpus."
tags:
  - literatur
  - paper-review
  - llm-embeddings
  - cross-dataset
  - zero-shot
status: "audited"
---

# 📖 Bedah Kritis: Penyelarasan Label Lintas Dataset LLM (Liu et al., 2024)
## *Leveraging LLM Embeddings for Cross Dataset Label Alignment*

> **Objek Bedah:** Naskah IEEE ICME 2024 (38 KB text)  
> **Kedudukan dalam TA:** **Rujukan Integrasi Taksonomi Dataset Multidomain (Bab II Subbab 2.1)**

---

## 🧭 Step 0 & 1: Konteks & Abstrak Kuantitatif
* **Konteks:** Menggunakan kecerdasan bahasa LLM untuk memetakan label emosi teks yang beragam dari berbagai dataset musik ke dalam ruang semantik bersama (*shared semantic space*).
* **Hasil Kuantitatif Konkret:**
  * Meningkatkan skor transfer lintas dataset sebesar **+9.2%** F1-score tanpa perlu melatih ulang model audio dari awal (*zero-shot alignment*).
  * Memvalidasi bahwa ruang 2D Valence-Arousal adalah *anchor representation* yang paling stabil dalam menyatukan korpus musik yang berbeda.

---

## 💡 Step 9 & 10: Sintesis & Research Gap
1. **Fakta Terbukti:** LLM embedding sangat efektif menyelaraskan variasi istilah emosi ke dalam sistem koordinat kontinu terpadu.
2. **Kegunaan untuk TA:** Memperkuat justifikasi bahwa pemetaan koordinat 2D pada DEAM bersifat universal dan dapat dipahami secara lintas platform.
