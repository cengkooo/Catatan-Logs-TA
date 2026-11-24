---
title: Kamus Notasi & Glosarium Tugas Akhir
tags:
  - glosarium
  - notasi
  - matematika
---

# 📍 Kamus Notasi & Glosarium Tugas Akhir

Daftar istilah dan notasi matematis standar untuk menjaga konsistensi penulisan di draf bab dan LaTeX (`thesis.tex`).

---

## 🔣 Notasi Matematis

| Notasi | Makna / Definisi | Domain |
| :--- | :--- | :--- |
| $V$ | **Valence** (Tingkat kesenangan emosi: negatif/sedih $\rightarrow$ positif/senang) | $[-1.0, 1.0]$ atau $[1, 9]$ |
| $A$ | **Arousal** (Tingkat energi emosi: tenang/pasif $\rightarrow$ intens/berenergi) | $[-1.0, 1.0]$ atau $[1, 9]$ |
| $\mathbf{p}_i(t)$ | Titik posisi lagu $i$ di ruang emosi pada waktu $t$: $(V_i(t), A_i(t))$ | $\mathbb{R}^2$ |
| $\vec{\mathbf{v}}_i$ | Vektor trajectory mood internal lagu $i$: $\mathbf{p}_i(t_{\text{end}}) - \mathbf{p}_i(t_0)$ | $\mathbb{R}^2$ |
| $\theta_i$ | Sudut arah pergerakan emosi lagu: $\arctan2(\Delta A, \Delta V)$ | $[-\pi, \pi]$ |
| $\mathcal{S}$ | Metrik **Smoothness** (Kelancaran transisi antarlagu berturutan) | $\mathbb{R}^+$ |
| $\mathcal{E}$ | Metrik **Evenness** (Keseragaman laju perubahan mood pada playlist) | $\mathbb{R}^+$ |

---

## 📖 Istilah Kunci (Glosarium)

* **Mood Arc:** Pola lintasan emosi yang direncanakan sepanjang durasi playlist (misal: kurva naik dari relaksasi menuju fokus berenergi tinggi).
* **Static-Point Matching:** Metode konvensional yang menyamakan lagu dengan titik target hanya berdasarkan rata-rata $V$ dan $A$ seluruh durasi lagu.
* **Trajectory Alignment:** Penyelarasan arah pergerakan emosi internal lagu dengan vektor target transisi playlist.
* **DEAM (Database for Emotion Analysis in Music):** Dataset musik berisi 1802 klip lagu berdurasi 45 detik dengan anotasi emosi kontinu berfrekuensi 2 Hz.
