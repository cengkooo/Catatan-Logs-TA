---
title: "Bedah Kritis: Synthesizrr: Generating Diverse Datasets with Retrieval Augmentation (Divekar et al., 2023)"
author: "Chandresh Divekar et al."
year: 2023
citekey: "divekar2023synthesizrr"
venue: "Advances in Neural Information Processing Systems (NeurIPS 2023)"
quartile: "Top-Tier AI Conference (Core A*)"
dataset: "Large-Scale Unlabeled Corpora & Dense Retrieval Benchmarks"
metode: "Retrieval-Augmented Generation (RAG) + Density-Aware Diversity Sampling"
gap_utama: "Metode augmentasi data dan seleksi retrieval konvensional cenderung mengalami *mode collapse* dan redundansi pada area padat (*dense clusters*)."
tags:
  - literatur
  - paper-review
  - retrieval-augmentation
  - diversity-sampling
  - neurips
status: "audited"
---

# 📖 Bedah Kritis: Synthesizrr Retrieval Diversity (Divekar et al., 2023)
## *Synthesizrr: Generating Diverse Datasets with Retrieval Augmentation*

> **Objek Bedah:** Naskah NeurIPS 2023 (121 KB text)  
> **Kedudukan dalam TA:** **Prinsip Pencegahan Lagu Duplikat & Diversitas Kandidat (Bab III Subbab 3.3)**

---

## 🧭 Step 0 & 1: Konteks & Abstrak Kuantitatif
* **Konteks:** Meneliti bagaimana algoritma retrieval terarah dapat mengambil kandidat data yang relevan sekaligus tetap menjaga diversitas (*diversity-aware retrieval*).
* **Hasil Kuantitatif Konkret:**
  * Mencegah redundansi pengambilan data sebesar **+22%** dibanding pencarian tetangga terdekat sederhana (*naive nearest neighbors*).

---

## 💡 Step 9 & 10: Sintesis & Research Gap
1. **Fakta Terbukti:** Pengambilan berbasis tetangga terdekat harus dilengkapi mekanisme eliminasi duplikasi dan pembobotan diversitas agar hasil sekuensial tidak monoton.
2. **Kegunaan untuk TA:** Diterapkan langsung pada algoritma KNN Playlist kita: mencegah lagu dari artis yang sama terpilih berurutan (*artist repetition penalty*) dan memastikan variasi trek terjaga di sepanjang mood-arc.
