---
title: "Fase 02: Penulisan Bab 2 Tinjauan Pustaka"
tags:
  - todolist
  - phase-2
  - bab2
  - naskah
status: "TODO"
aliases:
  - Phase-02-Bab-2-Tinjauan-Pustaka
  - Bab 2 Tinjauan Pustaka Todolist
---
# 📚 Fase 02: Penulisan Bab 2 (Tinjauan Pustaka)

> **Tujuan Akhir:** Menghasilkan draf naskah Bab 2 komprehensif pada [[Bab-2-Tinjauan-Pustaka]] berdasarkan 21 paper yang ada di [[Spreadsheet-Studi-Literatur]] dan [[Matriks-Sintesis]].
> **Standar:** Minimal 15 referensi primer, ≥ 70% 3 tahun terakhir (2023–2026), sitasi IEEE murni.

---

## 🎯 Sub-Fase 2.1: Landasan Teori Emosi Musik (2.1)

- [ ] **Langkah 2.1.1 — Model Dimensi Emosi Russell (1980):**
  - Jelaskan teori Circumplex Model of Affect (\cite{russell1980circumplex}).
  - Bedakan sumbu horizontal Valence (senang vs sedih) dan sumbu vertikal Arousal (berenergi vs tenang).
  - Jelaskan keunggulan model dimensional dibanding model kategori diskrit untuk pemodelan lintasan aljabar kontinu.
- [ ] **Langkah 2.1.2 — Sifat Temporal Emosi Musik:**
  - Rujuk temuan Eerola & Anderson (2026) dan Wen et al. (2025): Arousal memiliki inersia temporal tinggi dan korelasi prediksi lebih stabil daripada Valence.
  - Jelaskan perlunya filter peredam bising (*moving average / smoothing*) untuk mengatasi kelambatan persepsi manusia (*perception latency* ~1 detik).

---

## 🎯 Sub-Fase 2.2: Sistem Rekomendasi Musik & Playlist Generation (2.2)

- [ ] **Langkah 2.2.1 — Evolusi Playlist Berbasis Konteks:**
  - Bahas evolusi dari model tradisional (Cardoso et al., 2011) ke sistem industri modern (Bontempelli et al., 2022).
  - Tunjukkan bahwa pengguna kurasi manusia sangat memprioritaskan koherensi transisi sekuensial (Schweiger et al., 2025; Tomasi et al., 2023).
- [ ] **Langkah 2.2.2 — Konsep Mood-Arc (Kurva Suasana Hati):**
  - Definisikan konsep kurva mood: perubahan emosional terarah sepanjang durasi mendengarkan (misal: kurva parabola relaksasi, kurva linear peningkatan energi).
  - Tuliskan formulasi matematis interpolasi waypoint $P_i$.

---

## 🎯 Sub-Fase 2.3: Telaah Mendalam Baseline Gaur & Donnelly (2020/2024) (2.3)

- [ ] **Langkah 2.3.1 — Arsitektur 2-Stage Pipeline Gaur:**
  - Tahap 1: Pencarian $k$ tetangga terdekat di ruang V-A menggunakan KNN.
  - Tahap 2: Re-ranking kandidat berbasis kesamaan fitur audio (Cosine Similarity pada MFCC, tempo, chroma).
- [ ] **Langkah 2.3.2 — Analisis Kritis Kelemahan DMDD:**
  - Dataset DMDD (Delbouys et al., 2018) hanya memiliki label statis rata-rata.
  - Sertakan ilustrasi/skenario: Lagu A (verse tenang $V=0.2$, chorus meledak $V=0.8 
ightarrow$ rata-rata $0.5$) dan Lagu B (konstan $V=0.5$). Dalam sistem Gaur, keduanya dianggap identik.

---

## 🎯 Sub-Fase 2.4: Matriks Komparasi Studi Terkait & Sintesis Gap Riset (2.4)

- [ ] **Langkah 2.4.1 — Susun Tabel Matriks Komparasi 10–15 Paper Utama:**
  - Ambil data dari [[Spreadsheet-Studi-Literatur]] (Gaur, Aljanaki, Eerola, Bontempelli, Tomasi, Schweiger, Wen, Sun, Li, Divekar).
  - Kolom tabel: Penulis/Tahun, Metode, Dataset, Kelebihan, Limitasi, Posisi Riset TA.
- [ ] **Langkah 2.4.2 — Formulasi Hipotesis & Novelty TA:**
  - Nyatakan bagaimana Trajectory Alignment menutup celah *boundary jump* antarlagu.
