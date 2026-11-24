---
title: "Master Blueprint Slide Sempro IF ITERA (10 Menit — 14 Slide)"
tags:
  - blueprint
  - sempro
  - slides
  - anti-slop
  - speaking-script
  - itera
total_slides: 14
presentation_budget: "09:30 (Target Maksimal 10:00)"
qna_budget: "30:00"
theme: "Touying Metropolis / SpaceX Academic"
---

# 🎯 Master Blueprint Slide Sempro IF ITERA (14 Slide — Tepat 10 Menit)

> **Aturan Wajib ITERA (AGENTS.md):** Alokasi presentasi mahasiswa **tepat 10 menit**, dilanjutkan tanya jawab penguji **30 menit**. Melewati 10 menit akan dipotong oleh moderator. Target latihan mandiri: **9 menit 30 detik**.

---

## ⏱️ Alokasi Waktu Global

```mermaid
gantt
    title Alokasi Waktu 10 Menit Sempro (Total 570 Detik)
    dateFormat X
    axisFormat %s s
    section Pendahuluan
    Slide 1: Cover & Identitas        :0, 30
    Slide 2: Fenomena Streaming Musik  :30, 75
    Slide 3: Kelemahan Baseline Gaur   :75, 135
    Slide 4: Research Gap & Hipotesis  :135, 180
    Slide 5: Rumusan & Tujuan          :180, 225
    section Metodologi
    Slide 6: Teori Russell & DEAM      :225, 285
    Slide 7: Pipeline 2-Tahap          :285, 345
    Slide 8: Tahap 1 Interpolasi & KNN :345, 405
    Slide 9: Tahap 2 Trajectory Align  :405, 465
    section Evaluasi & Rencana
    Slide 10: Metrik Evaluasi          :465, 510
    Slide 11: Validasi Awal EDA DEAM   :510, 540
    Slide 12: Roadmap TA 2             :540, 555
    Slide 13: Kesimpulan               :555, 570
    Slide 14: Q&A Closing              :570, 600
```

---

## 📑 Rincian Slide demi Slide (*Slide-by-Slide Specification*)

### 📌 Slide 1: Cover & Identitas Akademik ITERA
- **Alokasi Waktu:** 00:00 – 00:30 (30 detik)
- **Komponen Visual:** Judul riset, Nama Mahasiswa (Andryano / 121140205), Dosen Pembimbing, Logo/Identitas IF ITERA.
- **Gagasan Inti:** Membuka presentasi secara lugas, percaya diri, dan menyatakan judul penelitian.
- **Speaking Script (Narasi Lisan):**
  > *"Selamat pagi/siang Bapak/Ibu dosen penguji dan pembimbing. Terima kasih atas kesempatan yang diberikan. Pada hari ini saya akan mempresentasikan proposal Tugas Akhir saya yang berjudul: **'Rancang Bangun Sistem Mood-Arc Playlist Generation Berbasis Dynamic Emotion Trajectory Alignment Menggunakan Dataset DEAM'**."*

---

### 📌 Slide 2: Fenomena Streaming Musik & Kebutuhan *Mood-Arc*
- **Alokasi Waktu:** 00:30 – 01:15 (45 detik)
- **Komponen Visual:** Kartu perbandingan: Pendengar musik membutuhkan kurva emosi dinamis (*mood-arc*, misal: relaksasi bertahap dari stres menuju tenang), bukan sekadar koleksi lagu acak dengan genre serupa.
- **Anti-Slop Pattern:** Diagram *Emotional Journey Curve* (Waktu vs Valence/Arousal).
- **Speaking Script:**
  > *"Dalam industri streaming modern seperti Spotify dan Apple Music, playlist berbasis konteks dan suasana hati menjadi fitur yang paling banyak dikonsumsi. Namun, respon emosional pendengar saat mendengarkan musik bukanlah garis datar statis, melainkan sebuah kurva perjalanan yang terus bertransisi atau kita sebut sebagai **mood-arc**."*

---

### 📌 Slide 3: Kelemahan Struktural Model Acuan (Gaur & Donnelly 2020)
- **Alokasi Waktu:** 01:15 – 02:15 (60 detik)
- **Komponen Visual:** *Versus Split-Box*: Diagram alir KNN Gaur & Donnelly (2020) yang menggunakan dataset DMDD.
- **Anti-Slop Pattern:** Box merah kontras menyorot **Akar Masalah Struktural**.
- **Speaking Script:**
  > *"Penelitian acuan kami, Gaur dan Donnelly (2020), memperkenalkan pendekatan interpolasi lintasan mood menggunakan algoritma KNN. Namun, terdapat kelemahan struktural mendasar: bukan pada algoritmanya, melainkan karena dataset DMDD yang mereka gunakan hanya menyediakan **satu nilai rata-rata statis** per lagu. Akibatnya, lagu berdurasi 4 menit hanya direpresentasikan oleh 1 titik koordinat, mengabaikan dinamika internal lagu dan menimbulkan lonjakan emosi yang tajam saat transisi."*

---

### 📌 Slide 4: *Research Gap* & Hipotesis Kontribusi Utama
- **Alokasi Waktu:** 02:15 – 03:00 (45 detik)
- **Komponen Visual:** *Callout Banner* tebal berwarna emas/kuning memuat pernyataan *Research Gap* formal.
- **Gagasan Inti:** Merumuskan kontribusi pembeda penelitian.
- **Speaking Script:**
  > *"Dari kelemahan tersebut, muncul Research Gap utama: **Belum ada studi yang menguji apakah mempertimbangkan trajektori dinamis mood beresolusi tinggi di dalam lagu menghasilkan transisi playlist mood-arc yang lebih koheren dan mulus dibandingkan static-point matching.** Hipotesis kami adalah pemodelan lintasan dinamis akan secara signifikan mereduksi metrik kekasaran transisi (smoothness penalty)."*

---

### 📌 Slide 5: Rumusan Masalah & Tujuan Penelitian
- **Alokasi Waktu:** 03:00 – 03:45 (45 detik)
- **Komponen Visual:** 3 Kartu Bernomor (*Numbered Cards* 01, 02, 03) yang saling berpasangan antara Rumusan dan Tujuan.
- **Speaking Script:**
  > *"Penelitian ini menjawab 3 rumusan masalah utama: Pertama, bagaimana merancang representasi trajektori emosi 2D dari dataset beresolusi tinggi? Kedua, bagaimana mengintegrasikan algoritma Trajectory Alignment untuk memilih urutan lagu paling mulus? Ketiga, seberapa besar peningkatan performa yang dicapai dibanding model baseline Gaur & Donnelly?"*

---

### 📌 Slide 6: Model Emosi 2D Russell & Profil Dataset Utama DEAM
- **Alokasi Waktu:** 03:45 – 04:45 (60 detik)
- **Komponen Visual:** Diagram Kuadran Russell (Valence horizontal, Arousal vertikal) + *Stat Cards Telemetri* (**1.802 audio tracks**, sampling rate **2 Hz** per 500 ms).
- **Speaking Script:**
  > *"Kami mengadopsi model sirkumpleks emosi 2D Russell yang memetakan emosi ke sumbu Valence dan Arousal. Untuk mengatasi kelemahan model acuan, kami beralih ke dataset **DEAM (Database for Emotion Analysis in Music)** yang memuat 1.802 audio klip penuh dengan anotasi temporal kontinu sampling 2 Hz atau per 500 milidetik."*

---

### 📌 Slide 7: Diagram Alir Arsitektur Dua Tahap (*Two-Stage Pipeline*)
- **Alokasi Waktu:** 04:45 – 05:45 (60 detik)
- **Komponen Visual:** Flowchart arsitektur sistem modular:
  `Input Waypoint User` $\rightarrow$ `Tahap 1: KNN Candidate Retrieval` $\rightarrow$ `Tahap 2: Dynamic Trajectory Alignment & Smoothing` $\rightarrow$ `Output Playlist`.
- **Speaking Script:**
  > *"Arsitektur solusi yang kami bangun terdiri dari **Two-Stage Pipeline**. Tahap pertama berfungsi memfilter kandidat lagu secara cepat dari ruang interpolasi waypoint menggunakan KNN. Tahap kedua adalah inti kebaruan kami, yaitu melakukan dynamic trajectory alignment untuk mengurutkan lagu berdasarkan kecocokan kurva emosi kontinu."*

---

### 📌 Slide 8: Tahap 1 — Interpolasi Waypoint & Algoritma KNN Retrieval
- **Alokasi Waktu:** 05:45 – 06:45 (60 detik)
- **Komponen Visual:** Formulasi matematis interpolasi linear/spline antara titik awal $P_{\text{start}}$ dan titik akhir $P_{\text{target}}$, serta formula jarak Euclidean ruang pencarian KNN.
- **Speaking Script:**
  > *"Pada tahap pertama, pengguna menentukan titik emosi awal dan target. Sistem melakukan interpolasi kurva untuk menghasilkan $K$ titik waypoint ideal. Algoritma KNN kemudian mengambil sejumlah $M$ lagu kandidat terdekat di sekitar setiap waypoint sebagai pool seleksi awal."*

---

### 📌 Slide 9: Tahap 2 — Dynamic Trajectory Alignment & Penalti Emosi
- **Alokasi Waktu:** 06:45 – 07:45 (60 detik)
- **Komponen Visual:** Formula jarak trajektori terbobot temporal $D(\mathbf{T}_A, \mathbf{T}_B)$ dan fungsi objektif minimasi penalti:
  $$ \min \sum_{k=1}^{K-1} D(\mathbf{T}_k, \mathbf{T}_{k+1}) + \lambda \cdot \text{JerkPenalty} $$
- **Speaking Script:**
  > *"Di tahap kedua, kami menghitung keselarasan antara akhir lintasan lagu $A$ dengan awal lintasan lagu $B$. Kami merumuskan fungsi objektif dengan penalti akselerasi emosi (jerk penalty) agar pergantian lagu terasa natural di telinga pendengar."*

---

### 📌 Slide 10: Tiga Metrik Evaluasi Kuantitatif Objektif
- **Alokasi Waktu:** 07:45 – 08:30 (45 detik)
- **Komponen Visual:** Tabel/Kartu 3 Metrik Utama:
  1. **Smoothness Metric:** Rata-rata deviasi kuadrat perubahan emosi antar lagu.
  2. **Evenness Metric:** Keseragaman interval langkah emosi sepanjang playlist.
  3. **Cosine Trajectory Similarity:** Keselarasan arah vektor perubahan emosi terhadap rute target.
- **Speaking Script:**
  > *"Untuk memvalidasi keunggulan model secara objektif tanpa bias subjektivitas pendengar, kami mengukur tiga metrik kuantitatif: Smoothness untuk mengukur kemulusan transisi, Evenness untuk pemerataan jarak langkah, dan Cosine Similarity terhadap rute ideal."*

---

### 📌 Slide 11: Validasi Awal Eksperimen & Karakteristik Data DEAM
- **Alokasi Waktu:** 08:30 – 09:00 (30 detik)
- **Komponen Visual:** Grafik scatter plot sebaran 1.802 trajektori lagu DEAM pada bidang Valence-Arousal yang membuktikan variasi temporal dinamis dalam setiap lagu.
- **Speaking Script:**
  > *"Eksplorasi data awal pada dataset DEAM membuktikan bahwa lebih dari 78% lagu mengalami perpindahan kuadran emosi sepanjang durasinya. Hal ini memperkuat hipotesis kami bahwa mengabaikan dinamika temporal lagu adalah cacat struktural yang fatal pada model-model sebelumnya."*

---

### 📌 Slide 12: Roadmap Penelitian & Rencana Kerja TA 2
- **Alokasi Waktu:** 09:00 – 09:20 (20 detik)
- **Komponen Visual:** Tabel Gantt Chart rencana implementasi coding PyTorch CUDA pada GPU RTX 3070 Ti, komparasi head-to-head terhadap baseline Gaur, hingga penulisan naskah akhir.
- **Speaking Script:**
  > *"Berikut adalah peta jalan penelitian hingga tahap Sidang Akhir. Eksperimen replikasi baseline Gaur dan pipeline trajektori dinamis akan diakselerasi menggunakan PyTorch CUDA pada workstation lokal."*

---

### 📌 Slide 13: Kesimpulan Proposal
- **Alokasi Waktu:** 09:20 – 09:40 (20 detik)
- **Komponen Visual:** 2 Poin Kesimpulan Kunci dalam kartu terarsir elegan.
- **Speaking Script:**
  > *"Kesimpulannya, proposal ini menawarkan solusi pemodelan mood-arc playlist yang mengatasi batasan representasi statis melalui dynamic trajectory alignment dengan dataset beresolusi temporal tinggi 2 Hz."*

---

### 📌 Slide 14: Penutup & Sesi Tanya Jawab (Q&A)
- **Alokasi Waktu:** 09:40 – 10:00 (20 detik)
- **Komponen Visual:** Teks tegas *"Terima Kasih — Sesi Tanya Jawab (Q&A)"*, Nama & Kontak Mahasiswa, Institusi IF ITERA.
- **Speaking Script:**
  > *"Demikian presentasi proposal Tugas Akhir saya. Waktu presentasi saya kembalikan kepada Bapak/Ibu Dewan Penguji. Saya siap untuk sesi tanya jawab. Terima kasih."*
