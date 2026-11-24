---
title: "MOODetector: A Prototype Software Tool for Mood-based Playlist Generation"
author: "Luís Cardoso, Renato Panda, Rui Pedro Paiva"
year: 2011
citekey: "cardoso2011moodetector"
dataset: "AllMusic Taxonomy & Handcrafted Feature Corpora"
metode: "Support Vector Machines (SVM) on Thayer's Energy-Stress Plane"
tags:
  - literatur
  - paper-review
status: "read"
---

# 📖 MOODetector: A Prototype Software Tool for Mood-based Playlist Generation

- **Penulis:** `Luís Cardoso, Renato Panda, Rui Pedro Paiva` (2011)
- **Citekey LaTeX:** `\cite{cardoso2011moodetector}`
- **Dataset:** `AllMusic Taxonomy & Handcrafted Feature Corpora`
- **Metode Utama:** `Support Vector Machines (SVM) on Thayer's Energy-Stress Plane`

---

## 🎯 Masalah & Tujuan Riset
- **Permasalahan:** Kurangnya perangkat lunak interaktif yang memungkinkan pengguna menavigasi koleksi lagu pribadi berdasarkan suasana hati.
- **Tujuan:** Mengembangkan prototipe perangkat lunak (MOODetector) yang mengklasifikasikan trek musik dan menyusun playlist berbasis mood pengguna.

---

## 🔬 Arsitektur & Metodologi
- **Representasi Emosi:** Thayer's 2D Emotion Model (Energy vs Stress).
- **Algoritma / Pendekatan:** Ekstraksi fitur audio standar (MARSYAS) + klasifikasi SVM + path finding sederhana antar kuadran.
- **Metrik Evaluasi:** Akurasi klasifikasi SVM dan uji kegunaan perangkat lunak (usability testing).

---

## 💡 Temuan Utama & Hasil
- Visualisasi 2D memberikan pengalaman navigasi musik yang jauh lebih intuitif bagi pendengar awam.

---

## ⚠️ Limitasi & Gap Riset (Peluang untuk TA Kita)
> [!IMPORTANT]
> **Apa kelemahan paper ini yang diselesaikan oleh TA kita?**
- Model awal yang masih mengandalkan fitur akustik tradisional dan titik statis diskrit.

---

## 🔗 Relevansi dengan Tugas Akhir
- Rujukan historis penting untuk tinjauan pustaka mengenai evolusi playlist generation berbasis mood spasial.
- Terkait dengan: [[Matriks-Sintesis]] | [[01-Dataset-DEAM-dan-Eksplorasi|Dataset-DEAM]] | [[Bab-2-Tinjauan-Pustaka]]
