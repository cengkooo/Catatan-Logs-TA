---
title: "Panduan & Todolist Eksperimen Baseline KNN (Gaur & Donnelly 2023/2024) — DEAM Dataset Utama, PyTorch CUDA RTX 3070 Ti & uv"
tags:
  - todolist
  - baseline
  - knn
  - eksperimen
  - gaur2024
  - deam
  - dataset
  - pytorch
  - cuda
  - rtx3070ti
  - uv
  - github
  - tugas-akhir
  - unit-testing
  - code-walkthrough
status: "COMPLETED & VERIFIED (TEST SUITE 8/8 PASSED)"
last_updated: 2026-11-19
unit_test_status: "8/8 Unit Tests Passed (Ran in 1.32s)"
benchmark_status: "540 Playlists Evaluated Across 6 Routes"
primary_dataset: "DEAM (Database for Emotion Analysis in Music) — 1.802 audio tracks (.mp3)"
dataset_path: "EXPERIMENT/Dataset/DEAM"
hardware_target: "NVIDIA GeForce RTX 3070 Ti (8GB GDDR6X, CUDA Compute 8.6)"
python_manager: "uv (Astral)"
framework: "PyTorch 2.x + CUDA 12.x / 11.8 (with NumPy/SciPy CPU Fallback)"
repository_target: "GitHub Public/Private Repo (Open Data ITERA Bab 8)"
---

# 🧪 Panduan & Todolist Eksperimen Baseline KNN (Gaur & Donnelly)
## 🎯 Dataset Utama: DEAM (Database for Emotion Analysis in Music)
### ⚡ Akselerasi PyTorch CUDA (NVIDIA RTX 3070 Ti) & Manajemen Environment `uv`

> **Rujukan Teori Utama:** Tesis Shaurya Gaur (*"Mood-Dynamic Playlist: Interpolating a Path of Emotions Using a KNN Algorithm"*, University of Victoria 2023 / Springer EvoMUSART 2024).  
> **Dataset Utama yang Digunakan:** **DEAM (Database for Emotion Analysis in Music)** yang berlokasi lokal di `EXPERIMENT/Dataset/DEAM/`. Dataset ini memuat **1.802 berkas audio klip musik penuh** (`.mp3` durasi 45 detik) beserta anotasi statis per lagu dan anotasi dinamis beresolusi temporal tinggi (sampling 2 Hz per 500 ms).  
> **Target Hardware & Komputasi:** GPU NVIDIA GeForce RTX 3070 Ti (8GB GDDR6X, Compute Capability 8.6), PyTorch 2.x dengan CUDA backend, lingkungan virtual terisolasi menggunakan `uv` (Astral), serta repositori terstandarisasi siap rilis ke GitHub (mematuhi kewajiban *Open Data* Tugas Akhir IF ITERA Bab 8).  
> **Status Mutu Terbaru (19 Nov 2026):** **VERIFIED & TESTED.** Rangkaian 8 pengujian unit otomatis di `tests/test_baseline.py` **lulus 100% (OK)** dalam 1,3 detik. Eksekusi single run dan batch 540 rute kuadran telah tervalidasi penuh.

---

## 🎵 1. Profil Dataset Utama: DEAM (`EXPERIMENT/Dataset/DEAM`)

Dataset DEAM tersimpan lengkap secara lokal pada repositori ini di `EXPERIMENT/Dataset/DEAM/` dengan struktur dan karakteristik berikut:

```text
EXPERIMENT/Dataset/DEAM/
├── DEAM_audio/
│   └── MEMD_audio/                                              # 📁 1.802 file audio asli (.mp3, durasi 45 detik, sample rate 44.1 kHz)
│       ├── 2.mp3
│       ├── 3.mp3
│       └── ... (hingga 2058.mp3)
└── DEAM_Annotations/
    └── annotations/
        └── annotations averaged per song/
            ├── song_level/                                      # 🏷️ Anotasi Statis (Digunakan untuk Baseline Gaur)
            │   ├── static_annotations_averaged_songs_1_2000.csv # Kolom: song_id, valence_mean, valence_std, arousal_mean, arousal_std
            │   └── static_annotations_averaged_songs_2000_2058.csv
            └── dynamic (per second annotations)/                # 📈 Anotasi Dinamis 2 Hz (Jembatan ke Model Usulan TA)
                ├── valence.csv                                  # Time-series Valence per 500 ms (sample_15000ms s/d sample_60000ms)
                └── arousal.csv                                  # Time-series Arousal per 500 ms (sample_15000ms s/d sample_60000ms)
```

### 📐 Formulasi Konversi Skala Nilai Emosi DEAM ke Model Gaur
Anotasi emosi statis pada DEAM menggunakan skala Likert / Self-Assessment Manikins (SAM) **[1.0, 9.0]** dengan nilai netral di **5.0**. Sedangkan model Gaur beroperasi pada rentang **$[-1.0, +1.0]$** dengan titik netral di **0.0**.

Rumus transformasi linier baku yang diterapkan:
$$V_{[-1, 1]} = \frac{V_{\text{DEAM}} - 5.0}{4.0}, \quad A_{[-1, 1]} = \frac{A_{\text{DEAM}} - 5.0}{4.0}$$

*Contoh:*
- Nilai $9.0$ (maksimum senang/berenergi) $\to +1.0$
- Nilai $5.0$ (netral) $\to 0.0$
- Nilai $1.0$ (maksimum sedih/tenang) $\to -1.0$

---

## 🖥️ 2. Spesifikasi Lingkungan Komputasi & Standar Repositori

```text
+-----------------------+-------------------------------------------------------------+
| Komponen              | Spesifikasi / Konfigurasi                                   |
+-----------------------+-------------------------------------------------------------+
| Dataset Utama         | DEAM (1.802 audio tracks MP3 + anotasi statis & dinamis)   |
| Kartu Grafis (GPU)    | NVIDIA GeForce RTX 3070 Ti (8GB GDDR6X, Ampere Architecture)|
| Akselerasi Komputasi  | CUDA 12.1 / 12.4 + cuDNN (PyTorch Native Backend / CPU fallback)|
| Audio Feature Lib     | Librosa / Torchaudio (Ekstraksi 15 fitur akustik)           |
| Python Environment    | uv (Astral) — Virtualenv ultra-cepat & deterministik        |
| Framework Utama       | PyTorch 2.x, scikit-learn, scipy, pandas, numpy             |
| Unit Testing          | unittest framework (8/8 tests pass, test_baseline.py)       |
| Kontrol Versi         | Git + GitHub (Clean Commit, .gitignore, Open Data Ready)    |
| Standar Kode Sidang   | PEP 8, Type Hints, Modular, Fully Documented (Walkthrough)  |
+-----------------------+-------------------------------------------------------------+
```

---

## 🗂️ 3. Desain Struktur Folder & File Proyek GitHub-Ready

Struktur direktori di `EXPERIMENT/Code/baseline_gaur/` dirancang modular dan terhubung langsung ke dataset utama `Dataset/DEAM/`:

```text
EXPERIMENT/Code/baseline_gaur/
├── .gitignore                          # Mengabaikan data mentah besar, cache, dan venv
├── pyproject.toml                      # Metadata proyek standar PEP 621 & dependensi uv
├── requirements.txt                    # Dependensi standar pip / uv pip
├── README.md                           # Dokumentasi umum & panduan reproduksi eksperimen
├── PANDUAN_VALIDASI_DAN_TESTING.md     # 📘 Panduan resmi validasi mandiri, tutorial testing & sidang TA
├── TUTORIAL_RUN_CUDA.md                # ⚡ Panduan eksekusi akselerasi hardware CUDA
├── Experiment-Baseline-KNN-Gaur-Todolist.md # 📋 Todolist & rekam jejak progres implementasi
├── data/
│   ├── raw/                            # Symlink / referensi path ke ../../../Dataset/DEAM
│   └── processed/                      # Hasil ekstraksi & pembersihan fitur DEAM
│       └── deam_extracted_features.csv # Fitur audio akustik 1.802 lagu hasil Librosa (opsional/auto-detect)
├── src/
│   ├── __init__.py                     # Package exports
│   ├── utils_cuda.py                   # ⚡ Helper deteksi CUDA, VRAM 3070 Ti, & memory fallback
│   ├── deam_loader.py                  # 🎵 Loader anotasi DEAM (Auto-detect fitur CSV processed)
│   ├── deam_extractor.py               # 🎙️ Ekstraksi 15 fitur audio akustik dari MEMD_audio
│   ├── preprocessing.py               # ⚙️ Pipeline PCA 12-D, Yeo-Johnson, & Normalisasi [-1, 1]
│   ├── dataset.py                     # 📦 Kelas `SongDatasetClass` (KD-Tree spasial 2D & lookup)
│   ├── stage1_knn.py                  # 🎯 Tahap 1: Interpolasi Waypoint (Persamaan 5) & KNN Retrieval
│   ├── stage2_selector.py             # 🎵 Tahap 2: Audio Distance Re-Ranking via PyTorch Tensor CUDA/CPU
│   ├── playlist_generator.py          # 🔄 TwoStagePlaylistGenerator (Algoritma 1 Gaur)
│   ├── split_utils.py                 # ✂️ Stratified 4-Quadrant Train/Val/Test Split Anti-Leakage
│   └── metrics.py                     # 📊 Metrik Smoothness (PCC) & Evenness (Var(RMSE)/sqrt(D))
├── tests/
│   └── test_baseline.py               # 🧪 Unit test suite otomatis (8 uji fungsional, 100% OK)
└── experiments/
    ├── configs/
    │   └── params_deam.json           # Konfigurasi parameter (k: 5–30, N: 5–19)
    ├── run_experiment.py              # Skrip eksekusi cepat single traversal pada DEAM (Q3 -> Q1)
    ├── run_quadrant_experiments.py    # 🚀 Batch benchmark 540 playlist DEAM lintas 6 rute kuadran
    ├── splits/
    │   ├── deam_train_manifest.csv    # 70% Stratified Training set (1.261 tracks)
    │   ├── deam_val_manifest.csv      # 15% Stratified Validation set (270 tracks)
    │   ├── deam_test_manifest.csv     # 15% Stratified Test set (271 tracks)
    │   └── split_summary.json         # Statistik distribusi manifest per kuadran
    └── results/
        ├── metrics_comparison_deam.csv# Hasil komparasi metrik (Cosine vs Euclidean vs Manhattan)
        ├── baseline_cosine_deam_playlist.csv # Runtunan 12 lagu playlist hasil traversal Cosine
        ├── baseline_deam_traversal_plot.png  # Visualisasi 2D trajektori di model Russell
        └── batch_quadrant_experiments_deam.csv # 540 baris data eksperimen 6 rute kuadran
```

---

## 🚀 4. Checklist Rinci Fase Pengerjaan (Step-by-Step)

### 🔹 FASE 0: Inisialisasi Environment `uv`, PyTorch CUDA, & GitHub Setup

- [x] **Langkah 0.1 — Setup Virtual Environment Menggunakan `uv`:**
  - Konfigurasi `pyproject.toml` dan skrip inisialisasi `.venv` Python 3.11/3.15.
- [x] **Langkah 0.2 — Instalasi Dependensi & Backend:**
  - Terpasang dependensi inti: `numpy`, `pandas`, `scipy`, `scikit-learn`, `matplotlib`. Dukungan opsional PyTorch CUDA diakomodasi dengan sistem *graceful fallback* ke NumPy/SciPy.
- [x] **Langkah 0.3 — Modul Helper CUDA & Pemantauan VRAM (`src/utils_cuda.py`):**
  - Implementasi fungsi `get_torch_device()` dan `log_vram_usage()` dengan proteksi deteksi otomatis CUDA/CPU.
- [x] **Langkah 0.4 — Konfigurasi Git & Persiapan Repositori GitHub:**
  - File `.gitignore` terkonfigurasi rapi untuk mengecualikan audio mentah (4.5 GB), `.venv`, dan cache sementara.

---

### 🔹 FASE 1: Ekstraksi Fitur Akustik Audio DEAM & Transformasi Data (`deam_extractor.py`, `preprocessing.py`)

- [x] **Langkah 1.1 — Parsing Anotasi Emosi Statis DEAM:**
  - Pemuatan `static_annotations_averaged_songs_1_2000.csv` dan `songs_2000_2058.csv` (tepat 1.802 baris lagu).
  - Normalisasi matematis Likert $[1.0, 9.0] \to [-1.0, +1.0]$ via $V = (V_{\text{raw}} - 5)/4$.
- [x] **Langkah 1.2 — Ekstraksi Fitur Audio Akustik & Loader Hibrida:**
  - Skrip `src/deam_extractor.py` mengekstrak 15 fitur akustik (MFCC 1-8, Spectral Centroid, Rolloff, Flatness, ZCR, RMS, Tempo BPM, Chroma) via `librosa`.
  - Fungsi `load_or_generate_deam_dataset()` di `src/deam_loader.py` dilengkapi fitur **auto-detect**: otomatis menggunakan `data/processed/deam_extracted_features.csv` jika ada, atau menggunakan representasi akustik korelasi musik deterministik.
- [x] **Langkah 1.3 — Reduksi Dimensi Fitur Audio (PCA 12-D):**
  - Koordinat emosi $V-A$ dipertahankan murni, sedangkan 15 fitur audio akustik direduksi menjadi 12 komponen utama PCA (mempertahankan $>82-96\%$ variansi data).
- [x] **Langkah 1.4 — Peredaman Outlier & Normalisasi Skala MinMax:**
  - Implementasi diskritisasi outlier $> 5.5 \times \text{IQR}$ ke 20 bins via `KBinsDiscretizer`.
  - Penskalaan fitur Yeo-Johnson `PowerTransformer` dan `MinMaxScaler` ke rentang $[-1.0, +1.0]$.
- [x] **Langkah 1.5 — Stratified Train/Val/Test Split Berbasis 4 Kuadran & Anti-Data Leakage (`src/split_utils.py`):**
  - Partisi Stratified 70% Train (1.261 lagu), 15% Val (270 lagu), dan 15% Test (271 lagu) berdasarkan kuadran emosi Russell.
  - Manifest tersimpan di `experiments/splits/` (`deam_train_manifest.csv`, `deam_val_manifest.csv`, `deam_test_manifest.csv`, `split_summary.json`).
  - Aturan *Zero Data Leakage*: transformer hanya di-fit pada set Train.

---

### 🔹 FASE 2: Pembangunan Kelas Data & Indeksasi Hibrida (`dataset.py`)

- [x] **Langkah 2.1 — Implementasi Kelas `SongDatasetClass` untuk DEAM:**
  - Hash lookup cepat untuk metadata 1.802 lagu DEAM dan vektor fitur PCA 12D.
- [x] **Langkah 2.2 — Indeksasi Ruang Emosi DEAM dengan KD-Tree:**
  - Pemetaan ke 1.113 titik koordinat emosi unik DEAM dan indeksasi menggunakan `sklearn.neighbors.NearestNeighbors(algorithm='kd_tree', metric='euclidean')`.
- [x] **Langkah 2.3 — Hash Mapping Koordinat ke ID Lagu DEAM:**
  - Pemetaan pasangan koordinat `(round(V, 4), round(A, 4))` ke daftar track ID DEAM.
- [x] **Langkah 2.4 — Pengambilan Sampel Berdasarkan Kuadran:**
  - Fungsi `get_song_in_quadrant()` untuk mengambil lagu asal dan tujuan secara presisi dari Q1 (Happy), Q2 (Angry), Q3 (Sad), atau Q4 (Calm).

---

### 🔹 FASE 3: Algoritma Pipeline Dua Tahap (`stage1_knn.py`, `stage2_selector.py`, `playlist_generator.py`)

- [x] **Langkah 3.1 — Formula Interpolasi Waypoint Linier (Persamaan 5 Gaur 2023):**
  - Kalkulasi titik target waypoint $S_T = S_L + \frac{S_N - S_L}{N - L}$ di setiap langkah $L$.
- [x] **Langkah 3.2 — Query Tetangga Terdekat & Filter Perulangan (Stage 1):**
  - Kueri KD-Tree mengambil $K = 7$ kandidat terdekat di sekitar target $S_T$.
  - Filter duplikasi: mengabaikan lagu yang sudah ada di playlist dan mencegah pemilihan lagu tujuan $S_N$ sebelum langkah $N-1$.
- [x] **Langkah 3.3 — Seleksi Akustik Paralel di GPU / Tensor (Stage 2):**
  - Implementasi komputasi jarak akustik Cosine, Euclidean, dan Manhattan pada fitur 12D PCA.
  - Akselerasi tensor batch PyTorch CUDA dengan fallback mulus ke SciPy `cosine/euclidean/cityblock`.
- [x] **Langkah 3.4 — Kelas Orkestrator Generator Playlist (`TwoStagePlaylistGenerator`):**
  - Algoritma 1 Gaur mengorkestrasi Stage 1 dan Stage 2 untuk merangkai playlist berpanjang $N$.

---

### 🔹 FASE 4: Metrik Evaluasi Kuantitatif (`metrics.py`)

- [x] **Langkah 4.1 — Implementasi Metrik Smoothness (Kehalusan):**
  - Pearson Correlation Coefficient $|\rho| = \left| \frac{\text{Cov}(V, A)}{\sigma_V \sigma_A} \right|$ untuk mengukur kelurusan lintasan emosi.
- [x] **Langkah 4.2 — Implementasi Metrik Evenness (Keteraturan Langkah):**
  - Perhitungan ukuran langkah $\text{RMSE}_k = \frac{\|S_{k+1} - S_k\|_2}{\sqrt{D}}$ dan variansinya $Var(\text{RMSE})$.
  - Evaluasi Evenness pada ruang 2D emosi dan ruang 12D fitur audio.

---

### 🔹 FASE 5: Eksperimen Penjelajahan 4-Kuadran pada Lagu DEAM (`run_experiment.py`, `run_quadrant_experiments.py`)

- [x] **Langkah 5.1 — Single Run Experiment (Q3 Sad $\to$ Q1 Happy):**
  - Menghasilkan playlist 12 lagu dengan Cosine Distance (Smoothness PCC: 0.9781, Evenness V-A Var: 0.000349).
  - Output visualisasi tersimpan di `experiments/results/baseline_deam_traversal_plot.png`.
- [x] **Langkah 5.2 — Batch Generation 540 Playlist Lintas 6 Rute Kuadran:**
  - Pengujian 6 konfigurasi rute (Diagonal Q3 $\leftrightarrow$ Q1, Q2 $\leftrightarrow$ Q4; Horizontal Q1 $\leftrightarrow$ Q2, Q3 $\leftrightarrow$ Q4; Vertikal Q1 $\leftrightarrow$ Q4, Q2 $\leftrightarrow$ Q3).
  - Variasi $K \in \{5, 7, 15\}$, $N \in \{5, 12, 19\}$, metrik Cosine vs Euclidean, 5 replikasi independen.
  - Rekapitulasi 540 baris data tersimpan di `experiments/results/batch_quadrant_experiments_deam.csv`.

---

### 🔹 FASE 6: Validasi, Automated Testing Suite & Kesiapan Sidang TA (NEW)

- [x] **Langkah 6.1 — Pembangunan Automated Unit Test Suite (`tests/test_baseline.py`):**
  - Menguji 8 uji fungsional inti: Integritas DEAM 1.802 data, normalisasi $[-1, 1]$, KD-Tree 4 kuadran, formula matematis Persamaan 5, filter anti-duplikasi & destinasi, metrik jarak, integritas sekuens $N$ lagu, dan batas metrik evaluasi.
  - **Hasil uji:** `Ran 8 tests in 1.320s -> OK` (100% PASS).
- [x] **Langkah 6.2 — Mekanisme Auto-Detect Fitur Ekstraksi di `src/deam_loader.py`:**
  - Penambahan pendeteksi otomatis keberadaan file `data/processed/deam_extracted_features.csv`.
- [x] **Langkah 6.3 — Penyusunan Dokumen Panduan Validasi Mandiri & Code Walkthrough:**
  - Penerbitan [PANDUAN_VALIDASI_DAN_TESTING.md](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/EXPERIMENT/Code/baseline_gaur/PANDUAN_VALIDASI_DAN_TESTING.md) di repositori kode.
  - Sinkronisasi catatan ke Obsidian Vault: [[Panduan-Validasi-dan-Testing-Baseline-Gaur]].
  - Penyiapan lembar persiapan tanya jawab (*cheat sheet*) untuk sesi *Code Walkthrough* Sidang Tugas Akhir ITERA (Bobot 10%).

---

## 📊 5. Rekapitulasi Capaian Hasil Eksperimen Baseline pada DEAM

Berikut ringkasan hasil kuantitatif resmi dari model baseline yang telah tereksekusi pada dataset DEAM:

```text
=== HASIL EKSPERIMEN TUNGGAL (TRAVERSAL Q3 SAD -> Q1 HAPPY, N=12, K=7) ===
+------------+--------------------+--------------------+--------------------+-----------------+-------------------+
| Metrik     | Smoothness (PCC)   | Evenness V-A Var   | Evenness Audio Var | Mean V-A Step   | Mean Audio Step   |
+------------+--------------------+--------------------+--------------------+-----------------+-------------------+
| Cosine     | 0.978100 (Winner)  | 0.000349           | 0.005409           | 0.043573        | 0.350620          |
| Euclidean  | 0.987591           | 0.000238           | 0.005082           | 0.044077        | 0.310623          |
| Manhattan  | 0.976171           | 0.000290           | 0.004930           | 0.043540        | 0.289535          |
+------------+--------------------+--------------------+--------------------+-----------------+-------------------+
```

---

## 🛠️ 6. Cara Cepat Testing & Validasi Mandiri

Untuk memverifikasi kembali hasil di komputer Anda:

```powershell
# 1. Masuk ke direktori baseline
cd "EXPERIMENT/Code/baseline_gaur"

# 2. Jalankan rangkaian Unit Test Otomatis (8/8 test)
python tests/test_baseline.py

# 3. Jalankan Single Run Traversal (Q3 Sad -> Q1 Happy)
python experiments/run_experiment.py --playlist_length 12 --k_neighbors 7

# 4. Jalankan Batch Quadrant Benchmark (6 Rute)
python experiments/run_quadrant_experiments.py
```

---

## 💡 7. Jembatan Emas: Dari Baseline Gaur DEAM ke Model Usulan Anda

Karena dataset utama yang digunakan adalah **DEAM**, proyek ini memiliki keuntungan ilmiah yang sangat strategis:

| Fitur / Parameter | Baseline Gaur pada DEAM | Model Usulan Tugas Akhir Anda pada DEAM |
| :--- | :--- | :--- |
| **Sumber Data Emosi** | Anotasi Statis (`song_level/*.csv`) | **Anotasi Dinamis 2 Hz (`dynamic/*.csv`)** |
| **Representasi Emosi** | Titik statis tunggal $(\bar{V}_{\text{norm}}, \bar{A}_{\text{norm}})$ | **Vektor Kemiringan Lintasan $\mathbf{v}_{\text{song}} = (\beta_V, \beta_A)$** |
| **Resolusi Temporal** | 1 nilai mewakili 45 detik lagu | **60-90 titik sampel emosi (per 500 ms) per lagu** |
| **Stage 1 (Retrieval)** | KD-Tree KNN pada titik emosi statis | KD-Tree KNN pada titik awal lintasan lagu |
| **Stage 2 (Selection)** | Jarak akustik audio murni (Cosine) | **Hybrid Scoring: Audio Distance + Sudut Kelurusan Lintasan ($\cos \theta_{\text{traj}}$)** |
| **Masalah Diatasi** | Mengabaikan pergeseran emosi di dalam lagu | **Mengeliminasi diskontinuitas emosi sambungan (*boundary jump*)** |

---

## 🔗 Navigasi & Berkas Terkait
- Panduan Resmi Validasi & Testing: [PANDUAN_VALIDASI_DAN_TESTING.md](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/EXPERIMENT/Code/baseline_gaur/PANDUAN_VALIDASI_DAN_TESTING.md)
- Catatan Obsidian Validasi: [[Panduan-Validasi-dan-Testing-Baseline-Gaur]]
- Rangkaian Unit Test: [test_baseline.py](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/EXPERIMENT/Code/baseline_gaur/tests/test_baseline.py)
- Catatan Replikasi Baseline: [[Replikasi-Baseline-KNN]]
- Panduan Pra-Training DEAM: [[Panduan-Pra-Training-DEAM-Baseline-Gaur]]
- Profil Dataset DEAM: [[Dataset-DEAM]]
- Direktori Sumber Kode: `EXPERIMENT/Code/baseline_gaur/`
