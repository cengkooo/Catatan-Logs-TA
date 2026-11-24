---
title: "Mood-Dynamic Playlist: Interpolating a Path of Emotions Using a KNN Algorithm"
author: "Shaurya Gaur"
year: 2023
citekey: "gaur2023mooddynamic"
dataset: "DMDD (Deezer Mood Detection Dataset) - 18.644 lagu"
metode: "K-Nearest Neighbors (KNN) + Linear Mood Arc Interpolation"
tags:
  - literatur
  - paper-review
status: "read"
---

# 📖 Mood-Dynamic Playlist: Interpolating a Path of Emotions Using a KNN Algorithm

- **Penulis:** `Shaurya Gaur` (2023)
- **Citekey LaTeX:** `\cite{gaur2023mooddynamic}`
- **Dataset:** `DMDD (Deezer Mood Detection Dataset) - 18.644 lagu`
- **Metode Utama:** `K-Nearest Neighbors (KNN) + Linear Mood Arc Interpolation`

---

## 🎯 Masalah & Tujuan Riset
- **Permasalahan:** Layanan streaming musik konvensional menyajikan playlist dengan mood yang statis dan monoton. Pengguna sering kali membutuhkan perjalanan transisi emosional bertahap (mood-arc) dari satu kondisi perasaan ke kondisi lain (misalnya dari stres/agitasi menuju tenang).
- **Tujuan:** Merancang dan mengevaluasi algoritma berbasis K-Nearest Neighbors (KNN) yang menginterpolasi lintasan emosi pada ruang 2D Valence-Arousal untuk menghasilkan playlist mood-arc yang mulus.

---

## 🔬 Arsitektur & Metodologi
- **Representasi Emosi:** Model Dimensi 2D Valence-Arousal (Russell), di mana setiap lagu dipetakan ke 1 titik koordinat statis rata-rata.
- **Algoritma / Pendekatan:** Interpolasi linier Euclidean antara titik awal dan titik akhir emosi, dilanjutkan dengan pencarian kandidat lagu terdekat menggunakan KNN berbasis jarak Euclidean/Cosinus, serta metrik Smoothness dan Evenness.
- **Metrik Evaluasi:** Smoothness (kelancaran transisi antarlagu bertetangga), Evenness (keseragaman jarak lonjakan), dan perbandingan terhadap shuffle acak.

---

## 💡 Temuan Utama & Hasil
- Pendekatan interpolasi KNN menghasilkan playlist yang secara signifikan lebih mulus (smooth) dan teratur (even) dibandingkan pengacakan standar dalam transisi suasana hati.

---

## ⚠️ Limitasi & Gap Riset (Peluang untuk TA Kita)
> [!IMPORTANT]
> **Apa kelemahan paper ini yang diselesaikan oleh TA kita?**
- Dataset DMDD hanya menyediakan satu nilai rata-rata statis per lagu. Akibatnya, dinamika internal lagu (perubahan mood dari verse ke chorus) terabaikan, berisiko memicu transisi tajam yang mengganggu pendengar.

---

## 🔗 Relevansi dengan Tugas Akhir
- Menjadi baseline primer dan titik pijak utama Tugas Akhir ini. Kita mereplikasi arsitektur KNN ini dan meningkatkannya dengan Trajectory Alignment berbasis dataset DEAM.
- Terkait dengan: [[Matriks-Sintesis]] | [[Dataset-DEAM]] | [[Bab-2-Tinjauan-Pustaka]]
