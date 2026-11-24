---tier: "Tier 2: Methodological Benchmarks & Audio Similarity"

title: "Bedah Kritis: Musical Audio Similarity with Self-supervised Convolutional Neural Networks"
author: "Matthias Thome, David Doukhan, & Gaël Richard"
year: 2022
citekey: "thome2022musical"
venue: "IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP 2022)"
quartile: "Top-Tier Audio Processing Conference (Core A)"
dataset: "Million Song Dataset (MSD) Subsets & Jamendo"
metode: "Self-Supervised Contrastive Learning (SimCLR Audio Adaptation) + Triplet Loss"
gap_utama: "Pengukuran kemiripan audio musik tradisional berbasis jarak Euclidean fitur buatan tangan (handcrafted) rentan terhadap bias loudness dan instrumentasi semu."
tags:
  - literatur
  - paper-review
  - audio-similarity
  - contrastive-learning
  - timbral-distance
status: "audited"
aliases:
  - Thome2022-Musical-Audio-Similarity
  - Audio Similarity Thome
---
# 📖 Bedah Kritis: Kemiripan Audio Musik (Thome et al., 2022)
## *Musical Audio Similarity with Self-supervised Convolutional Neural Networks*

> **Objek Bedah:** Naskah ICASSP 2022 (12 KB text)  
> **Kedudukan dalam TA:** **Pondasi Reranking Jarak Akustik Tahap 2 (Bab III Subbab 3.3)**

---

## 🧭 Step 0 & 1: Konteks & Abstrak Kuantitatif
* **Konteks:** Mengembangkan representasi kemiripan akustik musik tanpa memerlukan anotasi label manual menggunakan *self-supervised contrastive learning*.
* **Hasil Kuantitatif Konkret:**
  * Mengungguli jarak MFCC standar dalam tugas *audio retrieval* dengan peningkatan Mean Average Precision (mAP) sebesar **+18.4%**.
  * Membuktikan bahwa kesamaan musik yang dipersepsikan manusia bertumpu pada keselarasan *timbral smoothness* dan *spectral flux*.

---

## 💡 Step 9 & 10: Sintesis & Research Gap
1. **Fakta Terbukti:** Jarak akustik antar segmen musik dapat diukur secara andal untuk menghindari transisi instrumen yang terlalu kontras saat pergantian lagu.
2. **Research Gap TA Kita:** Thome dkk. mengukur kemiripan global antar lagu utuh; belum pernah diterapkan untuk menyelaraskan segmen lokal spesifik (*outro* trek $A$ ke *intro* trek $B$) pada playlist mood-arc.
