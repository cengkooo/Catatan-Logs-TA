---
title: "Bedah Kritis: Developing a Benchmark for Emotional Analysis of Music (DEAM)"
author: "Anna Aljanaki, Yi-Hsuan Yang, & Mohammad Soleymani"
year: 2017
citekey: "aljanaki2017developing"
venue: "PLOS ONE, Vol. 12, No. 4, e0173366"
quartile: "Q1 Scopus / ISI Web of Science (SJR 0.72)"
dataset: "DEAM (MediaEval Database for Emotional Analysis in Music) — 1.802 klip lagu"
metode: "Crowdsourced Dynamic Annotation (Amazon Mechanical Turk) + Baseline Regression (SVR, Random Forest)"
gap_utama: "Kurangnya dataset publik berskala besar dengan anotasi emosi kontinu deret waktu berfrekuensi tinggi (2 Hz) bebas hak cipta."
tags:
  - literatur
  - paper-review
  - dataset-primer
  - deam
  - dynamic-emotion
  - plos-one
status: "audited"
---

# 📖 Bedah Kritis: Dataset Benchmark DEAM (Aljanaki et al., 2017)
## *Developing a Benchmark for Emotional Analysis of Music*

> **Objek Bedah:** Jurnal Q1 PLOS ONE (67 KB text)  
> **Kedudukan dalam TA:** **Dataset Primer / Korpus Data Utama** Tugas Akhir

---

## 🧭 Step 0: Metadata dan Konteks
* **Penulis & Afiliasi:** Anna Aljanaki (Utrecht University & Geneva), Yi-Hsuan Yang (Academia Sinica, Taiwan), Mohammad Soleymani (Swiss Center for Affective Sciences, University of Geneva).
* **Venue & Reputasi:** *PLOS ONE* (2017), Jurnal Multidisiplin Bereputasi Internasional (Q1 Scopus, Impact Factor $pprox 3.75$).
* **Tujuan Membaca:** Memvalidasi kredibilitas ilmiah anotasi deret waktu 2 Hz, memastikan pemahaman perlakuan *offset delay* 15 detik, dan menghitung reliabilitas inter-annotator agreement.

---

## 📑 Step 1: Abstrak (Bedah 5 Komponen)
1. **Konteks & Masalah:** Bidang Music Emotion Recognition (MER) terhambat oleh kelangkaan dataset terbuka berstandar baku dan keragaman format representasi emosi.
2. **Gap yang Diklaim:** Sebagian besar dataset terdahulu (seperti MIREX) berukuran kecil, tertutup hak cipta komersial, atau hanya memiliki satu label statis per lagu.
3. **Pendekatan:** Membangun dataset DEAM melalui crowdsourcing Amazon Mechanical Turk (AMT) dengan antarmuka dinamis kontinu pada bidang 2D Valence-Arousal.
4. **Hasil Kuantitatif Konkret:**
   * **Ukuran Dataset:** 1.802 klip musik (masing-masing 45 detik) berlisensi Creative Commons (CC) dari Free Music Archive (FMA) dan Jamendo.
   * **Frekuensi Sampling:** 2 Hz (1 sampel per 0.5 detik $ightarrow$ 90 titik pengamatan per lagu).
   * **Anotasi:** Minimal 10 annotator per lagu ($N \ge 10$), dengan skor konsistensi inter-rater *Cronbach's alpha* $lpha \ge 0.78$ untuk Arousal dan $lpha \ge 0.65$ untuk Valence.
5. **Implikasi:** Menjadi dataset benchmark standar emas (*gold standard*) di kompetisi internasional MediaEval.

---

## 🎯 Step 2: Pendahuluan (Problem Framing)
* **Definisi Masalah:** Musik bersifat temporal dinamis; perasaan pendengar bergeser seiring perkembangan progresi akor, dinamika ritme, dan melodi. Penggunaan label statis mengabaikan hakikat temporal musik.
* **Motivasi:** Membuka akses riset MIR global dengan menyediakan audio mentah legal bebas hak cipta disertai ekstraksi fitur akustik openSMILE.

---

## ⚙️ Step 4: Metodologi & Formulasi Pengumpulan Data
* **Protokol Dynamic Annotation:**
  * Annotator mendengarkan klip 45 detik sambil menggerakkan kursor mouse pada antarmuka 2D Valence-Arousal (rentang $[-10, 10]$ yang dinormalisasi ke $[-1, 1]$).
* **Offset 15 Detik (*Reaction Time Lag*):**
  * Data anotasi dimulai efektif pada detik ke-15 ($t = 15.0$ detik) karena 15 detik pertama dialokasikan bagi annotator untuk menangkap nuansa emosi lagu dan mengatasi *motor-reaction delay*.
  * Panjang deret waktu efektif per trek: $45 - 15 = 30$ detik $	imes 2	ext{ Hz} = \mathbf{60	ext{ timestamp}}$ (atau 90 timestamp jika dihitung dari detik ke-0).

---

## 🧪 Step 5: Setup Eksperimen Baseline Aljanaki
* **Fitur Akustik:** Ekstraksi 260 fitur audio openSMILE (MFCC, Spectral Flux, Loudness, Pitch).
* **Model Baseline:** Support Vector Regression (SVR) dan Random Forest Regressor.
* **Metrik Evaluasi:** Root Mean Squared Error (RMSE) dan Pearson Correlation Coefficient ($r$).
* **Temuan Baseline:** Prediksi emosi **Arousal jauh lebih akurat ($r pprox 0.65$)** dibanding **Valence ($r pprox 0.35$)**, membuktikan bahwa fitur akustik standar lebih mudah menangkap energi musik daripada kebahagiaan/kesedihan.

---

## ⚠️ Step 7: Limitasi Tersembunyi & Red Flags
> [!IMPORTANT]
> **Limitasi Dataset DEAM yang Wajib Diwaspadai:**
> 1. **Perbedaan Reliabilitas V-A:** Reliabilitas Valence lebih rendah daripada Arousal karena persepsi valensi (positif/negatif) sangat dipengaruhi latar belakang budaya dan preferensi subyektif annotator.
> 2. **Durasi Terbatas 45 Detik:** DEAM menggunakan klip cuplikan 45 detik, bukan lagu durasi penuh 3–4 menit. Hal ini harus dinyatakan secara tegas pada batasan masalah Bab I TA.

---

## 💡 Step 9: Sintesis Pencapaian 3 Kalimat
1. **Fakta Terbukti:** Dataset DEAM terbukti menyediakan 1.802 klip musik dengan anotasi emosi kontinu 2 Hz yang memiliki reliabilitas statistik tinggi dan bebas hak cipta.
2. **Lompatan SOTA:** Melipatgandakan ukuran dataset dinamis terdahulu hingga 3 kali lipat dan menyediakan fitur akustik terbuka.
3. **Kegunaan Praktis:** Menjadi fondasi data deret waktu yang memungkinkan ekstraksi vektor trajektori emosi $[\Delta v, \Delta a, 	heta]$.

---

## 🎯 Step 10: Research Gap Tiga Lapis
1. **Lapis 1 (Gap Aljanaki):** Aljanaki fokus pada *Music Emotion Recognition (MER)* regresi pasif (memprediksi emosi dari audio), belum menyentuh aplikasi *Recommender Systems* atau *Playlist Generation*.
2. **Lapis 2 (Gap Integrasi ke Baseline):** Baseline Gaur (2023) belum pernah dievaluasi pada dataset dinamis DEAM karena Gaur hanya memakai dataset statis DMDD.
3. **Lapis 3 (Gap Orisinalitas TA Kita):** Memanfaatkan matriks deret waktu DEAM untuk mengekstrak vektor laju perubahan mood antarsegmen intro/outro guna memecahkan masalah transisi pada playlist.

> **Template Gap Statement Bab I & II:**  
> *"Meskipun dataset DEAM (Aljanaki et al., 2017) telah menyediakan anotasi deret waktu emosi berfrekuensi 2 Hz pada 1.802 klip musik, data temporal tersebut selama ini hanya dieksploitasi untuk tugas regresi emosi (MER), dan belum pernah dimanfaatkan untuk memandu penyelarasan trajektori transisi antarlagu pada sistem perekomendasi playlist mood-arc."*
