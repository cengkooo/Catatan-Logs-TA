---
title: "Spreadsheet: Penjelasan Dataset (Komparasi 47 Dataset MER & Rekomendasi DEAM)"
tags:
  - spreadsheet-mirror
  - penjelasan-dataset
  - benchmark-deam
  - tugas-akhir
source_sheet_id: "1ydH6Cnd-DG08dG2ix7CgPogitx_rmPxgzt0NudJbRHk"
---

# 📑 Mirror Spreadsheet: PENJELASAN DATASET

> **ID Spreadsheet Asli:** [1ydH6Cnd-DG08dG2ix7CgPogitx_rmPxgzt0NudJbRHk](https://docs.google.com/spreadsheets/d/1ydH6Cnd-DG08dG2ix7CgPogitx_rmPxgzt0NudJbRHk)  
> **Terdiri dari 4 Tab Utama:**
> 1. `1_TLDR_DAN_RANKING` (Survei 47 dataset MER 2007–2025, eliminasi 30 dataset, Tier 1 vs Tier 2)
> 2. `2_DETAIL_DATASET` (Spesifikasi mendalam 6 dataset kandidat teratas)
> 3. `3_ANALISIS_SWOT` (Matriks perbandingan head-to-head parameter teknis)
> 4. `4_SKENARIO_EKSPERIMEN` (Panduan implementasi metodologis Bab 2 & Bab 3)

---

## 📊 TAB 1: TLDR & Ranking Survei 47 Dataset MER (2007–2025)

Berdasarkan telaah komprehensif terhadap 47 dataset Music Emotion Recognition (*Kang & Herremans, arXiv 2024*), mayoritas korpus akademis hanya berfokus pada klasifikasi kategori diskrit atau kuadran emosi.

Hanya segelintir kecil dataset yang memenuhi **3 Pilar Teknis Tugas Akhir**:
1. **Model Emosi 2D Kontinu Russell (Valence & Arousal):** Diperlukan untuk kalkulus jarak KNN pada Tahap 1 Gaur (2024).
2. **File Audio Digital Asli (MP3/WAV):** Diperlukan untuk ekstraksi fitur akustik Librosa pada Tahap 2.
3. **Anotasi Dinamis Berkelanjutan (Time-Continuous):** Kunci kebaruan (*novelty*) inovasi *Trajectory Alignment* Tugas Akhir.

### 🚫 Justifikasi Eliminasi 30 Dataset
* **30 Dataset Kategorikal / Diskrit (GUGUR):**
  *Contoh:* XMIDI (2025), EMMA (2024), MERGE (2024), Popular Hooks (2024), Affolter (2024), TROMPA-MER (2023), EmoMV (2023), Indonesian Song (2023), Music-Mouv (2023), YM2413-MDB (2022), EMOPIA (2021), MER500 (2020), MTG-Jamendo (2019), Turkish Music (2019), RAVDESS (2018), 4Q-emotion (2018), Emotify (2016), Malheiro (2016), CAL500exp (2014), Panda (2013), CAL500 (2007), MoodsMIREX (2007).
  *Alasan:* Operasi interpolasi linier dan jarak Euclidean mustahil dilakukan secara matematis pada string label kategori atau kuadran.
* **Dataset Format Simbolik / MIDI Murni (GUGUR):**
  *Contoh:* VGMIDI (2019), XMIDI (2025). Tidak memiliki gelombang akustik timbre nyata tanpa disintesis.
* **Dataset Teks Lirik Saja (GUGUR):**
  *Contoh:* MoodyLyrics (2017). Tidak memiliki modalitas suara.

---

## 🏆 TAB 2: Detail Dataset Kandidat (Tier 1 & Tier 2)

### 🥇 TIER 1: Paling Relevan & Kompatibel (Time-Continuous + Russell 2D)

| # | Nama Dataset | Tahun | Format & Ukuran | Jumlah Sampel | Resolusi Anotasi | Rekomendasi TA |
| :---: | :--- | :---: | :--- | :--- | :--- | :--- |
| **1** | **DEAM** | **2018** | **MP3 (1,4 GB)** | **2.058 lagu** | **Dinamis 2 Hz (0,5s) + Statis** | **DATASET UTAMA (Primary)** |
| 2 | **PMEmo** | 2018 | MP3 (1,3 GB) | 794 lagu penuh | Dinamis 2 Hz + Statis (EDA) | VALIDASI SILANG |
| 3 | **MERP** | 2022 | WAV | 54 lagu penuh | Dinamis 10 Hz (0,1s) | EKSPLORASI MIKRO |
| 4 | **ENSA** | 2023 | MP3 | 60 lagu penuh | Dinamis per struktur lagu | STUDI STRUKTUR |
| 5 | **emoMusic** | 2013 | MP3 | 1.000 klip (45s) | Dinamis 2 Hz | Cikal bakal DEAM |
| 6 | **MoodSwings** | 2008/11 | MP3 | 240 klip (15s) | Dinamis 1 Hz | Sampel terlalu sedikit |

### 🥈 TIER 2: Relevan Pendukung (Baseline-Only Statis)
Dataset dengan koordinat V-A kontinu tetapi hanya bernilai statis rata-rata per lagu (cocok untuk mereplikasi kelemahan baseline Gaur):
* **SiTunes (2024):** 300 lagu WAV, dimensional statis.
* **MusAV (2022):** 2.092 lagu preview Spotify, 1.404 genre.
* **HKU956 (2022):** 956 lagu MP3, rentang V-A [-10, 10].
* **MuSe (2021):** 90.001 lagu, V-A-D dari tag Last.fm.
* **CCMED-WCMED (2020):** 800 lagu WAV musik klasik Barat & China.
* **Music4all (2020):** 109.269 klip WAV, fitur Spotify.
* **DMDD (2018):** 18.644 lagu (*Dataset asli yang dipakai Gaur & Donnelly 2024*).

---

## 🥊 TAB 3: Matriks Analisis SWOT & Perbandingan Head-to-Head

| Parameter Kritis | DEAM (2018) | PMEmo (2018) | MERP (2022) | DMDD (Gaur 2024) |
| :--- | :--- | :--- | :--- | :--- |
| **Tahun Rilis** | 2018 | 2018 | 2022 (Terbaru) | 2018 |
| **Format Audio** | MP3 (1,4 GB) | MP3 (1,3 GB) | WAV | Audio / Stream |
| **Durasi Lagu** | 45 detik (standar) | Lagu utuh (*full*) | Lagu utuh | Lagu utuh |
| **Jumlah Lagu** | **2.058 lagu** | 794 lagu | 54 lagu | 18.644 lagu |
| **Model Emosi** | 2D Russell Kontinu | 2D Russell Kontinu | 2D Russell Kontinu | 2D Russell Kontinu |
| **Anotasi Dinamis** | **YA (2 Hz / per 0,5s)** | **YA (2 Hz / per 0,5s)** | YA (10 Hz / per 0,1s) | **TIDAK (Statis)** |
| **Metode Rating** | Crowdsource (10 rater) | 457 subjek manusia | 452 partisipan | Ekstraksi Last.fm |
| **Kepadatan KNN** | **Sangat Baik (densitas pas)** | Cukup | Kurang (terlalu sedikit)| Sangat Padat |
| **Uji Trajectory TA**| **SANGAT IDEAL** | **SANGAT IDEAL** | Eksplorasi Mikro | **TIDAK BISA** |
| **Kesimpulan Peran**| **DATASET UTAMA** | **VALIDASI SILANG** | **STUDI KASUS BARU** | **BASELINE EKSISTING** |

### Analisis SWOT Pemilihan DEAM sebagai Dataset Utama:
* **Strengths (Kekuatan):**
  - Anotasi kontinu frekuensi 2 Hz memungkinkan kalkulasi slope regresi dinamis.
  - Jumlah 2.058 lagu memberikan ruang pencarian KNN yang seimbang (tidak over-sparse dan tidak over-clustered).
  - Lisensi Creative Commons bebas hak cipta, aman untuk penelitian dan repositori terbuka ITERA.
* **Weaknesses (Kelemahan):**
  - Mayoritas klip berdurasi 45 detik (segmen representatif), bukan lagu utuh 3-4 menit.
* **Opportunities (Peluang TA):**
  - Memecahkan kelemahan *static-point matching* Gaur & Donnelly (2024) yang menjadi celah riset utama.
* **Threats (Tantangan):**
  - Keterlambatan persepsi manusia (*perception latency* ~1 detik) pada anotasi dinamis memerlukan pembersihan sinyal (*temporal smoothing*).

---

## 🎯 TAB 4: Skenario Eksperimen untuk Bab 2 & Bab 3

1. **Bab 3 (Metodologi Penelitian):**
   Tetapkan **DEAM (2018)** sebagai dataset eksperimen utama. Cantumkan justifikasi ilmiah bahwa pemilihan ini didasarkan pada perbandingan terhadap 47 dataset MER terkini (*Kang & Herremans, 2024*), di mana DEAM memiliki rasio keterpenuhan terbaik antara kecukupan sampel KNN (2.058 track) dan ketersediaan anotasi dinamis 2 Hz.
2. **Bab 4 (Pengujian & Pembahasan):**
   Gunakan **PMEmo (2018)** sebagai dataset uji silang (*cross-dataset validation*) untuk membuktikan bahwa metrik kelancaran transisi trajectory alignment konsisten pada lagu berdurasi utuh.
3. **Bab 2 (Tinjauan Pustaka):**
   Sitasi dataset mutakhir seperti **MERP (2022)**, **MusAV (2022)**, dan **SiTunes (2024)** untuk membuktikan kebaruan pustaka bahwa penelitian dimensi afektif musik terus aktif hingga tahun 2024–2026.
