---
title: Bank Pertanyaan Dosen & Simulasi Sidang Sempro
tags:
  - bimbingan
  - sempro
  - ujian
---

# ❓ Bank Pertanyaan Dosen & Simulasi Sempro

Kumpulan potensi pertanyaan dari dosen penguji beserta strategi argumentasi ilmiahnya.

---

### Q1: Kenapa tidak langsung pakai Deep Learning (e.g. RNN / Transformer / RL) saja untuk generate playlist?
* **Jawaban Kunci:** 
  Tujuan utama penelitian ini adalah menguji secara terkontrol **apakah penambahan sinyal trajectory dinamis pada lagu membawa pengaruh nyata terhadap smoothness playlist**. Menggunakan pipeline 2-tahap (KNN + filtering geometris berbasis trajectory alignment) memberikan interpretabilitas penuh yang memungkinkan kita membandingkan secara *fair* (*apple-to-apple*) dengan replikasi *state-of-the-art* Gaur & Donnelly (2020), tanpa terdistorsi oleh bias *black-box* model generatif kompleks.

---

### Q2: Apa bukti bahwa lagu-lagu di dataset DEAM benar-benar memiliki dinamika mood internal yang signifikan?
* **Jawaban Kunci:** 
  Pada tahap EDA Sprint 1 ([[Dataset-DEAM]]), kita menghitung magnitudo variansi dan arah vektor pergeseran titik awal ($t_0$) ke titik akhir ($t_{\text{end}}$) di ruang Valence-Arousal. Sebagian besar lagu menunjukkan perpindahan kuadran emosi atau pergeseran arousal yang signifikan (> threshold $\epsilon$), membuktikan bahwa informasi dinamis ini membawa sinyal riil, bukan sekadar noise.

---

### Q3: Bagaimana metrik "Smoothness" dan "Evenness" dihitung secara kuantitatif?
* **Jawaban Kunci:**
  Mengacu pada formulasi evaluasi Gaur & Donnelly:
  - **Smoothness:** Mengukur deviasi sudut dan jarak Euclidean pada titik batas transisi antara akhir lagu $i$ ($t_{\text{end}}$) dengan awal lagu $i+1$ ($t_0$).
  - **Evenness:** Mengukur konsistensi laju perubahan mood sepanjang kurva target (*target mood-arc*).
  Rincian formula ada di [[Bab-3-Metodologi]].
