---
title: "Peta Modul Eksperimen & Kode Komputasi"
tags:
  - eksperimen
  - baseline
  - trajectory
  - deam
  - code-walkthrough
date: 2026-11-24
---

# 🔬 Peta Modul Eksperimen & Kode Komputasi (05-Eksperimen)

Folder ini mengelola seluruh dokumentasi teknis, analisis data, replikasi baseline, dan pengembangan model usulan Tugas Akhir:

> **Repositori Kode Python:** `EXPERIMENT/Code/baseline_gaur/`  
> **Dataset Utama:** DEAM (1.802 klip musik, sampling 2 Hz)

---

## 🧭 Struktur Modul Eksperimen

```
05-Eksperimen/
│
├── 01-baseline-gaur/                  ◄── Replikasi model acuan Gaur & Donnelly (2020)
│   ├── 1_TRAIN_BASELINE.md            (Log eksekusi training baseline pada dataset DEAM)
│   ├── Panduan-Pra-Training-DEAM-Baseline-Gaur.md
│   ├── Panduan-Validasi-dan-Testing-Baseline-Gaur.md
│   └── Replikasi-Baseline-KNN.md      (Analisis gap & limitasi static-point matching)
│
└── 02-dynamic-trajectory-alignment/   ◄── Model usulan: Dynamic Trajectory Alignment
    ├── Dataset-DEAM.md                (Spesifikasi 1.802 audio, offset 15s, sampling 2 Hz)
    ├── Ekstraksi-Trajectory.md        (Formula vektor arah [Δv, Δa, θ] & slope)
    ├── Peta-Kode-Code-Walkthrough.md  (Panduan modul Python untuk bobot 10% sidang)
    ├── 4_BLUEPRINT_ARAH_PENELITIAN_TA.md (Master blueprint filosofi & arsitektur riset)
    └── 3_PANDUAN_TERMINOLOGI_SEMPRO.md (Kamus istilah teknis persiapan Sempro)
```

---

## 📊 Matriks Komparasi Eksperimen

| Komponen Riset | 01. Baseline Gaur & Donnelly (2020) | 02. Usulan: Dynamic Trajectory Alignment |
| :--- | :--- | :--- |
| **Representasi Emosi Lagu** | Rata-rata skalar tunggal $(\bar{v}, \bar{a})$ per lagu (*Static-Point Matching*). | Vektor trajektori deret waktu $[\Delta v, \Delta a, \theta]$ (90 timestamp 2 Hz). |
| **Algoritma Tahap 1** | KNN retrieval berdasarkan waypoint statis. | KNN retrieval berdasarkan waypoint statis. |
| **Algoritma Tahap 2** | Acoustic feature distance reranking. | **Dynamic Trajectory Alignment Reranking** (menyelaraskan outro lagu $A$ ke intro lagu $B$). |
| **Masalah Perseptual** | Memicu **The Boundary Jump Problem** (sentakan kasar saat pergantian trek). | **Menghilangkan Boundary Jump Shock** (transisi emosi mulus mengalir). |
| **Target Evaluasi** | Metrik standar Smoothness ($\mathcal{S}$) dan Evenness ($\mathcal{E}$). | **Reduksi nilai Smoothness Index ($\mathcal{S}$) minimal 15%** dibanding baseline. |
