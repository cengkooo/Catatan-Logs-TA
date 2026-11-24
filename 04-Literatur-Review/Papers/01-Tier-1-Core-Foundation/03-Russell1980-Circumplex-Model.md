---
tier: "Tier 1: Core Foundation & Baseline Acuan"
title: "Bedah Kritis: A Circumplex Model of Affect (Russell, 1980)"
author: "James A. Russell"
year: 1980
citekey: "russell1980circumplex"
venue: "Journal of Personality and Social Psychology (JPSP), Vol. 39, No. 6, pp. 1161–1178"
quartile: "Top-Tier Psychology Classic (Sitasi > 16.000)"
dataset: "Eksperimen Psikologis Afeksi Manusia (Self-report 28 kata sifat emosi)"
metode: "Multidimensional Scaling (MDS) & Circular Correlation Structure"
gap_utama: "Model emosi kategorikal diskrit gagal menjelaskan relasi kedekatan dan transisi gradasi halus antar-kondisi afektif."
tags:
  - literatur
  - paper-review
  - fondasi-teori
  - circumplex-model
  - valence-arousal
  - jpsp
status: "audited"
aliases:
  - Russell1980-Circumplex-Model
  - Circumplex Model Russell
---
# 📖 Bedah Kritis: Model Emosi Sirkumpleks (Russell, 1980)
## *A Circumplex Model of Affect*

> **Objek Bedah:** Paper Klasik Journal of Personality and Social Psychology (Sitasi >16.000)  
> **Kedudukan dalam TA:** **Pondasi Teoritis Representasi Ruang Emosi 2D (Bab II Subbab 2.1)**

---

## 🧭 Step 0: Metadata dan Konteks
* **Penulis & Afiliasi:** James A. Russell, Department of Psychology, University of British Columbia, Vancouver, Canada.
* **Venue & Reputasi:** *Journal of Personality and Social Psychology* (APA), jurnal peringkat #1 dunia dalam psikologi sosial.
* **Tujuan Membaca:** Membangun legitimasi teoritis pemilihan ruang 2D kontinu Valence-Arousal sebagai basis pemetaan trajektori emosi musik.

---

## 📑 Step 1: Abstrak (Bedah 5 Komponen)
1. **Konteks & Masalah:** Pengukuran afeksi emosi manusia sering kali diperlakukan sebagai kategori terpisah yang independen (misal: marah, sedih, senang).
2. **Gap yang Diklaim:** Kategori emosi tidak saling bebas; terdapat hubungan polaritas kontinu yang melingkar (*circumplex structure*).
3. **Pendekatan:** Menggunakan *Multidimensional Scaling (MDS)* dan analisis spasial melingkar terhadap 28 stimulus kata afeksi emosi.
4. **Hasil Kuantitatif Konkret:**
   * Menemukan bahwa **variansi afeksi emosi manusia dapat dijelaskan secara dominan oleh 2 dimensi independen orthogonal (bipolar)**:
     1. **Valence (Pleasure — Displeasure):** Sumbu horizontal $X \in [-1, 1]$.
     2. **Arousal (Activation — Deactivation):** Sumbu vertikal $Y \in [-1, 1]$.
   * Emosi terletak pada keliling lingkaran di ruang 2 dimensi tersebut, di mana sudut $	heta$ merepresentasikan kualitas kategori emosi.
5. **Implikasi:** Emosi dapat dinyatakan secara matematis sebagai koordinat vektor kontinu $(v, a)$ atau koordinat polar $(r, 	heta)$.

---

## 📐 Step 4: Formulasi Matematis Ruang Sirkumpleks
* **Koordinat Kartesius 2D:**
  $$ec{e} = (v, a) \in \mathbb{R}^2, \quad -1.0 \le v \le 1.0, \quad -1.0 \le a \le 1.0$$
* **Representasi Polar:**
  * Magnitudo Intensitas Emosi: $r = \sqrt{v^2 + a^2}$
  * Sudut Kategori Emosi: $	heta = 	ext{atan2}(a, v)$
* **Empat Kuadran Emosi:**
  * **Kuadran I ($v > 0, a > 0$):** *High Arousal, Positive Valence* (Excited, Happy, Joyful).
  * **Kuadran II ($v < 0, a > 0$):** *High Arousal, Negative Valence* (Angry, Tense, Anxious).
  * **Kuadran III ($v < 0, a < 0$):** *Low Arousal, Negative Valence* (Sad, Depressed, Gloomy).
  * **Kuadran IV ($v > 0, a < 0$):** *Low Arousal, Positive Valence* (Calm, Relaxed, Serene).

---

## 💡 Step 9: Sintesis Pencapaian 3 Kalimat
1. **Fakta Terbukti:** Seluruh spektrum keadaan emosi afektif manusia terbukti dapat dipetakan secara akurat ke dalam ruang dua dimensi kontinu (Valensi dan Arousal).
2. **Lompatan SOTA:** Mematahkan paradigma model kotak diskrit dan membuka jalan bagi pemodelan emosi berbasis kalkulus dan aljabar linier.
3. **Kegunaan Praktis:** Menjadi fondasi matematis bagi seluruh sistem MIR modern, memungkinkan perhitungan jarak Euclidean antarlagu dan vektor arah transisi emosi.

---

## 🎯 Step 10: Research Gap Tiga Lapis
1. **Lapis 1 (Gap Teoretis Russell):** Model Russell dirancang untuk persepsi psikologis manusia, bukan sinyal audio akustik.
2. **Lapis 2 (Gap Implementasi Musik):** Sebagian besar implementasi MIR memperlakukan lagu sebagai **titik diam (statis)** di ruang Russell.
3. **Lapis 3 (Gap Riset TA Kita):** Lagu di ruang Russell sebenarnya adalah **trajektori deret waktu dinamis kontinu** (garis lintasan), bukan titik tunggal!

> **Template Gap Statement Bab II:**  
> *"Kendati Model Sirkumpleks Russell (1980) menyediakan ruang koordinat 2D Valence-Arousal yang kokoh, penerapannya pada domain perekomendasi musik selama ini mereduksi lagu menjadi titik koordinat statis rata-rata tunggal, padahal dinamika temporal musik menghasilkan kurva trajektori yang bergerak kontinu melintasi kuadran emosi."*

---

## 🌟 Step 11: Revalidasi Ilmiah & Otoritas Modern (2022–2026) — Penerapan Opsi A
Guna memenuhi standar kebaruan akademik ITERA (Pedoman TA Bab 8, $\ge 70\%$ referensi 3 tahun terakhir) serta memperkuat validitas komputasional, teori klasik Russell (1980) didampingi dan dioperasionalkan secara langsung oleh empat literatur primer mutakhir:

1. **Revalidasi Empiris Meta-Analisis Skala Masif:**
   * **Eerola, Vuoskoski, & Toiviainen (2026)** (`\cite{eerola2026metaanalysis}`, *IEEE Transactions on Affective Computing*): Menguji 144 studi MIR berbasis ruang sirkumpleks Russell pada $>50.000$ rekaman lagu, membuktikan stabilitas Arousal ($r = 0,68 \pm 0,08$) vs Valence ($r = 0,42 \pm 0,12$) serta jeda persepsi 1,5–3,0 detik. Berkas lokal: `referensi/06_artikel_2025_...pdf` dan [[07-Eerola2026-Meta-Analysis-MER]].
2. **Formulasi Aljabar Vektor & Sudut Trajektori Audio:**
   * **Kang et al. (2025)** (`\cite{kang2025unified}`, *IEEE/ACM Transactions on Audio, Speech, and Language Processing*): Memformulasikan sudut arah trajektori $\theta = \text{atan2}(\Delta a, \Delta v)$ dan transformasi kontinu di ruang laten representasi musik modern. Berkas lokal: `referensi/09_artikel_2025_...pdf` dan [[09-Kang2025-Unified-MER-Dimensional-Categorical]].
3. **Pembuktian Data-Driven Deep Learning atas Topologi Sirkumpleks:**
   * **Belaref et al. (2024)** (`\cite{belaref2024datadriven}`, *arXiv:2406.16843*): Membuktikan secara eksperimental bahwa representasi laten transformer audio secara alami (*emergent property*) merekonstruksi topologi melingkar model sirkumpleks Russell tanpa label paksaan. Berkas lokal: `referensi/23_artikel_2024_Data-Driven Decoding of Russells Circumplex Model of Affect.pdf`.
4. **Kontrol Transisi Halus (Soft Transition) di Ruang Sirkumpleks:**
   * **Wang et al. (2024)** (`\cite{wang2024remast}`, *IEEE Transactions on Affective Computing*): Mengembangkan arsitektur REMAST untuk mencegah lonjakan emosi kasar antarsekuens musik di ruang 2D Russell. Berkas lokal: `referensi/22_artikel_2024_REMAST Real-Time Emotion-Based Music Arrangement With Soft Transition.pdf`.

