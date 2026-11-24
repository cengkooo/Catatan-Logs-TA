---
tier: "Tier 3: Contextual & Auxiliary Reference"
title: "Bedah Kritis: Music Emotion Recognition: The Role of Individuality (Yang et al., 2007)"
author: "Yi-Hsuan Yang et al."
year: 2007
citekey: "yang2007music"
venue: "Proceedings of the ACM International Conference on Multimedia (ACM MM 2007)"
quartile: "Top-Tier Multimedia Conference (Core A*)"
dataset: "195 Klip Musik Klasik & Pop dengan Anotasi Multi-Subjek"
metode: "Support Vector Regression (SVR) + Individual Difference Modeling + Ranking Adaptation"
gap_utama: "Penggunaan nilai emosi rata-rata tunggal (*ground truth consensus*) mengaburkan variasi preferensi dan sensitivitas emosional antar individu."
tags:
  - literatur
  - paper-review
  - individuality
  - subjective-perception
  - acm-mm
status: "audited"
aliases:
  - Yang2007-MER-Role-of-Individuality
  - Individuality MER Yang
---
# 📖 Bedah Kritis: Peran Individualitas dalam MER (Yang et al., 2007)
## *Music Emotion Recognition: The Role of Individuality*

> **Objek Bedah:** Naskah ACM Multimedia 2007 (40 KB text)  
> **Kedudukan dalam TA:** **Landasan Subjektivitas Evaluasi Pendengaran (Bab II Subbab 2.1)**

---

## 🧭 Step 0 & 1: Konteks & Abstrak Kuantitatif
* **Konteks:** Meneliti sejauh mana perbedaan latar belakang musik, suasana hati personal, dan kepribadian mempengaruhi persepsi emosi lagu.
* **Hasil Kuantitatif Konkret:**
  * Korelasi persepsi antar subjek manusia (*inter-subject agreement*) berkisar antara **$r = 0.55 - 0.75$**, membuktikan bahwa ada komponen emosi konsensus yang objektif, namun tetap ada variasi subjektif sebesar ~30%.

---

## 💡 Step 9 & 10: Sintesis & Research Gap
1. **Fakta Terbukti:** Persepsi emosi musik memiliki komponen konsensus umum (dapat dioptimasi oleh algoritma komputasi) dan komponen personal.
2. **Kegunaan untuk TA:** Memperkuat dasar pengujian *User Listening Study* kita bahwa evaluasi transisi playlist harus menggunakan uji statistik non-parametrik (seperti Wilcoxon Signed-Rank Test) yang memperhitungkan variasi pasangan respon per individu.
