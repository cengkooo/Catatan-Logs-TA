---
title: "3_PANDUAN_TERMINOLOGI_SEMPRO — Kamus Istilah Ilmiah & Panduan Komunikasi Sempro/Sidang IF ITERA"
tags:
  - sempro
  - sidang-ta
  - terminologi
  - mir
  - recommender-system
  - code-walkthrough
  - unesco
date: 2026-11-19
status: "DEFINITIVE & VERIFIED"
author: "Andryano Shevchenko Limbong (123140205)"
---

# 🛡️ 3_PANDUAN_TERMINOLOGI_SEMPRO
## Kamus Istilah Akademik, Antisipasi Jebakan Penguji, & Panduan Komunikasi Ilmiah
### Program Studi Teknik Informatika — Institut Teknologi Sumatera (ITERA)

> **Dokumen Terkait:** [Proposal Pengajuan TA.pdf](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Proposal%20Pengajuan%20TA.pdf), [1_TRAIN_BASELINE.md](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Catatan-Memori/Catatan-Memori-Logs/05-Eksperimen/1_TRAIN_BASELINE.md), dan [plan_academic_taxonomy_of_thesis.md](file:///C:/Users/kadarisman/.gemini/antigravity-cli/brain/65c74f6d-fb7e-4835-968d-67954c603f26/plan_academic_taxonomy_of_thesis.md)  
> **Tujuan Dokumen:** Memastikan mahasiswa menggunakan register bahasa ilmiah yang $100\%$ presisi, menghindari istilah rancu (*blunder*) yang memancing serangan penguji, dan memaksimalkan nilai **Presentasi (20%)** serta **Code Walkthrough (10%)** pada Sempro dan Sidang Akhir.

---

## 🚫 1. Tabel Hitam-Putih: Kata Terlarang vs. Kata Pengganti yang Elegan

| ❌ JANGAN PERNAH UCAPKAN (Pemicu Serangan) | ✅ UCAPKAN INI (Akurat, Elegan, & Anti-Debat) | Mengapa Harus Diganti? (Alasan Akademik) |
| :--- | :--- | :--- |
| *"Saya **melatih (train) model AI** untuk membuat playlist."* | *"Kami mengembangkan **pipeline sequential music recommendation berbasis konten (content-based)** dengan pendekatan heuristik dua tahap."* | Di kode Anda tidak ada *gradient descent*, *loss function*, atau *epochs*. Mengklaim "melatih AI" akan membuat penguji meminta grafik loss dan bobot model. |
| *"Model baseline Gaur mencapai **akurasi 99%**."* | *"Proyeksi PCA 12-komponen berhasil mempertahankan **explained variance sebesar 99.10%** dari 15 fitur audio akustik."* | 99.10% adalah metrik reduksi variansi PCA (SVD), **bukan akurasi model**. Menyebutnya "akurasi" adalah kesalahan fatal statistika. |
| *"Saya melakukan **training KNN** pada dataset DEAM."* | *"Kami melakukan **indeksasi spasial koordinat emosi statis** menggunakan struktur data **KD-Tree** untuk pencarian tetangga terdekat $\mathcal{O}(\log M)$."* | KNN adalah *lazy learner* non-parametrik. Fase training-nya kosong; yang terjadi hanyalah pembentukan pohon biner pencarian di memori RAM. |
| *"Penelitian saya berada di bidang **Deep Learning / Generative AI**."* | *"Penelitian ini berada pada ranah **Music Information Retrieval (MIR)** dan **Affective Computing** dengan fokus pada **Sequential Playlist Generation**."* | Ini menempatkan riset Anda pada taksonomi internasional yang tepat (ACM CCS / ISMIR), bukan *buzzword* generik. |
| *"Algoritma baseline Gaur **gagal / jelek**."* | *"Metode acuan Gaur (2020) memiliki **keterbatasan struktural** akibat representasi titik statis tunggal per lagu pada dataset DMDD yang digunakannya."* | Menghormati literatur terdahulu (paper rujukan diterbitkan di Springer EvoMUSART) dan menunjukkan bahwa kelemahannya bersumber dari sifat data, bukan kecerobohan penulisnya. |
| *"Saya membuat **dataset baru**."* | *"Kami melakukan **ekstraksi fitur akustik mandiri** (Librosa) dan **pemodelan vektor trajektori emosi dinamis 2 Hz** pada korpus baku DEAM."* | Anda tidak merekam lagu baru; Anda mengekstrak dimensi representasi baru dari korpus DEAM yang sudah terstandarisasi. |
| *"Playlist ini **enak didengar dan smooth**."* | *"Playlist ini memiliki **tingkat kelancaran matematis (Smoothness $|\rho|$)** dan **keseragaman langkah emosi (Evenness $Var(\text{RMSE})$)** yang terukur secara kuantitatif."* | Menghindari klaim subjektif/persepsi manusia tanpa uji dengar formal (*user study*), dan berpegang teguh pada metrik objektif proposal. |

---

## 🎯 2. Cheat Sheet Ujian: Menjawab 5 Pertanyaan Kritis Penguji

Gunakan skrip jawaban berikut saat dosen penguji menguji metodologi Anda:

### ❓ Pertanyaan 1: *"Apakah Anda melatih (train) model machine learning pada sistem ini?"*
> **Jawaban Mahasiswa:**  
> *"Tidak secara *eager learning* parametrik, Bapak/Ibu. Dalam taksonomi machine learning (Tom Mitchell, 1997), K-Nearest Neighbors diklasifikasikan sebagai **Instance-Based Learning** atau **Lazy Learner**. Sistem kami tidak mengoptimasi bobot neural network via backpropagation, melainkan mengintegrasikan tiga teknik komputasi:
> 1. **Statistical Learning:** Regresi linier sederhana (*Ordinary Least Squares*) untuk mengestimasi vektor slope kemiringan emosi internal lagu ($\beta_V, \beta_A$).
> 2. **Unsupervised Learning:** Reduksi dimensi 15 fitur audio menjadi 12 dimensi PCA via Singular Value Decomposition.
> 3. **Spatial Metric Query:** Indeksasi pohon biner KD-Tree untuk pencarian kandidat lagu terdekat saat runtime."*

---

### ❓ Pertanyaan 2: *"Kalau tidak ada deep learning, di mana letak kontribusi keilmuan Teknik Informatika-nya?"*
> **Jawaban Mahasiswa:**  
> *"Kontribusi informatika pada penelitian ini terletak pada **perancangan algoritma dan optimasi pemodelan data sekuensial pada ranah Music Information Retrieval (MIR)**. 
> Kontribusi utamanya adalah:
> 1. **Perluasan Representasi Data:** Mengubah representasi emosi lagu dari yang sebelumnya hanya 1 titik statis (0 Hz) menjadi vektor trajektori dinamis berbasis anotasi time-series 2 Hz.
> 2. **Metrik Evaluasi Baru:** Kami merancang metrik orisinal bernama **Arc-Trajectory Alignment Score** untuk mengukur keselarasan mikro-transisi di dalam lagu terhadap makro-arc playlist.
> 3. **Formulasi Multi-Criteria Re-Ranking:** Menggabungkan kriteria jarak akustik dan penyelarasan arah trajektori menggunakan pembobotan adaptif $\alpha$."*

---

### ❓ Pertanyaan 3: *"Mengapa menggunakan pendekatan KNN + Geometri, bukan langsung pakai Transformer atau Reinforcement Learning?"*
> **Jawaban Mahasiswa:**  
> *"Ada dua alasan ilmiah mendasar, Bapak/Ibu:
> 1. **Ketersediaan Data Anotasi Emosi Dinamis:** Model Deep Learning/Transformer membutuhkan puluhan ribu hingga jutaan playlist pengguna (seperti Spotify Million Playlist Dataset) yang sayangnya tidak memiliki label emosi kontinu 2 Hz. Dataset DEAM dengan rating manusia kontinu hanya berjumlah 1.802 lagu. Menggunakan Transformer pada ukuran data ini akan menyebabkan *severe overfitting*.
> 2. **Transparansi & Keterjelikan (*Explainability*):** Industri streaming (seperti Deezer Flow Moods) membutuhkan kontrol mood arc yang deterministik. Pendekatan geometri dua tahap menjamin transparansi matematis penuh mengapa sebuah lagu dipilih, berbeda dengan sifat *black-box* pada deep learning."*

---

### ❓ Pertanyaan 4: *"Apa fungsi parameter $\alpha$ pada rumus Tahap 2 Anda?"*
> **Jawaban Mahasiswa:**  
> *"Parameter $\alpha \in [0.0, 1.0]$ adalah koefisien penyeimbang (*trade-off weight*) antara kemiripan tekstur akustik instrumen dan keselarasan arah emosi:
> $$\text{Final Score} = \alpha \cdot \text{Acoustic Sim} + (1 - \alpha) \cdot \text{Trajectory Alignment}$$
> * Ketika $\alpha = 1.0$, sistem bekerja murni sebagai **Baseline Gaur (2020)**.
> * Ketika $\alpha < 1.0$ (misal $0.5$ atau $0.7$), sistem mengaktifkan modul usulan kami yang mempertimbangkan arah pergerakan mood internal lagu. Ini membuktikan bahwa baseline Gaur adalah kasus khusus (*special case*) dari model usulan kami."*

---

### ❓ Pertanyaan 5: *"Mengapa metrik Smoothness baseline Gaur bisa mencapai 0.995 padahal katanya punya kelemahan?"*
> **Jawaban Mahasiswa:**  
> *"Angka Smoothness 0.995 diukur menggunakan korelasi Pearson antara Valence dan Arousal sepanjang playlist. Nilai ini sangat tinggi bukan karena kualitas musiknya sempurna, melainkan karena formula Persamaan 5 Gaur secara eksplisit memaksa titik target waypoint ($S_T$) berada pada garis lurus antara titik asal dan titik tujuan.
> Kelemahan aslinya baru terlihat saat lagu tersebut diputar: transisi antar-lagunya bisa terasa menabrak karena Gaur mengabaikan apakah emosi di akhir lagu pertama selaras dengan emosi di awal lagu kedua. Inilah yang diatasi oleh metrik **Arc-Trajectory Alignment Score** kami."*

---

## 🏛️ 3. Taksonomi Resmi untuk Penulisan Naskah UNESCO (Bab I–III)

Gunakan taksonomi baku ini pada draf naskah LaTeX `thesis.tex`:

```text
Bidang Ilmu          : Teknik Informatika (Computer Science)
Sub-bidang Utama     : Information Systems -> Recommender Systems
Sub-bidang Spesifik  : Music Information Retrieval (MIR) / Affective Computing
Topik Riset          : Sequential Playlist Generation Berbasis Mood-Arc
Paradigma Algoritma  : Two-Stage Content-Based Retrieval & Trajectory Alignment
Metode Tahap 1       : Instance-Based Spatial Retrieval (K-Nearest Neighbors via KD-Tree)
Metode Tahap 2       : Multi-Criteria Decision Making (Acoustic Distance + Directional Cosine Alignment)
Korpus Uji           : Database for Emotion Analysis in Music (DEAM) — 1.802 Tracks (2 Hz Sampling)
```

---

## 📋 4. Checklist 10 Menit Presentasi Sempro

Saat menyusun slide (menggunakan Typst/Touying):
- [ ] **Slide 1-3 (Latar Belakang & Gap):** Tampilkan kontras antara kebutuhan industri streaming (*Mood Arc*) vs keterbatasan representasi statis Gaur (1 lagu = 1 titik).
- [ ] **Slide 4-5 (Dataset DEAM):** Jelaskan keunggulan DEAM yang memiliki dua layer: Anotasi Statis (untuk Baseline) dan Anotasi Dinamis 2 Hz (untuk Model Usulan).
- [ ] **Slide 6-7 (Metodologi Sistem):** Tampilkan diagram alur 2-Tahap Anda. Tekankan bahwa Tahap 1 menggunakan KNN untuk *retrieval* kandidat, dan Tahap 2 menggunakan *Trajectory Alignment*.
- [ ] **Slide 8-9 (Metrik Evaluasi):** Tunjukkan 3 metrik kuantitatif: Smoothness (PCC), Evenness (Var RMSE), dan Arc-Trajectory Alignment Score.
- [ ] **Slide 10 (Target Luaran & Jadwal):** Tampilkan roadmap penyelesaian dan luaran komparatif *apple-to-apple*.
