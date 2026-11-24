---
title: "SynthesizRR: Generating Diverse Datasets with Retrieval Augmentation"
author: "Abhishek Divekar, Greg Durrett"
year: 2023
citekey: "divekar2023synthesizrr"
dataset: "Benchmark Korpus Pengambilan dan Klasifikasi Teks"
metode: "Retrieval-Augmented Density Filtering & Diversity Maximization"
tags:
  - literatur
  - paper-review
status: "read"
---

# 📖 SynthesizRR: Generating Diverse Datasets with Retrieval Augmentation

- **Penulis:** `Abhishek Divekar, Greg Durrett` (2023)
- **Citekey LaTeX:** `\cite{divekar2023synthesizrr}`
- **Dataset:** `Benchmark Korpus Pengambilan dan Klasifikasi Teks`
- **Metode Utama:** `Retrieval-Augmented Density Filtering & Diversity Maximization`

---

## 🎯 Masalah & Tujuan Riset
- **Permasalahan:** Algoritma seleksi tetangga terdekat (seperti KNN murni) cenderung bias pada area ruang fitur yang padat (density bias), menyebabkan luaran yang monoton dan miskin keragaman.
- **Tujuan:** Mengembangkan mekanisme filter retrieval-augmented yang mempertahankan keragaman sampel sambil tetap memenuhi target kedekatan jarak.

---

## 🔬 Arsitektur & Metodologi
- **Representasi Emosi:** Representasi vektor multidimensi dalam ruang retrieval.
- **Algoritma / Pendekatan:** Retrieval density filtering dengan penalti redundansi antarkandidat tetangga terdekat.
- **Metrik Evaluasi:** Coverage metric, diversity score, dan akurasi representasi data luaran.

---

## 💡 Temuan Utama & Hasil
- Pemberian penalti jarak antar elemen terpilih mencegah pengelompokan berlebih (*clustering collapse*) dan meningkatkan variasi hasil secara signifikan.

---

## ⚠️ Limitasi & Gap Riset (Peluang untuk TA Kita)
> [!IMPORTANT]
> **Apa kelemahan paper ini yang diselesaikan oleh TA kita?**
- Diterapkan pada domain teks NLP, bukan musik audio.

---

## 🔗 Relevansi dengan Tugas Akhir
- Memberikan landasan teoritis bagi rancangan tahap kedua pada pipeline kita: mencegah pemilihan lagu yang berulang pada area emosi yang sama.
- Terkait dengan: [[Matriks-Sintesis]] | [[Dataset-DEAM]] | [[Bab-2-Tinjauan-Pustaka]]
