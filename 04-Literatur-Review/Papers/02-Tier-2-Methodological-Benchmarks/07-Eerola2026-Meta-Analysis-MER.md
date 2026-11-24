---
tier: "Tier 2: Methodological Benchmarks & Audio Similarity"
title: "Bedah Kritis: A Meta-Analysis of Music Emotion Recognition Studies (Eerola et al., 2026)"
author: "Tuomas Eerola, Jonna Vuoskoski, & Petri Toiviainen"
year: 2026
citekey: "eerola2026meta"
venue: "IEEE Transactions on Affective Computing (Early Access 2025/2026)"
quartile: "Q1 Scopus (Top 5% Affective Computing)"
dataset: "Meta-analisis 144 studi empiris MER (melibatkan >50.000 lagu & 20 dataset)"
metode: "Systematic Meta-Analysis + Random-Effects Meta-Regression + Heterogeneity Analysis"
gap_utama: "Inkonsistensi pelaporan performa MER lintas studi akibat bias seleksi fitur, perbedaan durasi lag perseptual, dan ketiadaan standarisasi metrik regresi."
tags:
  - literatur
  - paper-review
  - meta-analysis
  - mer-benchmarks
  - arousal-valence
status: "audited"
aliases:
  - Eerola2026-Meta-Analysis-MER
  - Meta-Analysis Eerola
---
# 📖 Bedah Kritis: Meta-Analisis MER (Eerola et al., 2026)
## *A Meta-Analysis of Music Emotion Recognition Studies*

> **Objek Bedah:** Naskah Meta-Analisis IEEE TAC (83 KB text)  
> **Kedudukan dalam TA:** **Rujukan Otoritatif Validitas Metodologi Representasi Emosi (Bab II Subbab 2.1)**

---

## 🧭 Step 0 & 1: Konteks & Abstrak Kuantitatif
* **Konteks:** Meneliti sintesis komprehensif atas 144 studi empiris Music Emotion Recognition (MER) selama 2 dekade terakhir.
* **Hasil Kuantitatif Konkret:**
  * **Asimetri Prediktabilitas:** Model komputasi konsisten meraih akurasi korelasi tinggi pada dimensi **Arousal ($r = 0.68 \pm 0.08$)**, sementara **Valence jauh lebih menantang ($r = 0.42 \pm 0.12$)**.
  * **Perceptual Time Lag:** Respons afektif pendengar manusia memiliki jeda waktu alami (*temporal lag*) sebesar **1.5 hingga 3.0 detik** terhadap perubahan dinamika akustik audio.
  * **Ukuran Sampel:** Riset yang menggunakan klip $<30$ detik cenderung memiliki *effect size* lebih rendah karena pendengar belum mencapai kestabilan interpretasi emosi.

---

## 🔬 Step 4 & 5: Metodologi & Audit Eksperimen
* **Sintesis Metodologis:** Menunjukkan bahwa kombinasi fitur akustik standar (MFCC, Spectral, Dynamics) sudah cukup untuk merepresentasikan Arousal, namun Valence sangat bergantung pada modalitas harmonik dan lirik.
* **Red Flag yang Ditemukan Penulis pada Riset MER:** Lebih dari 40% studi MER tidak melaporkan interval kepercayaan (*confidence interval*), dan 28% studi memiliki indikasi *sample overlap* antar partisi data.

---

## 💡 Step 9 & 10: Sintesis & Research Gap
1. **Fakta Terbukti:** Arousal adalah fitur yang sangat objektif dan stabil untuk diprediksi oleh komputer, sedangkan Valence memiliki subjektivitas perseptual lebih tinggi.
2. **Lompatan SOTA:** Meta-analisis terluas dalam sejarah MIR yang memetakan disparitas performa lintas arsitektur ML/DL.
3. **Research Gap TA Kita:** Eerola membuktikan adanya *perceptual lag* 2-3 detik pada manusia; oleh karena itu, interpolasi waypoint emosi antarlagu tidak boleh berubah secara drastis dalam jeda waktu singkat (*The Boundary Jump Problem* harus diredam).
