---tier: "Tier 1: Core Foundation & Baseline Acuan"

title: "Bedah Kritis: The Impact of Playlist Characteristics on Coherence in User-Curated Playlists"
author: "Harald Schweiger, Emilia Parada-Cabaleiro, & Markus Schedl"
year: 2025
citekey: "schweiger2025playlist"
venue: "EPJ Data Science, Vol. 14, Article 24 (Springer Nature)"
quartile: "Q1 Scopus / ISI Web of Science (Top 10% Data Science)"
dataset: "Spotify Million Playlist Dataset (MPD) & AOTM (Ribuan Playlist Kurasi Manusia)"
metode: "Sequential Ordering Analysis + Transition Distance Metrics + Multi-Feature Coherence Measurement"
gap_utama: "Konsep koherensi playlist selama ini didefinisikan secara samar tanpa formulasi metrik transisi sekuensial yang terstandarisasi."
tags:
  - literatur
  - paper-review
  - playlist-coherence
  - sequential-transition
  - epj-data-science
status: "audited"
aliases:
  - Schweiger2025-Playlist-Coherence
  - Playlist Coherence Schweiger
---
# 📖 Bedah Kritis: Koherensi Playlist Musik (Schweiger et al., 2025)
## *The Impact of Playlist Characteristics on Coherence in User-Curated Music Playlists*

> **Objek Bedah:** Jurnal Q1 Springer EPJ Data Science (130 KB text)  
> **Kedudukan dalam TA:** **Rujukan Teoretis Evaluasi Metrik Koherensi Transisi Playlist (Bab II Subbab 2.4)**

---

## 🧭 Step 0: Metadata dan Konteks
* **Penulis & Afiliasi:** Harald Schweiger, Emilia Parada-Cabaleiro, Markus Schedl (Institute of Computational Perception, Johannes Kepler University Linz, Austria).
* **Venue & Reputasi:** *EPJ Data Science* (Springer Open, 2025), salah satu jurnal data science paling bereputasi di Eropa (Impact Factor 3.6, Q1).
* **Tujuan Membaca:** Mengadopsi landasan teoretis bahwa urutan sekuensial (*track ordering*) antarlagu bertetangga adalah penentu utama kenyamanan pendengar dalam menikmati playlist.

---

## 📑 Step 1: Abstrak (Bedah 5 Komponen)
1. **Konteks & Masalah:** Pembuatan playlist musik adalah tugas krusial dalam MIR. Riset sebelumnya berfokus pada diversitas dan popularitas lagu, namun mengabaikan faktor koherensi transisi.
2. **Gap yang Diklaim:** Konsep koherensi playlist (*smooth transition between tracks*) tidak memiliki formulasi matematis yang terstandarisasi dan minim kajian empiris pada playlist nyata.
3. **Pendekatan:** Merumuskan definisi formal pengukuran koherensi berbasis urutan sekuensial (*sequential ordering*) pada dimensi audio, genre, dan emosi.
4. **Hasil Kuantitatif Konkret:**
   * Menganalisis jutaan playlist kurasi manusia pada dataset Spotify MPD.
   * Membuktikan bahwa manusia **secara konsisten memprioritaskan transisi halus antartrek bertetangga ($L_i 
ightarrow L_{i+1}$)** dibanding kesamaan global seluruh isi playlist.
   * Lonjakan jarak transisi (*transition jumps*) yang melebihi ambang batas toleransi terbukti menjadi penyebab utama pengguna menekan tombol *skip* lagu.
5. **Implikasi:** Metrik transisi sekuensial (seperti *Smoothness*) adalah indikator paling valid dalam menilai kualitas playlist buatan AI.

---

## 💡 Step 9: Sintesis Pencapaian 3 Kalimat
1. **Fakta Terbukti:** Manusia secara alami menyusun playlist dengan meminimalkan jarak lompatan fitur antarlagu yang berdekatan (*local sequential coherence*).
2. **Lompatan SOTA:** Menyediakan kerangka matematis pertama yang membedah korelasi karakteristik playlist (panjang trek, diversitas artis) terhadap koherensi transisi.
3. **Kegunaan Praktis:** Memberikan justifikasi ilmiah mutlak bagi penelitian kita: bahwa menyelesaikan *The Boundary Jump Problem* adalah kunci utama kepuasan pendengar musik.

---

## 🎯 Step 10: Research Gap Tiga Lapis
1. **Lapis 1 (Gap Schweiger):** Menganalisis playlist yang sudah ada (*post-hoc empirical analysis*), bukan merancang algoritma pembangkitan (*generative algorithm*).
2. **Lapis 2 (Gap Emosi Dinamis):** Schweiger et al. masih menggunakan fitur agregat lagu (Spotify API audio features statis).
3. **Lapis 3 (Gap Sintesis TA Kita):** Menggunakan prinsip koherensi sekuensial Schweiger untuk merancang algoritma optimasi transisi berbasis trajektori intro-outro dinamis.
