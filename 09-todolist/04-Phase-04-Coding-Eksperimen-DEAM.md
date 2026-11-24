---
title: "Fase 04: Implementasi Kode Eksperimen & Baseline"
tags:
  - todolist
  - phase-4
  - coding
  - eksperimen
status: "TODO"
aliases:
  - Phase-04-Coding-Eksperimen-DEAM
  - Coding DEAM Todolist
---
# 💻 Fase 04: Implementasi Kode & Validasi Eksperimen

> **Tujuan Akhir:** Menyiapkan seluruh modul kode Python yang bersih, modular, dapat direproduksi (*reproducible*), dan siap untuk sesi **Code Walkthrough (bobot 10% di sidang)**.
> **Lokasi Kode:** Direktori `EXPERIMENT/Code/`.

---

## 🎯 Sub-Fase 4.1: Persiapan Lingkungan & Modul Data Loader (4.1)

- [ ] **Langkah 4.1.1 — Konfigurasi Environment Python:**
  - Pastikan dependencies terinstal: `numpy`, `pandas`, `scipy`, `scikit-learn`, `librosa`, `matplotlib`, `seaborn`.
  - Buat berkas `requirements.txt` atau environment lock.
- [ ] **Langkah 4.1.2 — Pembuatan `deam_loader.py`:**
  - Buat fungsi `load_deam_annotations(csv_path)`: memuat metadata dinamis Valence dan Arousal 2 Hz.
  - Buat fungsi `compute_song_summary(df_annotations)`: menghitung mean, median, standard deviasi, serta koordinat awal ($t=15\text{s}$) dan akhir ($t=45\text{s}$).

---

## 🎯 Sub-Fase 4.2: Modul Ekstraksi Trajectory (`trajectory_extractor.py`) (4.2)

- [ ] **Langkah 4.2.1 — Kalkulasi Slope & Vektor Delta:**
  - Hitung slope regresi linear pergerakan mood: $\beta_V = \text{polyfit}(t, V, 1)[0]$, $\beta_A = \text{polyfit}(t, A, 1)[0]$.
  - Hitung magnitude pergerakan emosi: $\|\mathbf{v}\| = \sqrt{\Delta V^2 + \Delta A^2}$.
- [ ] **Langkah 4.2.2 — Validasi EDA Sinyal Trajectory:**
  - Buat notebook EDA visualisasi: Berapa persen lagu di DEAM yang memiliki pergerakan signifikan $(\|\mathbf{v}\| > 0.1)$?
  - Hasilkan 1 tabel distribusi + 2 grafik visualisasi untuk bahan Bab 1 & Bimbingan.

---

## 🎯 Sub-Fase 4.3: Replikasi Baseline Gaur & Donnelly (`baseline_knn.py`) (4.3)

- [ ] **Langkah 4.3.1 — Implementasi Tahap 1 (KNN di Ruang V-A):**
  - Implementasikan interpolasi linier $M$ waypoint antara $P_{\text{start}}$ dan $P_{\text{target}}$.
  - Gunakan `NearestNeighbors(n_neighbors=k, metric='euclidean')` untuk mengambil kandidat terdekat pada setiap waypoint.
- [ ] **Langkah 4.3.2 — Implementasi Tahap 2 (Cosine Audio Feature Re-ranking):**
  - Hitung Cosine Similarity antara fitur audio kandidat dengan lagu sebelumnya.
  - Seleksi lagu dengan skor kesamaan tertinggi yang belum pernah diputar (no repetition constraint).

---

## 🎯 Sub-Fase 4.4: Implementasi Usulan Trajectory Alignment (`moodarc_pipeline.py`) (4.4)

- [ ] **Langkah 4.4.1 — Modul Trajectory Angle Alignment:**
  - Hitung sudut kosinus antara vektor target mood-arc segmen ke-$i$ $(\mathbf{v}_{\text{arc}, i})$ dan vektor lagu $(\mathbf{v}_{\text{song}, j})$:
    $$\text{align\_score} = \frac{\mathbf{v}_{\text{arc}} \cdot \mathbf{v}_{\text{song}}}{\|\mathbf{v}_{\text{arc}}\| \|\mathbf{v}_{\text{song}}\|}$$
- [ ] **Langkah 4.4.2 — Integrasi Hybrid Scoring Function:**
  - Gabungkan skor audio similarity dan trajectory alignment dengan bobot $\alpha \in [0, 1]$.
  - Lakukan pencarian parameter $\alpha$ optimal (misal $\alpha = 0.5$).

---

## 🎯 Sub-Fase 4.5: Modul Evaluasi & Komparasi Kuantitatif (`evaluate_metrics.py`) (4.5)

- [ ] **Langkah 4.5.1 — Fungsi Evaluasi Smoothness & Evenness:**
  - Fungsi `calculate_smoothness(playlist_tracks)`
  - Fungsi `calculate_evenness(playlist_tracks)`
- [ ] **Langkah 4.5.2 — Uji Komparasi 100 Playlist Uji:**
  - Jalankan pengujian pada 100 pasang target kurva acak:
    1. Baseline Random Selection
    2. Replikasi Gaur & Donnelly (KNN murni)
    3. Usulan TA (KNN + Trajectory Alignment)
  - Cetak tabel perbandingan metrik dan simpan grafik boxplot komparasi.
