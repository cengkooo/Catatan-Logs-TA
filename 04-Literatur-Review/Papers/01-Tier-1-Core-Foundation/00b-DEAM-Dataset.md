---tier: "Tier 1: Core Foundation & Baseline Acuan"

title: "The MediaEval Database for Emotion Analysis in Music (DEAM)"
author: "Anna Aljanaki et al."
year: 2017
citekey: "aljanaki2017deam"
dataset: "DEAM Dataset"
metode: "Continuous Valence-Arousal Crowdsourcing Annotation"
tags:
  - literatur
  - paper-review
status: "read"
aliases:
  - DEAM-Dataset
---
# 📖 The MediaEval Database for Emotion Analysis in Music (DEAM)

- **Penulis:** `Anna Aljanaki, Yi-Hsuan Yang, Mohammad Soleymani` (2017)
- **Citekey LaTeX:** `\cite{aljanaki2017deam}`
- **Dataset:** `DEAM (1802 klip musik, 45 detik/klip)`
- **Metode Utama:** `Dynamic continuous 2 Hz rating via MTurk`

---

## 🎯 Karakteristik Dataset
- Anotasi emosi dilakukan secara kontinu oleh manusia setiap 0.5 detik (frekuensi sampling 2 Hz).
- Terdapat nilai rata-rata dan deviasi standar per timestamp untuk dimensi **Valence** dan **Arousal**.
- Menyediakan file audio asli (format WAV/MP3) dan fitur akustik ekstraksi OpenSMILE / Essentia.

---

## 💡 Relevansi dengan Tugas Akhir
- Dataset inilah yang memungkinkan kita mengekstrak **trajectory pergerakan emosi** per lagu.
- Format waktu kontinu 0.5s memungkinkan penghitungan turunan arah perubahan mood ($\Delta V / \Delta t, \Delta A / \Delta t$).
