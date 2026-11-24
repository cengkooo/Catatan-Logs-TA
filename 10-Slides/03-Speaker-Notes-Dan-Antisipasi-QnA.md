---
title: "Speaker Notes & Amunisi Tanya Jawab (Q&A 30 Menit Sempro)"
tags:
  - qna
  - speaker-notes
  - defense
  - sempro
  - deam
  - gaur2024
---

# 🛡️ Speaker Notes & Amunisi Tanya Jawab (Q&A 30 Menit Sempro)

> **Tujuan Dokumen:** Mempersiapkan mahasiswa menghadapi sesi tanya jawab 30 menit dari dewan penguji Sempro Teknik Informatika ITERA dengan argumen akademis berbasis data, rujukan paper primer, dan fondasi matematis yang kuat.

---

## 🎯 1. Bank Pertanyaan Kritis Dosen & Strategi Tangkisan

### ❓ Pertanyaan 1: *"Mengapa memilih dataset DEAM daripada Spotify API yang lagunya jauh lebih banyak dan populer?"*
> **Strategi Jawaban (Data-Driven Defense):**
> 1. **Keterbatasan Spotify API:** Spotify Web API hanya menyediakan satu angka statis skalar (skala 0.0 – 1.0) per lagu untuk fitur `valence`, `energy`, dan `danceability`. Spotify **sama sekali tidak menyediakan data time-series dinamis** di dalam lagu.
> 2. **Keunggulan Ilmiah DEAM:** Dataset DEAM (*Database for Emotion Analysis in Music*, Aljanaki et al. 2017) merupakan standar emas di ranah MIR (*Music Information Retrieval*) karena menyediakan **anotasi emosi temporal kontinu sampling 2 Hz (per 500 ms)** yang dievaluasi secara psikologis oleh pendengar manusia.
> 3. **Fokus Riset:** Riset ini bukan tentang kuantitas lagu komersial, melainkan pembuktian hipotesis akademis mengenai efek kurva dinamis terhadap kehalusan transisi playlist.

---

### ❓ Pertanyaan 2: *"Mengapa memilih algoritma KNN dan bukan Deep Reinforcement Learning (DRL) atau Transformer?"*
> **Strategi Jawaban (Scientific Control & Occam's Razor):**
> 1. **Komparasi Head-to-Head Adil:** Model acuan utama penelitian ini adalah karya Shaurya Gaur & Donnelly (2020 / Springer EvoMUSART 2024) yang mengusulkan KNN sebagai algoritma retrieval mood-arc.
> 2. **Isolasi Variabel Kontribusi:** Jika kita langsung mengganti algoritma ke Transformer/DRL, kita tidak bisa membuktikan apakah peningkatan metrik *smoothness* berasal dari representasi trajektori dinamis atau akibat kompleksitas model *deep learning* yang *black-box*.
> 3. **Efisiensi & Code Walkthrough:** KNN bersifat deterministik, transparan, cepat dieksekusi di GPU via PyTorch tensor distance, dan siap dipertanggungjawabkan 100% pada sesi *Code Walkthrough* sidang (bobot 10%).

---

### ❓ Pertanyaan 3: *"Apakah durasi 45 detik pada klip audio DEAM cukup merepresentasikan lagu utuh?"*
> **Strategi Jawaban (Literature Grounding):**
> 1. Mengacu pada metodologi riset psikomusikologi Eerola & Vuoskoski (2013) serta Aljanaki et al. (2017), klip 45 detik pada DEAM diekstrak dari segmen paling informatif lagu (bagian transisi *verse-chorus*).
> 2. Klip 45 detik pada sampling 2 Hz menghasilkan **90 titik telemetri emosi kontinu** per lagu. Jumlah ini sudah sangat cukup untuk menguji kurva transisi awal lagu dan akhir lagu (*boundary alignment*).

---

### ❓ Pertanyaan 4: *"Bagaimana Anda membuktikan secara objektif bahwa playlist Anda lebih mulus?"*
> **Strategi Jawaban (Mathematical Metrics):**
> Kami mengimplementasikan 3 metrik kuantitatif terstandarisasi:
> 1. **Smoothness Index ($S$):** Mengukur jumlah kuadrat deviasi perubahan koordinat emosi pada titik sambungan antar dua lagu ($t_{\text{end}}$ lagu $A$ ke $t_{\text{start}}$ lagu $B$). Nilai semakin kecil menandakan pergantian lagu yang semakin mulus tanpa lonjakan emosi kasar.
> 2. **Evenness Index ($E$):** Mengukur varians jarak Euclidean antar waypoint sepanjang playlist untuk memastikan perjalanan emosi terdistribusi merata.
> 3. **Cosine Trajectory Alignment ($C$):** Mengukur arah vektor perubahan emosi relatif terhadap arah ideal lintasan waypoint user.

---

## 🎙️ 2. Tips Gestur & Pengaturan Waktu (Pacing)

- **Menit 00:00 – 03:00 (Pendahuluan):** Bicara dengan tempo tenang dan artikulatif. Sorot kata kunci *"Kelemahan Struktural Baseline Gaur"*.
- **Menit 03:00 – 07:00 (Metodologi & Matematika):** Tingkatkan tempo, tunjukkan penguasaan formula matematis dan alur pipeline. Arahkan pointer ke diagram 2-tahap.
- **Menit 07:00 – 09:30 (Evaluasi & Roadmap):** Paparkan angka-angka empiris (1.802 audio, 2 Hz, 3 metrik). Tutup tepat sebelum menit ke-10.
- **Sesi Tanya Jawab (30 Menit):** Jangan memotong pertanyaan penguji. Catat poin dosen di kartu bimbingan. Awali jawaban dengan: *"Terima kasih atas pertanyaan Bapak/Ibu penguji, hal tersebut sangat relevan dengan batasan penelitian kami..."*
