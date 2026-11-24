---
title: "Flow Moods: Recommending Music by Moods on Deezer"
author: "Théo Bontempelli, Benjamin Chapus, François Rigaud, et al."
year: 2022
citekey: "bontempelli2022flowmoods"
dataset: "Deezer Production Catalog (jutaan lagu, jutaan pengguna aktif)"
metode: "Multi-Armed Bandit + Mood-Constrained Collaborative Filtering"
tags:
  - literatur
  - paper-review
status: "read"
---

# 📖 Flow Moods: Recommending Music by Moods on Deezer

- **Penulis:** `Théo Bontempelli, Benjamin Chapus, François Rigaud, et al.` (2022)
- **Citekey LaTeX:** `\cite{bontempelli2022flowmoods}`
- **Dataset:** `Deezer Production Catalog (jutaan lagu, jutaan pengguna aktif)`
- **Metode Utama:** `Multi-Armed Bandit + Mood-Constrained Collaborative Filtering`

---

## 🎯 Masalah & Tujuan Riset
- **Permasalahan:** Pengguna layanan streaming menginginkan pengalaman mendengarkan yang dipersonalisasi sesuai suasana hati saat itu (context-aware) tanpa harus menyusun playlist secara manual.
- **Tujuan:** Merancang dan menerapkan sistem rekomendasi mood industri berskala besar (Flow Moods) yang menyajikan radio musik berbasis mood.

---

## 🔬 Arsitektur & Metodologi
- **Representasi Emosi:** 6 kategori mood industri: You & Me, Motivation, Chill, Melancholy, Focus, dan Party.
- **Algoritma / Pendekatan:** Pipeline dua tahap: penyaringan kandidat berbasis kecocokan mood (filter audio/metadata) diikuti perangkingan bandit kontekstual personalisasi pengguna.
- **Metrik Evaluasi:** A/B Testing pada pengguna nyata Deezer: rasio retensi, stream duration, dan skip rate.

---

## 💡 Temuan Utama & Hasil
- Fitur Flow Moods meningkatkan total waktu dengar pengguna dan mengurangi skip rate secara drastis pada skenario aktivitas harian.

---

## ⚠️ Limitasi & Gap Riset (Peluang untuk TA Kita)
> [!IMPORTANT]
> **Apa kelemahan paper ini yang diselesaikan oleh TA kita?**
- Hanya mendukung kategori mood statis diskrit per sesi radio; tidak mendukung transisi mood dinamis (mood arc) antarlagu.

---

## 🔗 Relevansi dengan Tugas Akhir
- Bukti empiris industri streaming bahwa rekomendasi berbasis mood sangat diminati pendengar, memperkuat latar belakang Bab 1.
- Terkait dengan: [[Matriks-Sintesis]] | [[Dataset-DEAM]] | [[Bab-2-Tinjauan-Pustaka]]
