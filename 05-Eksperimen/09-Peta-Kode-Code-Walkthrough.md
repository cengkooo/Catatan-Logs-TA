---
title: "Peta Kode untuk Code Walkthrough (Lampiran 4 Pedoman TA ITERA)"
tags:
  - code-walkthrough
  - eksperimen
  - sidangnya-ta
  - python
  - lampiran-4
created: 2026-11-23
updated: 2026-11-23
aliases:
  - Peta-Kode-Code-Walkthrough
  - Code Walkthrough Sidang
---
# 💻 Peta Kode untuk Code Walkthrough (Lampiran 4)

Dokumen ini disusun sebagai panduan teknis operasional (*Cheat Sheet / Code-to-Math Mapping*) untuk menghadapi **Sesi Code Walkthrough (Bobot 10% Nilai Sidang Akhir)** di hadapan dewan penguji Program Studi Teknik Informatika ITERA sesuai **Pedoman TA [1.2.0] Subbab 7.5**.

> [!TIP]
> **Tujuan Code Walkthrough:** Dewan penguji akan menguji secara acak apakah mahasiswa benar-benar menulis, memahami, dan dapat mempertanggungjawabkan implementasi algoritma pada repositori kode: *"Tunjukkan di baris kode mana rumus matematika Bab 3 Anda dieksekusi!"*.

---

## 🗺️ Matriks Relasi: Rumus Bab 3 $\leftrightarrow$ File & Baris Kode Sumber

| No | Persamaan Matematis di Naskah Bab 3 | Berkas Kode Sumber | Fungsi / Class Python | Parameter & Keterangan Walkthrough |
| :-: | :--- | :--- | :--- | :--- |
| **1** | **Protokol Audio DEAM (Offset 15s, Sampling 2 Hz)**<br/>$\mathbf{x}(t) \text{ untuk } t \in [15.0, 60.0]$ | `EXPERIMENT/Code/baseline_gaur/src/data_loader.py` | `load_deam_clip()` | `sr=22050, offset=15.0, duration=45.0`. Jelaskan ke penguji: 15 detik pertama dipotong karena merupakan warming-up anotator. |
| **2** | **Normalisasi Dimensi Valence & Arousal**<br/>$v_{\text{norm}} = \frac{v - \mu_v}{\sigma_v} \text{ atau } 2\frac{v - v_{\min}}{v_{\max} - v_{\min}} - 1$ | `EXPERIMENT/Code/baseline_gaur/analyze_intra_song_dynamics.py` | `normalize_va_values()` | Menyelaraskan rentang anotasi DEAM (asli $[1.0, 9.0]$) ke ruang Cartesian simetris $[-1.0, +1.0]$. |
| **3** | **Vektor Trajektori Dinamis Lagu ($T_i$)**<br/>$\vec{\mathbf{v}}_i = \mathbf{p}_i(t_{\text{end}}) - \mathbf{p}_i(t_0) = (\Delta V_i, \Delta A_i)$ | `EXPERIMENT/Code/baseline_gaur/src/trajectory.py` | `extract_dynamic_trajectory()` | Menghitung vektor selisih 2D antara koordinat detik ke-45 dengan detik ke-15 (90 timestamp 2 Hz). |
| **4** | **Regresi Lereng Sudut Trajektori**<br/>$\theta_i = \arctan2(\Delta A_i, \Delta V_i), \quad m_i = \frac{\Delta A_i}{\Delta V_i}$ | `EXPERIMENT/Code/baseline_gaur/analyze_intra_song_dynamics.py` | `compute_trajectory_angle()` | Menentukan arah pergerakan emosi lagu (naik/turun energi vs ceria/sedih). |
| **5** | **Baseline KNN Retrieval (Gaur & Donnelly)**<br/>$d(\mathbf{w}_j, \bar{\mathbf{p}}_k) = \|\mathbf{w}_j - \bar{\mathbf{p}}_k\|_2$ | `EXPERIMENT/Code/baseline_gaur/src/knn_baseline.py` | `KNNPlaylistGenerator.query()` | Pencarian $K$ lagu terdekat terhadap titik waypoint target berdasarkan titik rata-rata statis. |
| **6** | **Trajectory Alignment Reranking Score**<br/>$Score(i, j) = (1-\alpha) \cdot d_{\text{dist}} + \alpha \cdot \cos(\vec{\mathbf{v}}_i, \vec{\mathbf{w}}_{j, j+1})$ | `EXPERIMENT/Code/baseline_gaur/src/reranker.py` | `trajectory_alignment_rerank()` | Bobot $\alpha$ mengontrol kompromi antara kedekatan posisi statis dan keselarasan arah trajektori dinamis. |
| **7** | **Metrik Smoothness Playlist ($\mathcal{S}$)**<br/>$\mathcal{S} = \frac{1}{M-1} \sum_{k=1}^{M-1} \|\mathbf{p}_k(t_{\text{end}}) - \mathbf{p}_{k+1}(t_0)\|_2$ | `EXPERIMENT/Code/baseline_gaur/src/metrics.py` | `calculate_playlist_smoothness()` | Mengukur kehalusan perpindahan emosi di perbatasan sambungan lagu. Semakin kecil semakin mulus. |
| **8** | **Metrik Evenness Playlist ($\mathcal{E}$)**<br/>$\mathcal{E} = \text{Var}(\{\|P_{k+1} - P_k\|_2\}_{k=1}^{M-1})$ | `EXPERIMENT/Code/baseline_gaur/src/metrics.py` | `calculate_playlist_evenness()` | Mengukur konsistensi laju perubahan jarak antar-waypoint sepanjang playlist. |
| **9** | **Boundary Jump Cost Penalty ($\mathcal{B}$)**<br/>$\mathcal{B} = \max(0, \|\mathbf{p}_k(t_{\text{end}}) - \mathbf{p}_{k+1}(t_0)\| - \tau)$ | `EXPERIMENT/Code/baseline_gaur/src/metrics.py` | `compute_boundary_jump_cost()` | Memberikan penalti tajam jika terjadi lompatan emosi yang melampaui ambang batas persepsi $\tau$. |

---

## ⚡ Panduan Demo & Smoke Test Langsung (Bila Diminta Penguji)

### 1. Perintah Eksekusi Cepat Terminal (PowerShell):
```powershell
# Berpindah ke direktori eksperimen baseline
cd "EXPERIMENT\Code\baseline_gaur"

# Jalankan benchmark playlist subsample cepat (20% data) via GPU / PyTorch
uv run python experiments/run_benchmark.py --mode fast --subsample 0.2

# Tampilkan visualisasi plot perbandingan trajectory vs random
python analyze_intra_song_dynamics.py
```

### 2. Cara Menjelaskan Arsitektur Sistem dalam 30 Detik:
> *"Bapak/Ibu Penguji, sistem ini membagi pembangkitan playlist menjadi dua tahap: Tahap 1 menggunakan algoritma KNN untuk menyaring kandidat lagu di sekitar waypoint target ruang emosi. Tahap 2 menerapkan reranking berbasis Trajectory Alignment yang mencocokkan vektor pergerakan internal lagu dengan vektor target transisi, sehingga mengeliminasi lompatan emosi kasar pada sambungan lagu (boundary jump problem)."*

---

## 📁 Struktur Berkas Repositori Eksperimen
* `EXPERIMENT/Code/baseline_gaur/`:
  * `src/`: Modul inti (data loader, ekstraksi trajektori, model KNN, metrik evaluasi).
  * `experiments/`: Skrip eksekusi batch benchmark 540 playlist.
  * `analyze_intra_song_dynamics.py`: Analisis empiris bukti dinamika 98,11% lagu DEAM.
  * `pyproject.toml` & `requirements.txt`: Ketergantungan dependensi reproducible.

---

## 🔗 Tautan Terkait
- 🔬 **Log Eksperimen:** [[01-Dataset-DEAM-dan-Eksplorasi|Dataset-DEAM]] | [[02-Formulasi-Ekstraksi-Trajectory|Ekstraksi-Trajectory]] | [[03-Replikasi-Baseline-KNN-Gaur|Replikasi-Baseline-KNN]]
- 📝 **Metodologi Naskah:** [[Bab-3-Metodologi]] | [[03-Phase-03-Bab-3-Metodologi-Desain|Phase-03-Bab-3-Metodologi-Desain]]
- 🛡️ **Tanya Jawab Ujian:** [[02-Bank-Pertanyaan-Dosen|Bank-Pertanyaan-Dosen]] | [[03-Speaker-Notes-Dan-Antisipasi-QnA]]
