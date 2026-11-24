---
title: "Bedah Kritis: Leakage-Audited Dynamic Arousal Forecasting With Scheduled Future Music"
author: "Bin Wen, Dai-Qiao Zhang, & Tien-Ping Tan"
year: 2025
citekey: "wen2025leakage"
venue: "IEEE/ACM Transactions on Audio, Speech, and Language Processing / Preprint"
quartile: "Top-Tier Speech & Audio Processing"
dataset: "PMEmo & DEAM (1.494 lagu evaluation pool terisolasi)"
metode: "Past/Future MuQ Representation + Complete Song Holdout + Innovation Forecasting"
gap_utama: "Adanya temporal data leakage masif pada riset dynamic MER akibat evaluasi berbasis random split dan penggunaan data masa depan secara tidak sah."
tags:
  - literatur
  - paper-review
  - leakage-audit
  - dynamic-arousal
  - deam
  - forecasting
status: "audited"
---

# 📖 Bedah Kritis: Leakage-Audited Dynamic Arousal (Wen et al., 2025)
## *Known Music, Unknown Response: Leakage-Audited Dynamic Arousal Forecasting*

> **Objek Bedah:** Naskah Riset Mutakhir 2025 (56 KB text)  
> **Kedudukan dalam TA:** **Rujukan Kritis Metodologi & Audit Integritas Data Deret Waktu DEAM**

---

## 🧭 Step 0: Metadata dan Konteks
* **Penulis & Afiliasi:** Bin Wen, Dai-Qiao Zhang, Tien-Ping Tan (School of Computer Sciences & Mathematical Sciences, Universiti Sains Malaysia).
* **Venue & Tahun:** Dipublikasikan awal 2025 (arXiv:2502.xxxx).
* **Tujuan Membaca:** Memahami bahaya laten *data leakage* pada pemrosesan dataset DEAM dan mengadopsi protokol pemisahan data berbasis *complete song holdout*.

---

## 📑 Step 1: Abstrak (Bedah 5 Komponen)
1. **Konteks & Masalah:** Dynamic MER konvensional memprediksi emosi dari audio yang sudah diobservasi secara bersamaan (*concurrent*). Namun, dalam skenario nyata, sistem perlu meramalkan perubahan respon emosi mendatang (*scheduled future music*).
2. **Gap yang Diklaim:** Banyak publikasi MER membanggakan akurasi tinggi, tetapi sebenarnya mengalami **temporal data leakage** karena membagi data secara *random frame-level split* (potongan frame dari lagu yang sama masuk ke train dan test).
3. **Pendekatan:** Mengembangkan protokol evaluasi ketat berbasis *complete song holdout* (memisahkan lagu secara utuh), menguji representasi MuQ (Music Quantized foundation model), dan meramalkan inovasi arousal.
4. **Hasil Kuantitatif Konkret:**
   * Diuji pada 1.494 lagu DEAM yang diisolasi ketat dari tahap engineering.
   * Representasi masa lalu/masa depan MuQ meningkatkan Concordance Correlation Coefficient (CCC) sebesar **0.389–0.507** dibanding baseline emosi terkini.
   * Membuktikan bahwa random-split pada time-series meningkatkan skor CCC secara semu (*inflated score*) hingga >35%.
5. **Implikasi:** Protokol *song-level split* adalah syarat mutlak agar hasil evaluasi komputasi dapat dipertanggungjawabkan di dunia nyata.

---

## ⚠️ Step 5 & 7: Audit Setup Eksperimen & Red Flags
> [!CAUTION]
> **Pelajaran Krusial untuk Metodologi Skripsi ITERA:**
> * **Larangan Keras Random Split pada Data Audio Beruntun:** Memotong klip lagu DEAM menjadi segmen 0.5 detik lalu mengacaknya ke train-test split adalah **kesalahan fatal metodologis (*catastrophic leakage*)**.
> * **Solusi yang Kita Adopsi:** Seluruh pemisahan data atau pengujian trajectory pada Tugas Akhir kita wajib menggunakan unit **lagu utuh (*Song-Level Holdout*)**.

---

## 💡 Step 9: Sintesis Pencapaian 3 Kalimat
1. **Fakta Terbukti:** Model peramalan arousal dinamis mampu memproyeksikan perubahan emosi musik mendatang dengan peningkatan CCC signifikan jika fitur masa depan dimanfaatkan secara benar.
2. **Lompatan SOTA:** Membangun benchmark audit *data leakage* pertama yang membedah kelemahan metodologis riset-riset MER terdahulu pada DEAM.
3. **Kegunaan Praktis:** Memberikan jaminan integritas bahwa evaluasi trajektori emosi antarlagu kita bebas dari kebocoran data.

---

## 🎯 Step 10: Research Gap Tiga Lapis
1. **Lapis 1 (Gap Wen):** Fokus pada peramalan emosi pendengar terhadap audio yang akan datang (*forecasting affect*).
2. **Lapis 2 (Gap Rekomendasi):** Wen et al. tidak merancang sistem pembentukan playlist (*playlist generation*); mereka murni menguji regresi time-series.
3. **Lapis 3 (Gap Sintesis TA Kita):** Menerapkan prinsip *leakage-free song-level evaluation* ke dalam pengujian metrik Smoothness dan Evenness pada playlist dinamis.
