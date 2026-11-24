---tier: "Tier 2: Methodological Benchmarks & Audio Similarity"

title: "Bedah Kritis: Automatic Music Playlist Generation via Simulation-based Reinforcement Learning"
author: "Federico Tomasi, Zhenwen Dai, & Damien Tardieu (Spotify Research)"
year: 2023
citekey: "tomasi2023automatic"
venue: "ACM Transactions on Recommender Systems (TORS 2023)"
quartile: "Q1 Scopus / Top RecSys Journal"
dataset: "Spotify Interaction Logs & Simulated User Engagement Models"
metode: "Markov Decision Process (MDP) + Deep Q-Network (DQN) + Simulation Environment"
gap_utama: "Metode rekomendasi playlist sekuensial statis gagal mengantisipasi dinamika kelelahan (*listener fatigue*) dan feedback real-time pendengar."
tags:
  - literatur
  - paper-review
  - reinforcement-learning
  - spotify
  - playlist-generation
status: "audited"
aliases:
  - Tomasi2023-Automatic-Playlist-RL
  - Spotify RL Playlist Tomasi
---
# 📖 Bedah Kritis: Playlist Berbasis RL Spotify (Tomasi et al., 2023)
## *Automatic Music Playlist Generation via Simulation-based Reinforcement Learning*

> **Objek Bedah:** Jurnal ACM TORS 2023 (62 KB text)  
> **Kedudukan dalam TA:** **Komparasi Paradigma Optimasi Sekuensial Playlist (Bab II Subbab 2.2)**

---

## 🧭 Step 0 & 1: Konteks & Abstrak Kuantitatif
* **Konteks:** Spotify Research merancang pembuatan playlist interaktif menggunakan Reinforcement Learning untuk memaksimalkan retensi sesi dengar jangka panjang.
* **Hasil Kuantitatif Konkret:**
  * Model RL meningkatkan *session length* sebesar **+11.3%** dan menurunkan *skip rate* sebesar **-8.7%** dibanding heuristik greedy konvensional.
  * Namun, kompleksitas pelatihan model membutuhkan simulasi jutaan interaksi dan biaya komputasi server yang sangat mahal.

---

## 💡 Step 9 & 10: Sintesis & Research Gap
1. **Fakta Terbukti:** Optimasi sekuensial antarlagu terbukti secara signifikan meningkatkan durasi mendengarkan musik pengguna.
2. **Research Gap TA Kita:** Pendekatan RL Spotify adalah *black box* yang membutuhkan log interaksi pengguna skala raksasa. Pendekatan *Geometric Trajectory Alignment* kita menawarkan solusi alternatif yang jauh lebih ringan, deterministik, transparan, dan dapat diimplementasikan secara efisien tanpa memerlukan infrastruktur big data.
