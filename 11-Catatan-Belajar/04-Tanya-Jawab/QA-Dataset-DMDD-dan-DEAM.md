---
title: "Dataset DMDD (Deezer Mood Detection Dataset) yang Dipakai Baseline Gaur"
tags:
  - note/tanya-jawab
  - learning-qa
  - dataset
  - dmdd
topik: "Dataset DMDD dan DEAM"
status: "solid"
rujukan_paper:
  - "[[14-Delbouys2018-Music-Mood-Audio-Lyrics]]"
  - "[[01-Gaur2023-Mood-Dynamic]]"
  - "[[02-Aljanaki2017-Developing-Benchmark-DEAM]]"
created: 2026-11-28
updated: 2026-11-28
---

# 💬 Dataset DMDD (Deezer Mood Detection Dataset) yang Dipakai Baseline Gaur

- **Topik:** `Dataset DMDD dan DEAM`
- **Status Pemahaman:** `solid`

---

## ❓ Pertanyaan #1
> Minta tautan dataset DMDD (*Deezer Mood Detection Dataset*) yang dipakai oleh Gaur & Donnelly.

### 💡 Jawaban

Tautan resmi repositori **Deezer Mood Detection Dataset (DMDD)** (Delbouys et al., ISMIR 2018) tersedia di GitHub Deezer Research:

- **Repositori Resmi GitHub:** [https://github.com/deezer/deezer_mood_detection_dataset](https://github.com/deezer/deezer_mood_detection_dataset)

#### Catatan Penting Isi & Keterbatasan DMDD
1. **Isi Berkas:** Menyediakan pemetaan metadata untuk **18.644 lagu**, berupa **Deezer Track IDs** dan **Million Song Dataset (MSD) IDs** beserta nilai **Valence** dan **Arousal** statis per lagu.
2. **Tidak Ada Audio Mentah Langsung:** Karena pembatasan hak cipta, repositori tersebut tidak menyertakan berkas audio MP3 atau teks lirik mentah. Peneliti harus menggunakan MSD ID atau Deezer API untuk mengambil metadata/pratinjau audio.
3. **Alasan Mengapa TA Anda Memilih DEAM, Bukan DMDD:** DMDD hanya menyimpan **satu nilai rata-rata statis** per lagu (diturunkan dari tag Last.fm), sehingga tidak memiliki deret waktu intra-lagu (2 Hz) seperti **DEAM** untuk memodelkan transisi *intro-to-outro*.

### 📚 Referensi
- GitHub Resmi Deezer Research: `https://github.com/deezer/deezer_mood_detection_dataset`
- [[14-Delbouys2018-Music-Mood-Audio-Lyrics]] — Bedah kritis paper Delbouys et al. (2018) di repo.
- [[01-Gaur2023-Mood-Dynamic]] — Penggunaan DMDD pada baseline Gaur & Donnelly.
- `Catatan-Memori/Catatan-Memori-Logs/04-Literatur-Review/Spreadsheet-Studi-Literatur.md`

---

## ❓ Pertanyaan #2
> Apa perbandingan DEAM vs. DMDD?

### 💡 Jawaban

Perbedaan mendasar antara **DEAM** (*Database for Emotion Analysis in Music*, Aljanaki et al., 2017) dan **DMDD** (*Deezer Mood Detection Dataset*, Delbouys et al., 2018) bukan sekadar jumlah lagunya, melainkan **resolusi waktu anotasi emosi** dan **ketersediaan berkas audio terbuka**.

| Aspek Perbandingan | **DEAM** (Dataset Utama TA Anda) | **DMDD** (Dataset Baseline Gaur & Donnelly) |
| :--- | :--- | :--- |
| **Penulis & Tahun** | Aljanaki et al. (2017 / rilis 2018) | Delbouys et al. (ISMIR 2018, Deezer Research) |
| **Jumlah Sampel** | **1.802 klip standar (45 detik)** beranotasi dinamis 2 Hz (total korpus rilis DEAM tercatat 2.058 lagu) | **18.644 lagu** (pemetaan ID Deezer & MSD) |
| **Model Emosi** | 2D Kontinu Russell (*Valence & Arousal*) | 2D Kontinu Russell (*Valence & Arousal*) |
| **Resolusi Anotasi** | **Dinamis 2 Hz** (1 nilai V-A setiap 0,5 detik) + nilai statis | **Statis tunggal** (hanya 1 pasang nilai $\bar{v}, \bar{a}$ per lagu) |
| **Sumber / Metode Label** | Anotasi langsung pendengar manusia via *crowdsourcing* (10 rater per lagu) | Diturunkan secara otomatis dari tag sosial **Last.fm** |
| **Ketersediaan Audio & Lisensi** | **Tersedia langsung (MP3, 1,4 GB)** dengan lisensi terbuka Creative Commons (FMA & Jamendo) | **Tidak menyertakan file audio/lirik langsung** karena hak cipta (hanya menyediakan ID) |
| **Kesesuaian untuk *Trajectory Alignment*** | **Sangat Ideal:** Bisa menghitung segmen *intro*, *outro*, vektor arah $\vec{\mathbf{t}}_k$, dan *Boundary Jump Cost* ($\mathcal{BJC}$) | **Tidak Bisa:** Tidak punya data perubahan emosi intra-lagu, sehingga memicu *The Boundary Jump Problem* |
| **Tantangan Teknis** | Durasi klip standar 45 detik (15 detik awal dipotong karena fase adaptasi manusia) dan perlu *moving average smoothing* untuk meredam *perceptual latency* | Hanya cocok untuk mereplikasi kelemahan *static-point matching* |

#### Inti yang Perlu Dipegang saat Sempro
1. **DMDD menang di kuantitas (18.644 lagu), tetapi buta waktu (statis):** Karena hanya berasal dari tag Last.fm satu nilai per lagu, model seperti Gaur & Donnelly (2020) yang memakai DMDD tidak bisa melihat apakah awal dan akhir lagu punya emosi yang bertolak belakang.
2. **DEAM menang di kualitas temporal (dinamis 2 Hz) dan keterbukaan data:** Meski jumlah klip standarnya lebih kecil (1.802 klip 45 detik), DEAM adalah standar emas MIR untuk dinamika emosi karena dinilai langsung oleh manusia per 0,5 detik dan audionya legal untuk *open data* repositori ITERA.

---

### 🔗 Catatan Terkait
- [[00-Index-Catatan]]
- [[02-Aljanaki2017-Developing-Benchmark-DEAM]]
