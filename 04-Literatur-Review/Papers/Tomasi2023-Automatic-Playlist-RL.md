---
title: "Automatic Music Playlist Generation via Simulation-based Reinforcement Learning"
author: "Federico Tomasi, Joseph Cauteruccio, Surya Kallumadi, Zhenwen Dai"
year: 2023
citekey: "tomasi2023automatic"
dataset: "Spotify User Listening Session Logs & Simulation Environment"
metode: "Simulation-based Reinforcement Learning (Markov Decision Process)"
tags:
  - literatur
  - paper-review
status: "read"
---

# 📖 Automatic Music Playlist Generation via Simulation-based Reinforcement Learning

- **Penulis:** `Federico Tomasi, Joseph Cauteruccio, Surya Kallumadi, Zhenwen Dai` (2023)
- **Citekey LaTeX:** `\cite{tomasi2023automatic}`
- **Dataset:** `Spotify User Listening Session Logs & Simulation Environment`
- **Metode Utama:** `Simulation-based Reinforcement Learning (Markov Decision Process)`

---

## 🎯 Masalah & Tujuan Riset
- **Permasalahan:** Pembentukan playlist sekuensial yang greedy sering gagal mempertahankan kepuasan pendengar jangka panjang sepanjang sesi.
- **Tujuan:** Merumuskan pembentukan playlist otomatis sebagai proses keputusan Markov (MDP) yang dioptimalkan dengan Reinforcement Learning.

---

## 🔬 Arsitektur & Metodologi
- **Representasi Emosi:** Kesesuaian preferensi sekuensial dan retensi sesi.
- **Algoritma / Pendekatan:** Q-Learning / Policy Gradient pada lingkungan simulasi interaksi pengguna Spotify (meminimalkan skip rate).
- **Metrik Evaluasi:** Session Completion Rate, Average Skip Position, dan Cumulative Session Reward.

---

## 💡 Temuan Utama & Hasil
- Mempertimbangkan efek sekuensial (lagu sebelumnya mempengaruhi persepsi lagu berikutnya) meningkatkan waktu dengar secara signifikan dibanding perangkingan independen.

---

## ⚠️ Limitasi & Gap Riset (Peluang untuk TA Kita)
> [!IMPORTANT]
> **Apa kelemahan paper ini yang diselesaikan oleh TA kita?**
- Pendekatan RL membutuhkan data interaksi pengguna skala besar (log Spotify) dan komputasi masif, serta sulit memaksakan kurva mood tertentu.

---

## 🔗 Relevansi dengan Tugas Akhir
- Membuktikan secara matematis bahwa transisi urutan lagu (sekuensial) sangat menentukan kualitas playlist.
- Terkait dengan: [[Matriks-Sintesis]] | [[Dataset-DEAM]] | [[Bab-2-Tinjauan-Pustaka]]
