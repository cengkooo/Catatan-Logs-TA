---
tier: "Tier 3: Contextual & Auxiliary Reference"
title: "Bedah Kritis: Feature Centric Based Deep Learning Approach for Music Mood Recognition with HuBERT Transformer Model"
author: "Y. Sun et al."
year: 2025
citekey: "sun2025feature"
venue: "IEEE Access, Vol. 13, 2025"
quartile: "Q1/Q2 Open Access Journal"
dataset: "DEAM (1.802 klip) & PMEmo"
metode: "HuBERT Audio Transformer Feature Extractor + BiLSTM Temporal Smoothing Regressor"
gap_utama: "Ekstraksi fitur akustik buatan tangan (handcrafted) gagal menangkap interaksi temporal jarak jauh pada data deret waktu emosi."
tags:
  - literatur
  - paper-review
  - hubert
  - transformer
  - deam
  - dynamic-regression
status: "audited"
aliases:
  - Sun2025-HuBERT-Music-Mood
  - HuBERT Sun
---
# 📖 Bedah Kritis: HuBERT Transformer untuk MER (Sun et al., 2025)
## *Feature Centric Deep Learning Approach with HuBERT Transformer Model*

> **Objek Bedah:** Naskah IEEE Access 2025 (110 KB text)  
> **Kedudukan dalam TA:** **Rujukan Benchmark Performa Regresi Emosi Terkini pada DEAM (Bab II Subbab 2.3)**

---

## 🧭 Step 0 & 1: Konteks & Abstrak Kuantitatif
* **Konteks:** Menerapkan arsitektur HuBERT transformer yang di-fine-tune untuk memprediksi deret waktu dinamis Valence dan Arousal pada dataset DEAM.
* **Hasil Kuantitatif Konkret:**
  * Meraih skor Pearson correlation **$r = 0.742$ (Arousal)** dan **$r = 0.518$ (Valence)** pada DEAM, membuktikan kemampuan representasi transformer dalam menangkap kurva emosi kontinu.

---

## 💡 Step 9 & 10: Sintesis & Research Gap
1. **Fakta Terbukti:** Model transformer mampu memetakan kurva trajektori emosi musik secara kontinu dengan korelasi tinggi.
2. **Research Gap TA Kita:** Sun dkk. fokus pada tahap prediksi emosi dari audio (*feature extraction*). Penelitian Tugas Akhir kita mengambil hasil trajektori tersebut untuk merancang algoritma optimasi transisi playlist (*downstream playlist alignment*).
