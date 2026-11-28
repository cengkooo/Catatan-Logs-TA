---
title: "Alur Komparatif 4 Jalur: Model Usulan, Baseline Gaur, Kontrol Random, dan Uji Ablasi"
tags:
  - eksperimen
  - komparatif
  - ablation-study
  - diagram
  - tugas-akhir
date: 2026-11-28
---

# Alur Komparatif 4 Jalur Model dan Uji Ablasi

Catatan ini menyatukan alur kerja keempat jalur pengujian pada **Bab III Subbab 3.3 dan 3.5** ([chapter-3.tex](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/proposal-penelitian-andryano-123140205/chapters/chapter-3.tex)) dalam satu diagram terpadu.

> [!tip] Tautan Diagram Terpisah yang Sudah Ada di `05-Eksperimen`
> - **Model Usulan:** [[Alur-Metode-Usulan-Trajectory-Alignment]] ([[Alur-Metode-Usulan-Trajectory-Alignment.canvas]])
> - **Baseline Gaur:** [[Alur-Uji-Coba-Baseline-Gaur]] ([[Alur-Uji-Coba-Baseline-Gaur.canvas]])
> - **Evaluasi & Ablasi:** [[Alur-Evaluasi-Komparatif-dan-Ablasi]] ([[Alur-Evaluasi-Komparatif-dan-Ablasi.canvas]])
> - **Uji Dengar Manusia:** [[Alur-Blind-AB-Listening-Test]] ([[Alur-Blind-AB-Listening-Test.canvas]])

---

## 1. Diagram Alur Terpadu (4 Jalur dari Input Identik)

```mermaid
flowchart TD
    IN["Korpus DEAM Terproses (1.802 klip, 2 Hz, Offset 15s, Normalisasi [-1, 1], Song-Level Split 80/20, seed=42)"] --> WP["Interpolasi Kurva Mood-Arc -> M Waypoints (M = 5, 10, 15; 4 Rute, 540 Sekuens)"]
    IN --> CTRL["Jalur 1 (Kontrol): Random Retrieval (Seleksi Acak M Lagu)"]

    WP --> KNN["Tahap 1: KNN Retrieval (K = 20 Kandidat Terdekat per Waypoint)"]

    KNN --> GAUR["Jalur 2 (Baseline Gaur 2023/2024): Static-Point Matching + Kemiripan Akustik Librosa"]
    KNN --> ABL_OFF["Jalur 3 (Ablasi OFF, lambda_traj = 0): Penyaringan Titik Statis Tanpa Arah Trajektori & BJC"]
    KNN --> USULAN["Jalur 4 (Model Usulan / Ablasi ON, lambda_traj > 0): Dynamic Trajectory Alignment + Penalti BJC"]

    CTRL --> EVAL["Evaluasi Komputasional Objektif (S, E, CBJC) + Uji Wilcoxon (alpha = 0,05)"]
    GAUR --> EVAL
    ABL_OFF --> EVAL
    USULAN --> EVAL
```

---

## 2. Ringkasan Perbedaan Antarjalur

| Jalur | Tahap 1 (Kandidat) | Tahap 2 (Perankingan Ulang) | Fungsi dalam Pengujian |
| :--- | :--- | :--- | :--- |
| **1. Model Kontrol (*Random Retrieval*)** | Tidak memakai KNN; ambil $M$ lagu acak | Tidak ada | Batas bawah (*lower bound*) |
| **2. Model Acuan Gaur (2023/2024)** | KNN ($K=20$) pada titik rata-rata statis $\bar{\mathbf{p}}_k$ | *Static-Point Matching* + kemiripan fitur akustik Librosa | Pembanding *baseline* utama |
| **3. Uji Ablasi (*Trajectory Filter OFF*)** | KNN ($K=20$) identik (`seed=42`) | $\lambda_{\mathrm{traj}} = 0$ (tanpa arah trajektori & $\mathcal{BJC}$) | Mengisolasi efek tanpa modul trajektori |
| **4. Model Usulan (*Trajectory Filter ON*)** | KNN ($K=20$) identik (`seed=42`) | $\lambda_{\mathrm{traj}} > 0$ (*Cosine Alignment* $\mathrm{Sim}_{\mathrm{traj}}$ + penalti $\mathcal{BJC}$) | Membuktikan kontribusi kausal trajektori |
