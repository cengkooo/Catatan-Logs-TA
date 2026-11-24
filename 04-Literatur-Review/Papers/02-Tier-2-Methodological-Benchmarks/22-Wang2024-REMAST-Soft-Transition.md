---
tier: "Tier 2: Methodological Benchmarks & Audio Similarity"
title: "Bedah Kritis: REMAST — Real-Time Emotion-Based Music Arrangement With Soft Transition (Wang et al., 2024)"
author: "Zihao Wang, Le Ma, Chen Zhang, Bo Han, Yunfei Xu, Yikai Wang, Xinyi Chen, HaoRong Hong, Wenbo Liu, Xinda Wu, & Kejun Zhang"
year: 2024
citekey: "wang2024remast"
venue: "IEEE Transactions on Affective Computing, Vol. 16, No. 2, pp. 1016–1030"
quartile: "Q1 Scopus (Top 5% Affective Computing)"
dataset: "E-GComp, VGmidi, dan Pop1K7"
metode: "Sequential Emotion Conditioning + Melody Downsampling + Soft Transition Trajectory Limiter"
gap_utama: "Model pengubah musik afektif konvensional memicu sentakan struktural kasar saat transisi antar-segmen karena mengabaikan kontinuitas inersia emosi sebelumnya."
tags:
  - literatur
  - paper-review
  - soft-transition
  - music-arrangement
  - circumplex-trajectory
  - ieee-tac
status: "audited"
aliases:
  - Wang2024-REMAST-Soft-Transition
  - REMAST Soft Transition
---
# 📖 Bedah Kritis: REMAST — Soft Emotion Transition (Wang et al., 2024)
## *Real-Time Emotion-Based Music Arrangement With Soft Transition*

> **Objek Bedah:** Naskah Riset IEEE Transactions on Affective Computing (2024)  
> **Kedudukan dalam TA:** **Rujukan Pembanding Arsitektur Transisi Halus & Penalti Lonjakan Emosi (Bab II & Bab III)**

---

## 🧭 Step 0 & 1: Konteks & Abstrak Kuantitatif
* **Konteks:** Meneliti tantangan penataan musik berbasis emosi real-time di mana transisi emosi yang terlalu mendadak merusak koherensi musikal.
* **Hasil Kuantitatif Konkret:**
  * Penggabungan inersia emosi langkah sebelumnya dengan emosi target mampu mereduksi kekasaran transisi sebesar **34,2%** pada uji dengar subyektif manusia.
  * Menerapkan batas kelengkungan trajektori emosi di ruang sirkumpleks Valence-Arousal Russell.

---

## 📐 Step 4: Formulasi Soft Transition & Kaitan dengan TA
* **Fungsi Transisi Emosi:**
  Menggabungkan vektor emosi segmen $t-1$ dengan target $t$:
  $$\mathbf{e}_{\text{target}, t} = \gamma \mathbf{e}_{t-1} + (1 - \gamma) \mathbf{e}_{\text{input}, t}$$
* **Relevansi Langsung dengan Tugas Akhir Kita:**
  Sangat paralel dengan perumusan **Boundary Jump Cost ($\mathcal{BJC}$)** pada Tugas Akhir kita, di mana transisi outro lagu $L_{k-1}$ ke intro lagu $L_k$ wajib diminimalkan agar tidak terjadi lompatan perseptual tajam.

---

## 🎯 Step 10: Research Gap & Kontribusi
* **Keterbatasan REMAST:** Diterapkan pada musik simbolik (MIDI generation), belum diuji pada playlist lagu utuh audio riil skala masif.
* **Posisi TA Kita:** Menerapkan prinsip transisi halus (*soft transition*) pada pemilihan katalog trek rekaman audio penuh (dataset DEAM) dengan menggabungkan perankingan trajektori dinamis dan fitur akustik.
