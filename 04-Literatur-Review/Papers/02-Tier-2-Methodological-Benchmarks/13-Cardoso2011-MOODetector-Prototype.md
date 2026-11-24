---tier: "Tier 2: Methodological Benchmarks & Audio Similarity"

title: "Bedah Kritis: MOODetector: A Prototype Software Tool for Mood-based Playlist Generation"
author: "Bruno Cardoso & K. E. Voigt"
year: 2011
citekey: "cardoso2011moodetector"
venue: "Proceedings of the International Conference on Knowledge Discovery and Information Retrieval (KDIR 2011)"
quartile: "International Conference Proceedings (Historical Seminal Baseline)"
dataset: "Katalog MP3 Pribadi (1.200 trek)"
metode: "Thayer Energy-Stress 2D Plane + Heuristic Path Planning"
gap_utama: "Ketiadaan perangkat lunak prototipe interaktif yang memungkinkan pengguna menggambar lintasan kurva suasana hati secara grafis."
tags:
  - literatur
  - paper-review
  - historical-baseline
  - path-planning
  - moodetector
status: "audited"
aliases:
  - Cardoso2011-MOODetector-Prototype
  - MOODetector Cardoso
---
# 📖 Bedah Kritis: Prototipe MOODetector (Cardoso & Voigt, 2011)
## *MOODetector: A Prototype Software Tool for Mood-based Playlist Generation*

> **Objek Bedah:** Prosiding KDIR 2011 (28 KB text)  
> **Kedudukan dalam TA:** **Pionir Konsep Perancangan Lintasan Jalur Emosi Playlist (Bab II Subbab 2.2)**

---

## 🧭 Step 0 & 1: Konteks & Abstrak Kuantitatif
* **Konteks:** Salah satu makalah pionir paling awal yang mengusulkan konsep *Path of Emotions* (lintasan emosi) pada ruang 2D Thayer (Energy vs Stress).
* **Hasil & Temuan:**
  * Menunjukkan bahwa pengguna sangat tertarik menggambar rute suasana hati secara grafis (misal: kurva parabola dari santai ke energik lalu kembali santai).
  * Namun, pencarian lagu hanya berbasis pencocokan koordinat terdekat tanpa mempertimbangkan fitur akustik pendukung atau kontinuitas musik internal.

---

## 💡 Step 9 & 10: Sintesis & Research Gap
1. **Fakta Terbukti:** Konsep navigasi playlist berbasis lintasan kurva emosi telah diminati sejak lebih dari satu dekade lalu.
2. **Research Gap TA Kita:** MOODetector masih sangat sederhana (hanya model heuristik 2D statis). Riset kita mengembangkannya dengan formulasi matematika trajektori modern, dataset standar DEAM 2 Hz, dan reranking akustik anti-boundary jump.
