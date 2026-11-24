---
title: "Peta Modul Eksperimen & Kode Komputasi (05-Eksperimen)"
tags:
  - eksperimen
  - baseline
  - trajectory
  - deam
  - code-walkthrough
date: 2026-11-24
---

# 🔬 Peta Modul Eksperimen & Kode Komputasi (05-Eksperimen)

Direktori ini mengelola seluruh dokumentasi teknis, analisis dataset, replikasi baseline, dan pengembangan model usulan Tugas Akhir:

> **Repositori Kode Python:** `EXPERIMENT/Code/baseline_gaur/`  
> **Dataset Utama:** DEAM (*Database for Emotion Analysis in Music*, 1.802 klip musik, sampling 2 Hz)

---

## 🧭 Alur Kronologis Eksperimen (16–23 November 2026)

Seluruh modul diurutkan secara kronologis berdasarkan tahapan pengembangan riset:

```
05-Eksperimen/
│
├── 01-Dataset-DEAM-dan-Eksplorasi.md                ◄── (16 Nov) Fondasi dataset 1.802 lagu, offset 15s, 2 Hz
├── 02-Formulasi-Ekstraksi-Trajectory.md            ◄── (16 Nov) Formulasi vektor dinamis [Δv, Δa, θ] & slope
├── 03-Replikasi-Baseline-KNN-Gaur.md                ◄── (16 Nov) Telaah kritis static-point matching Gaur (2020)
├── 04-Panduan-Pra-Training-DEAM-Baseline-Gaur.md    ◄── (17 Nov) Pra-pemrosesan data, ekstraksi fitur & standarisasi
├── 05-Panduan-Validasi-dan-Testing-Baseline-Gaur.md ◄── (19 Nov) Validasi logika, unit test, & verifikasi playlist
├── 06-Log-Training-Baseline-Gaur.md                 ◄── (19 Nov) Log fitting KD-Tree CUDA RTX 3070 Ti pada DEAM
├── 07-Panduan-Terminologi-Sempro.md                 ◄── (19 Nov) Kamus istilah ilmiah MIR/RecSys & antisipasi sidang
├── 08-Blueprint-Arah-Penelitian-TA.md               ◄── (19 Nov) Master blueprint arsitektur Dynamic Trajectory
├── 09-Peta-Kode-Code-Walkthrough.md                 ◄── (23 Nov) Peta modul Python untuk bobot 10% sidang (Lampiran 4)
└── README.md                                        ◄── Indeks navigasi modul eksperimen
```

---

## 📊 Matriks Ringkasan Modul Eksperimen

| No | Modul Eksperimen | Tanggal | Topik Utama & Kontribusi | Berkas Terkait |
| :---: | :--- | :---: | :--- | :--- |
| **01** | **Dataset DEAM & Eksplorasi** | 16 Nov 2026 | Spesifikasi 1.802 audio, durasi 45 detik, sampling deret waktu 2 Hz (90 timestamp), pemetaan kuadran Russell (VA space). | [[01-Dataset-DEAM-dan-Eksplorasi]] |
| **02** | **Formulasi Ekstraksi Trajectory** | 16 Nov 2026 | Perancangan matematis turunan emosi $(\Delta v, \Delta a)$, sudut arah $\theta$, dan laju perubahan mood kontinu. | [[02-Formulasi-Ekstraksi-Trajectory]] |
| **03** | **Replikasi Baseline KNN Gaur** | 16 Nov 2026 | Analisis algoritma Two-Stage KNN Gaur & Donnelly (2020/2023) serta identifikasi *The Boundary Jump Problem*. | [[03-Replikasi-Baseline-KNN-Gaur]] |
| **04** | **Panduan Pra-Training DEAM** | 17 Nov 2026 | Ekstraksi fitur akustik Librosa, pra-fitting, audit korelasi audio-emosi, dan normalisasi Z-score. | [[04-Panduan-Pra-Training-DEAM-Baseline-Gaur]] |
| **05** | **Validasi & Testing Baseline** | 19 Nov 2026 | Test suite verifikasi playlist, pengujian kontinuitas, sanity check keteraturan waypoint target. | [[05-Panduan-Validasi-dan-Testing-Baseline-Gaur]] |
| **06** | **Log Training Baseline Gaur** | 19 Nov 2026 | Dokumentasi eksekusi fitting KD-Tree PyTorch CUDA (NVIDIA RTX 3070 Ti), konfigurasi parameter, dan output serialisasi. | [[06-Log-Training-Baseline-Gaur]] |
| **07** | **Panduan Terminologi Sempro** | 19 Nov 2026 | Glosarium ilmiah resmi ITERA: *dynamic mood-arc*, *smoothness index*, *boundary jump*, antisipasi jebakan penguji. | [[07-Panduan-Terminologi-Sempro]] |
| **08** | **Blueprint Arah Penelitian TA** | 19 Nov 2026 | Master blueprint filosofi riset, formulasi gap, arsitektur reranking trajectory alignment, dan target reduksi metrik $\mathcal{S} \ge 15\%$. | [[08-Blueprint-Arah-Penelitian-TA]] |
| **09** | **Peta Kode Code Walkthrough** | 23 Nov 2026 | Pemetaan file Python (`generate_playlist.py`, `metrics.py`, dll.) terhadap rumus matematika untuk membidik nilai sempurna 10% sidang. | [[09-Peta-Kode-Code-Walkthrough]] |

---

## 🔬 Matriks Komparasi Eksperimental

| Komponen Riset | Model Acuan: Baseline Gaur & Donnelly (2020) | Model Usulan: Dynamic Trajectory Alignment |
| :--- | :--- | :--- |
| **Representasi Emosi Lagu** | Rata-rata skalar tunggal $(\bar{v}, \bar{a})$ per lagu (*Static-Point Matching*). | Vektor trajektori deret waktu $[\Delta v, \Delta a, \theta]$ (90 timestamp 2 Hz). |
| **Algoritma Tahap 1** | KNN retrieval berdasarkan waypoint statis. | KNN retrieval berdasarkan waypoint statis. |
| **Algoritma Tahap 2** | Acoustic feature distance reranking. | **Dynamic Trajectory Alignment Reranking** (menyelaraskan outro lagu $A$ ke intro lagu $B$). |
| **Masalah Perseptual** | Memicu **The Boundary Jump Problem** (sentakan kasar saat pergantian trek). | **Menghilangkan Boundary Jump Shock** (transisi emosi mulus mengalir). |
| **Target Evaluasi** | Metrik standar Smoothness ($\mathcal{S}$) dan Evenness ($\mathcal{E}$). | **Reduksi nilai Smoothness Index ($\mathcal{S}$) minimal 15%** dibanding baseline. |
