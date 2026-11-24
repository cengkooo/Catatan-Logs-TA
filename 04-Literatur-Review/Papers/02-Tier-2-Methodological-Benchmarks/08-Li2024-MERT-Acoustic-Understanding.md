---
tier: "Tier 2: Methodological Benchmarks & Audio Similarity"
title: "Bedah Kritis: MERT Acoustic Music Understanding Model with Large-Scale Self-Supervised Training"
author: "Yizhi Li et al. (Cambridge / Queen Mary / HKUST)"
year: 2024
citekey: "li2024mert"
venue: "International Conference on Learning Representations (ICLR 2024)"
quartile: "Top-Tier Machine Learning (Oral Presentation)"
dataset: "160.000 Jam Musik Audio (Unlabeled) + Downstream Benchmark (DEAM, GTZAN, MTG-Jamendo)"
metode: "Self-Supervised Masked Language Modeling + Multi-Task Acoustic Pre-training (CQT + RVQ)"
gap_utama: "Model audio umum (seperti Wav2Vec 2.0 / HuBERT) dirancang untuk wicara (speech) dan gagal menangkap harmoni, pitch, dan timbre musik."
tags:
  - literatur
  - paper-review
  - foundation-model
  - mert
  - self-supervised
  - audio-embeddings
status: "audited"
aliases:
  - Li2024-MERT-Acoustic-Understanding
  - MERT Audio Model
---
# 📖 Bedah Kritis: Model Audio MERT (Li et al., 2024)
## *MERT: Acoustic Music Understanding Model with Large-Scale Self-Supervised Training*

> **Objek Bedah:** Naskah ICLR 2024 (73 KB text)  
> **Kedudukan dalam TA:** **Rujukan State-of-the-Art Feature Extractor Akustik Modern (Bab II Subbab 2.3)**

---

## 🧭 Step 0 & 1: Konteks & Abstrak Kuantitatif
* **Konteks:** Menghadirkan model fondasi (*foundation model*) musik akustik berbasis transformer self-supervised pertama yang dilatih pada 160 ribu jam audio.
* **Hasil Kuantitatif Konkret:**
  * Pada downstream task regresi emosi DEAM, representasi MERT meraih skor **$R^2 = 0.648$ (Arousal)** dan **$R^2 = 0.412$ (Valence)**, mengungguli representasi fitur klasik openSMILE/Librosa sebesar **+14.2%**.
  * Parameter model: 95M (MERT-v1-95M) dan 330M (MERT-v1-330M).

---

## 🔬 Step 4 & 7: Metodologi & Analisis Trade-off Komputasi
* **Arsitektur:** Menggabungkan *Constant-Q Transform (CQT)* untuk menangkap struktur nada musik dan *Residual Vector Quantization (RVQ)* EnCodec.
* **Trade-off untuk Skripsi ITERA:**
  * Walaupun embedding MERT menghasilkan representasi akustik yang sangat kaya, beban inferensinya membutuhkan GPU VRAM besar (~4-8 GB per batch).
  * *Keputusan Desain TA:* Untuk modul replikasi baseline dan pencarian real-time KNN, fitur akustik Librosa (MFCC, Spectral Centroid, Energy) tetap dipilih karena kecepatan inferensi berlatensi rendah (<50 ms), sementara MERT dijadikan rujukan perbandingan teoretis di Bab II.

---

## 💡 Step 9 & 10: Sintesis & Research Gap
1. **Fakta Terbukti:** Self-supervised pre-training dengan CQT mampu mengekstraksi representasi musikal yang jauh lebih superior dibanding model adaptasi wicara.
2. **Research Gap TA Kita:** MERT unggul dalam memahami fitur statis dan representasi global lagu, namun belum dieksplorasi untuk pemodelan trajektori transisi playlist antarlagu berorientasi mood-arc.
