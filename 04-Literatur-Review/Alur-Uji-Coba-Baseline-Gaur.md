---
title: "Alur Uji Coba & Pembangkitan Baseline Gaur & Donnelly (2023/2024)"
tags:
  - literatur
  - baseline
  - gaur2024
  - diagram
  - tugas-akhir
date: 2026-11-26
---

# Alur Uji Coba & Cara Baseline Dihasilkan

Dokumen ini memvisualisasikan alur *end-to-end* bagaimana baseline **Gaur & Donnelly (2023/2024)** dihasilkan dan diuji pada dataset **DEAM** di repositori [`EXPERIMENT/Code/baseline_gaur/`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/EXPERIMENT/Code/baseline_gaur/README.md).

> [!tip] Versi Node-Graph Interaktif (Obsidian Canvas)
> Buka file **[[Alur-Uji-Coba-Baseline-Gaur.canvas]]** di Obsidian untuk tampilan *node-graph* yang bisa digeser, diperbesar, dan disunting langsung.

---

## Diagram Alur Pembangkitan & Uji Coba Baseline

```mermaid
flowchart TD
    subgraph S1["1. Persiapan Data & Preprocessing"]
        A["DEAM Dataset (1.802 klip, 45s)<br/>src/deam_loader.py<br/>Normalisasi V-A: [1,9] -> [-1,+1]"] --> B["GaurPreprocessor<br/>src/preprocessing.py<br/>IQR Discretizer -> Yeo-Johnson -> 12D PCA -> MinMax [-1,1]"]
        B --> C["Stratified 4-Quadrant Split<br/>src/split_utils.py<br/>Train 70% (1.261) | Val 15% (270) | Test 15% (271)"]
        C --> D["Spatial Index KD-Tree<br/>src/dataset.py<br/>Indeks koordinat unik (V, A) 2D"]
    end

    subgraph S2["2. Pembangkitan Playlist Baseline (Algorithm 1 Gaur)"]
        D --> E["Input Seed S0 & Target SN<br/>Tentukan panjang N & kandidat K"]
        E --> F["Stage 1: Linear Waypoint + KNN<br/>src/stage1_knn.py<br/>ST = SL + (SN - SL)/(N - L)<br/>Query KD-Tree ambil K kandidat"]
        F --> G["Stage 2: Audio Re-Ranking (CUDA)<br/>src/stage2_selector.py<br/>Jarak 12D PCA (Cosine / Euclidean / Manhattan)<br/>Pilih 1 lagu terdekat ke SL"]
        G --> H{"L < N ?"}
        H -- "Ya (Iterasi)" --> F
        H -- "Tidak (Selesai)" --> I["Playlist Baseline Terbentuk<br/>src/playlist_generator.py"]
    end

    subgraph S3["3. Protokol Uji Coba & Evaluasi"]
        I --> J1["Single-Run Benchmark (Q3 -> Q1)<br/>experiments/run_experiment.py<br/>N=12, K=7 (Cosine vs Euclidean vs Manhattan)"]
        I --> J2["Batch 540 Playlist (6 Rute Kuadran)<br/>experiments/run_quadrant_experiments.py<br/>K in {5,7,15} x N in {5,12,19} x 2 metrik x 5 trial"]
        J1 --> K["Evaluasi Metrik (src/metrics.py)<br/>Smoothness PCC: Cosine 0.9781, Euclidean 0.9876<br/>Evenness: Var(RMSE) V-A & Audio 12D"]
        J2 --> K
        K --> L["Audit Dinamika Intra-Lagu<br/>analyze_intra_song_dynamics.py<br/>98,11% (1.768/1.802) lagu DEAM melintasi kuadran<br/>-> Bukti kelemahan static-point matching"]
    end
```

---

## Ringkasan File Implementasi Terkait
- **Pipeline Utama:** [`run_experiment.py`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/EXPERIMENT/Code/baseline_gaur/experiments/run_experiment.py) & [`run_quadrant_experiments.py`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/EXPERIMENT/Code/baseline_gaur/experiments/run_quadrant_experiments.py)
- **Output Benchmark:** [`metrics_comparison_deam.csv`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/EXPERIMENT/Code/baseline_gaur/experiments/results/metrics_comparison_deam.csv), [`batch_quadrant_experiments_deam.csv`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/EXPERIMENT/Code/baseline_gaur/experiments/results/batch_quadrant_experiments_deam.csv), [`deam_intra_song_stats.json`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/EXPERIMENT/Code/baseline_gaur/experiments/results/deam_intra_song_stats.json)
