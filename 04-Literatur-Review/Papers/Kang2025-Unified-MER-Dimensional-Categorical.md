---
title: "Bedah Kritis: Towards Unified Music Emotion Recognition across Dimensional and Categorical Models"
author: "Huan Kang et al."
year: 2025
citekey: "kang2025unified"
venue: "IEEE Transactions on Multimedia (TMM 2025)"
quartile: "Q1 Scopus (Top 10% Multimedia & AI)"
dataset: "Cross-Corpus: DEAM, PMEmo, Emotify, 4Q"
metode: "Multi-Task Joint Learning + Coordinate-to-Category Projection Mapping"
gap_utama: "Keterpisahan dikotomis antara riset MER berbasis model dimensi kontinu (Russell) dan model kategori diskrit (Ekman/Hevner)."
tags:
  - literatur
  - paper-review
  - unified-mer
  - dimensional-categorical
  - cross-corpus
status: "audited"
---

# 📖 Bedah Kritis: Unifikasi Model Emosi Musik (Kang et al., 2025)
## *Towards Unified Music Emotion Recognition across Dimensional and Categorical Models*

> **Objek Bedah:** Naskah IEEE TMM 2025 (48 KB text)  
> **Kedudukan dalam TA:** **Landasan Penyelarasan Taksonomi Emosi (Bab II Subbab 2.1)**

---

## 🧭 Step 0 & 1: Konteks & Abstrak Kuantitatif
* **Konteks:** Menjembatani kesenjangan representasi emosi musik antara ruang dimensi kontinu $(v, a)$ dengan label kategori kata sifat (*happy, sad, calm, angry*).
* **Hasil Kuantitatif Konkret:**
  * Arsitektur joint-learning meningkatkan akurasi klasifikasi F1-score kategori sebesar **+6.8%** sekaligus mempertahankan nilai CCC regresi dimensi pada **$CCC \ge 0.72$**.
  * Memvalidasi proyeksi matematis sudut polar $\theta = \text{atan2}(a, v)$ pada model Russell terhadap cluster label diskrit pengguna.

---

## 💡 Step 9 & 10: Sintesis & Research Gap
1. **Fakta Terbukti:** Model dimensi kontinu dan model kategori diskrit saling melengkapi dan dapat diunifikasi melalui pemetaan sudut dan magnitudo ruang 2D.
2. **Kegunaan Praktis untuk TA:** Memperkuat argumen Bab I bahwa memilih model 2D kontinu Valence-Arousal memungkinkan interpolasi lintasan yang fleksibel sekaligus tetap dapat diterjemahkan ke dalam label suasana hati yang dipahami pengguna awam.
