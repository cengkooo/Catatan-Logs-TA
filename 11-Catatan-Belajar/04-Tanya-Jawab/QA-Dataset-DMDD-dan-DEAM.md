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

### 🔗 Catatan Terkait
- [[00-Index-Catatan]]
- [[02-Aljanaki2017-Developing-Benchmark-DEAM]]
