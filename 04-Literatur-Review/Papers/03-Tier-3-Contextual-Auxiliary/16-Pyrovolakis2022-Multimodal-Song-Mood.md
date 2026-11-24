---
tier: "Tier 3: Contextual & Auxiliary Reference"
title: "Bedah Kritis: Multi Modal Song Mood Detection with Deep Learning (Pyrovolakis et al., 2022)"
author: "Konstantinos Pyrovolakis et al."
year: 2022
citekey: "pyrovolakis2022multimodal"
venue: "Expert Systems with Applications, Vol. 209, Article 118284"
quartile: "Q1 Scopus (Top 10% AI & Expert Systems, Elsevier)"
dataset: "MoodyLyrics & Million Song Dataset (MSD)"
metode: "Dual-Branch Deep Learning: CNN-BiLSTM (Spectrogram) + BERT (Lyrics) + Cross-Modal Attention"
gap_utama: "Model penggabungan fitur (concatenation) sederhana gagal memodelkan interaksi non-linier antara sinyal musik dan lirik lagu."
tags:
  - literatur
  - paper-review
  - multimodal
  - deep-learning
  - expert-systems
status: "audited"
aliases:
  - Pyrovolakis2022-Multimodal-Song-Mood
  - Multimodal Pyrovolakis
---
# 📖 Bedah Kritis: Multimodal Deep Learning MER (Pyrovolakis et al., 2022)
## *Multi Modal Song Mood Detection with Deep Learning*

> **Objek Bedah:** Jurnal Q1 Elsevier ESWA (68 KB text)  
> **Kedudukan dalam TA:** **Rujukan Pemodelan Kompleksitas Mood Musik (Bab II Subbab 2.3)**

---

## 🧭 Step 0 & 1: Konteks & Abstrak Kuantitatif
* **Konteks:** Merancang model kecerdasan buatan multimodal tingkat lanjut yang menggunakan mekanisme atensi silang (*cross-modal attention*) antara audio spektrogram dan embedding teks BERT.
* **Hasil Kuantitatif Konkret:**
  * Meraih akurasi klasifikasi 4 kelas mood sebesar **85.7%**, mengungguli arsitektur unimodal sebesar **+7.3%**.
  * Analisis atensi membuktikan bahwa bagian intro dan chorus lagu memiliki bobot atensi tertinggi dalam menentukan suasana hati pendengar.

---

## 💡 Step 9 & 10: Sintesis & Research Gap
1. **Fakta Terbukti:** Bagian intro (awal) dan outro (akhir) lagu memegang peranan krusial dalam persepsi transisi mood musik.
2. **Research Gap TA Kita:** Pyrovolakis dkk. membuktikan pentingnya segmen lagu lokal, namun hanya menggunakannya untuk klasifikasi kategori; belum dimanfaatkan untuk penyelarasan transisi antar lagu pada playlist.
