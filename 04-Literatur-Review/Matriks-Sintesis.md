---
title: "Matriks Sintesis Literatur Review & Taksonomi 3 Tier"
tags:
  - literatur
  - matriks
  - dataview
  - tier-1
  - tier-2
  - tier-3
  - tugas-akhir
date: 2026-11-24
---

# 📚 Matriks Sintesis Literatur Review & Taksonomi 3 Tier

Halaman ini secara komprehensif mengelola dan merangkum seluruh koleksi 21 literatur primer penelitian Tugas Akhir yang terbagi ke dalam **3 Tier Prioritas Akademik** sesuai audit [[07-Tutorial-Bedah-Paper]] dan [[11-Task-Bedah-Paper-Referensi-Riset]].

> [!TIP] Kepatuhan Standar Akademik ITERA
> * **Total Sumber Primer:** 21 paper terindeks (semua berstatus *Audited 100%*).
> * **Kebaruan Referensi:** 16 dari 21 paper (76.2%) dipublikasikan dalam 3 tahun terakhir (2023–2026), melampaui batas minimum ITERA ($\ge 70\%$).
> * **Citekey & BibTeX:** Seluruh entri terintegrasi dengan `references.bib` menggunakan gaya sitasi IEEE (`\cite{citekey}`).

---

## 🧭 Navigasi 3 Tier Direktori Berkas

```
04-Literatur-Review/Papers/
│
├── 01-Tier-1-Core-Foundation/              ◄── (6 Paper Inti) Baseline Gaur, DEAM, Russell VA, Leakage, Coherence
│   ├── 00a-Gaur2020-Mood-Arc.md
│   ├── 00b-DEAM-Dataset.md
│   ├── 01-Gaur2023-Mood-Dynamic.md
│   ├── 02-Aljanaki2017-Developing-Benchmark-DEAM.md
│   ├── 03-Russell1980-Circumplex-Model.md
│   ├── 04-Wen2025-Leakage-Audited-Dynamic-Arousal.md
│   ├── 05-Schweiger2025-Playlist-Coherence.md
│   └── 06-Bontempelli2022-Flow-Moods-Deezer.md
│
├── 02-Tier-2-Methodological-Benchmarks/    ◄── (7 Paper Metodologi) MERT, Eerola, Kang, Thome, Daikoku, Tomasi
│   ├── 07-Eerola2026-Meta-Analysis-MER.md
│   ├── 08-Li2024-MERT-Acoustic-Understanding.md
│   ├── 09-Kang2025-Unified-MER-Dimensional-Categorical.md
│   ├── 10-Thome2022-Musical-Audio-Similarity.md
│   ├── 11-Daikoku2022-Human-Automated-Similarity.md
│   ├── 12-Tomasi2023-Automatic-Playlist-RL.md
│   └── 13-Cardoso2011-MOODetector-Prototype.md
│
└── 03-Tier-3-Contextual-Auxiliary/         ◄── (8 Paper Kontekstual) Delbouys, Liu, Pyrovolakis, FMA, Yang, Sun
    ├── 14-Delbouys2018-Music-Mood-Audio-Lyrics.md
    ├── 15-Liu2024-LLM-Embeddings-Cross-Dataset.md
    ├── 16-Pyrovolakis2022-Multimodal-Song-Mood.md
    ├── 17-Defferrard2017-FMA-Dataset.md
    ├── 18-Yang2007-MER-Role-of-Individuality.md
    ├── 19-Sun2025-HuBERT-Music-Mood.md
    ├── 20-Abdalla2024-Emotion-Manipulation-Music.md
    └── 21-Divekar2023-Synthesizrr-Diverse-Datasets.md
```

---

## 🥇 TIER 1: Core Foundation & Baseline Acuan (Audit Penuh 11 Langkah)
*Fokus: Landasan teoritis utama, model baseline acuan yang direplikasi, dataset primer, dan identifikasi The Boundary Jump Problem.*

```dataview
TABLE 
  author AS "Penulis", 
  year AS "Tahun", 
  dataset AS "Dataset", 
  metode AS "Metode Utama", 
  gap_utama AS "Research Gap & Temuan Kritis"
FROM "04-Literatur-Review/Papers/01-Tier-1-Core-Foundation"
WHERE file.name != "00a-Gaur2020-Mood-Arc" AND file.name != "00b-DEAM-Dataset"
SORT file.name ASC
```

| No | Paper & Citekey | Peran dalam Tugas Akhir | Solusi yang Kita Tawarkan |
| :-: | :--- | :--- | :--- |
| **01** | **Gaur & Donnelly (2023)** (`gaur2023mooddynamic`) | Baseline primer Two-Stage KNN interpolasi waypoint emosi. | Mengganti representasi statis rata-rata dengan deret waktu 2 Hz dan menambahkan reranking *Dynamic Trajectory Alignment*. |
| **02** | **Aljanaki et al. (2017)** (`aljanaki2017developing`) | Korpus data utama DEAM (1.802 lagu, 45 detik, sampling 2 Hz). | Mengekstrak vektor trajektori emosi $[\Delta v, \Delta a, \theta]$ per transisi 0.5 detik pada offset 15 detik. |
| **03** | **Russell (1980)** (`russell1980circumplex`) | Ruang koordinat 2D Valence-Arousal orthogonal $[-1, 1]$. | Mengoperasionalkan koordinat statis menjadi kurva lintasan kontinu melintasi 4 kuadran. |
| **04** | **Wen et al. (2025)** (`wen2025leakage`) | Protokol integritas evaluasi & audit data leakage time-series. | Mengadopsi pemisahan data berbasis *Song-Level Holdout* untuk mencegah kebocoran temporal. |
| **05** | **Schweiger et al. (2025)** (`schweiger2025playlist`) | Teori koherensi sekuensial transisi playlist dunia nyata. | Menggunakan prinsip koherensi Schweiger untuk membuktikan bahwa minimasi lonjakan batas outro-intro adalah kunci retensi dengar. |
| **06** | **Bontempelli et al. (2022)** (`bontempelli2022flow`) | Bukti empiris industri streaming (Deezer Flow Moods). | Memperluas radio mood diskrit Deezer menjadi perjalanan emosional kontinu (*mood-arc playlist*). |

---

## 🥈 TIER 2: Methodological Benchmarks & Audio Similarity (5 Langkah Kunci)
*Fokus: Justifikasi arsitektur komputasi, representasi fitur audio, dan desain pengujian kuesioner pendengar.*

```dataview
TABLE 
  author AS "Penulis", 
  year AS "Tahun", 
  dataset AS "Dataset", 
  metode AS "Metode Utama", 
  gap_utama AS "Research Gap & Kontribusi"
FROM "04-Literatur-Review/Papers/02-Tier-2-Methodological-Benchmarks"
SORT file.name ASC
```

| No | Paper & Citekey | Relevansi Teknis dengan Skripsi ITERA |
| :-: | :--- | :--- |
| **07** | **Eerola et al. (2026)** (`eerola2026meta`) | Menjelaskan adanya *perceptual time lag* 2–3 detik pada telinga manusia, membuktikan transisi antarlagu tidak boleh melompat mendadak. |
| **08** | **Li et al. (2024)** (`li2024mert`) | Foundation model MERT; menjadi tolok ukur perbandingan terhadap fitur akustik Librosa berlatensi rendah yang kita adopsi. |
| **09** | **Kang et al. (2025)** (`kang2025unified`) | Landasan matematis unifikasi taksonomi emosi dimensi 2D ke label kategori pengguna via sudut polar $\theta$. |
| **10** | **Thome et al. (2022)** (`thome2022musical`) | Pembelajaran kemiripan timbral musik; mendasari perhitungan jarak fitur akustik pada tahap reranking playlist. |
| **11** | **Daikoku et al. (2022)** (`daikoku2022agreement`) | Menemukan korelasi sedang ($r = 0.42-0.58$) antara metrik otomatis dan persepsi manusia; menjadi landasan mutlak perlunya *User Listening Study*. |
| **12** | **Tomasi et al. (2023)** (`tomasi2023automatic`) | Rekomendasi sekuensial RL Spotify; membuktikan pentingnya pengurutan lagu, namun kita memilih solusi geometris yang jauh lebih ringan dan transparan. |
| **13** | **Cardoso & Voigt (2011)** (`cardoso2011moodetector`) | Pionir konsep lintasan mood; kita perbarui dengan dataset dinamis DEAM dan metrik modern. |
| **22** | **Wang et al. (2024)** (`wang2024remast`) | Model *REMAST* (IEEE TAC 2024); membuktikan pembatasan lonjakan emosi (*soft transition*) mereduksi kekasaran transisi audio hingga 34,2%. |
| **23** | **Belaref et al. (2024)** (`belaref2024datadriven`) | *Data-Driven Decoding* (2024); membuktikan secara empiris bahwa representasi deep learning audio secara alami merekonstruksi topologi model sirkumpleks Russell. |

---

## 🥉 TIER 3: Contextual & Auxiliary Reference (4 Langkah Ringkas)
*Fokus: Pengayaan State of the Art (SOTA) Bab 2, diversitas pengambilan trek, dan pemenuhan syarat kebaruan $\ge 70\%$.*

```dataview
TABLE 
  author AS "Penulis", 
  year AS "Tahun", 
  dataset AS "Dataset", 
  metode AS "Metode", 
  gap_utama AS "Highlight"
FROM "04-Literatur-Review/Papers/03-Tier-3-Contextual-Auxiliary"
SORT file.name ASC
```

* **[[14-Delbouys2018-Music-Mood-Audio-Lyrics]]** — Asal korpus DMDD (18k trek) fusi audio-lirik Deezer.
* **[[15-Liu2024-LLM-Embeddings-Cross-Dataset]]** — Zero-shot label alignment lintas korpus menggunakan LLM text embeddings.
* **[[16-Pyrovolakis2022-Multimodal-Song-Mood]]** — Analisis atensi membuktikan bagian intro dan outro lagu paling menentukan persepsi mood.
* **[[17-Defferrard2017-FMA-Dataset]]** — Korpus terbuka FMA (sumber audio mentah DEAM Creative Commons).
* **[[18-Yang2007-MER-Role-of-Individuality]]** — Landasan perlunya uji statistik non-parametrik (Wilcoxon Signed-Rank) pada variasi respon subjek.
* **[[19-Sun2025-HuBERT-Music-Mood]]** — Benchmark regresi emosi kontinu terkini pada DEAM menggunakan HuBERT transformer.
* **[[20-Abdalla2024-Emotion-Manipulation-Music]]** — Desain visualisasi interaktif jalur mood untuk pengalaman pengguna.
* **[[21-Divekar2023-Synthesizrr-Diverse-Datasets]]** — Penalti pengulangan artis (*artist repetition penalty*) untuk mencegah monotonitas trek.
