---
title: Catatan Eksplorasi & Analisis Dataset DEAM
tags:
  - eksperimen
  - deam
  - dataset
  - audio
  - time-series
  - tugas-akhir
date: 2026-11-17
aliases:
  - Dataset-DEAM
  - Eksplorasi DEAM
---
# 🎵 Dataset DEAM (Database for Emotion Analysis in Music)

Dokumen ini mendokumentasikan analisis mendalam dataset **DEAM** yang digunakan sebagai data primer utama penelitian Tugas Akhir.

---

## 📊 Profil & Karakteristik Data Empiris

* **Lokasi Data Lokal:** `EXPERIMENT/Dataset/DEAM/`
* **Jumlah Lagu:** **1.802 klip audio penuh** (`.mp3`, durasi 45 detik, sample rate 44.1 kHz) pada `DEAM_audio/MEMD_audio/`.
* **Anotasi Statis (Song-Level):**
  * File: `static_annotations_averaged_songs_1_2000.csv` dan `songs_2000_2058.csv` (total 1.802 entri valid).
  * Format Skala: Skala Likert / SAM $[1.0, 9.0]$ dengan nilai netral di $5.0$.
  * Statistik Aktual:
    * Valence: Min $1.6$, Max $8.4$, Rata-rata $4.904$
    * Arousal: Min $1.6$, Max $8.1$, Rata-rata $4.814$
  * Rumus Normalisasi ke $[-1.0, +1.0]$:
    $$V_{\text{norm}} = \frac{V_{\text{DEAM}} - 5.0}{4.0}, \quad A_{\text{norm}} = \frac{A_{\text{DEAM}} - 5.0}{4.0}$$
* **Distribusi 4-Kuadran Russell:**
  * **Kuadran I ($V > 0, A > 0$):** 594 lagu (33.0%) — Happy / Energetic
  * **Kuadran II ($V \le 0, A > 0$):** 229 lagu (12.7%) — Angry / Anxious
  * **Kuadran III ($V \le 0, A \le 0$):** 742 lagu (41.2%) — Sad / Depressed
  * **Kuadran IV ($V > 0, A \le 0$):** 237 lagu (13.2%) — Calm / Relaxed
* **Anotasi Dinamis (Time-Series 2 Hz):**
  * File: `dynamic (per second annotations)/valence.csv` dan `arousal.csv` (matriks $1.802 \times 1.224$).
  * Resolusi Temporal: 2 Hz (sampling tiap 500 ms, dimulai dari `sample_15000ms` untuk membuang artefak transisi pendengaran pada 15 detik pertama).

---

## ⚖️ Analisis SWOT Dataset DEAM

| Kekuatan (Strengths) | Kelemahan (Weaknesses) |
| :--- | :--- |
| • Satu-satunya dataset musik terbuka dengan anotasi dinamis 2 Hz manusia berskala besar.<br>• Data audio WAV/MP3 lengkap tersedia secara legal tanpa ketergantungan API pihak ketiga.<br>• Memuat anotasi statis dan dinamis sekaligus, memungkinkan komparasi adil antara baseline Gaur vs usulan Trajectory. | • Durasi hanya 45 detik per klip (bukan lagu berdurasi 3-5 menit penuh).<br>• Variansi genre condong ke musik bebas royalti (Jamendo/Free Music Archive). |

| Peluang (Opportunities) | Ancaman (Threats) |
| :--- | :--- |
| • Mengekstrak vektor arah dan kecepatan pergeseran emosi internal ($\mathbf{v}_{\text{song}} = (\beta_V, \beta_A)$) yang belum pernah dimanfaatkan oleh model acuan Gaur (2020/2024).<br>• Mengeliminasi diskontinuitas batas antarlagu (*boundary jumps*). | • Fluktuasi noise anotasi subjektif manusia per 500 ms (memerlukan filter penghalusan moving average / Kalman filter). |

---

## ✂️ Partisi Dataset Resmi (Stratified 70/15/15)

Untuk menjamin representasi merata di tengah *class imbalance*, dataset dipartisi menggunakan modul `src/split_utils.py` dengan manifest tersimpan di `EXPERIMENT/Code/baseline_gaur/experiments/splits/`:

* **Train Set (70% — 1.261 lagu):** `deam_train_manifest.csv` (Q3: 41,16%, Q1: 32,99%, Q4: 13,16%, Q2: 12,69%).
* **Validation Set (15% — 270 lagu):** `deam_val_manifest.csv` (Q3: 41,11%, Q1: 32,96%, Q2: 12,96%, Q4: 12,96%).
* **Test Set (15% — 271 lagu):** `deam_test_manifest.csv` (Q3: 41,33%, Q1: 32,84%, Q4: 13,28%, Q2: 12,55%).
* **Zero Data Leakage:** Preprocessing Yeo-Johnson & PCA hanya di-fit pada Train set, lalu di-transform ke Val/Test.

---

## 🔗 Navigasi & File Terkait
- **Panduan Lengkap Pra-Training Baseline pada DEAM:** [[04-Panduan-Pra-Training-DEAM-Baseline-Gaur|Panduan-Pra-Training-DEAM-Baseline-Gaur]]
- **Dokumentasi Replikasi Baseline:** [[03-Replikasi-Baseline-KNN-Gaur|Replikasi-Baseline-KNN]]
- **Todolist Eksperimen:** [[06-Task-Baseline-KNN-Gaur|Experiment-Baseline-KNN-Gaur-Todolist]]
- **Tutorial Eksekusi CUDA:** `EXPERIMENT/Code/baseline_gaur/TUTORIAL_RUN_CUDA.md`
