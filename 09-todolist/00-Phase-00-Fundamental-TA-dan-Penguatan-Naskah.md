---
title: "Phase 00: Fundamental TA 16 Pilar & Penguatan Draf Naskah"
tags:
  - todolist
  - phase-0
  - fundamental-ta
  - naskah-draft
  - ablation-study
  - blind-ab-test
status: "IN PROGRESS"
target_output: "Naskah Bab I–III Konsisten (chapter-1.tex .. chapter-3.tex) & Blueprint Fundamental 16 Pilar"
---

# Phase 00: Fundamental TA (16 Pilar) & Penguatan Draf Naskah

> **Tujuan Fase 0:** Mengunci fondasi ilmiah Tugas Akhir secara utuh dan konsisten sebelum memproduksi slide atau menjalankan eksperimen penuh. Seluruh keputusan di fase ini menjadi acuan tunggal untuk naskah LaTeX (`proposal-penelitian-andryano-123140205/chapters/`) dan slide Typst (`Slides/`).

---

## Bagian A: Fondasi 16 Pilar Tugas Akhir (Anti-Goyah)

| Pilar | Ketetapan Terkunci | Checklist Audit di Naskah (`chapters/`) |
| :---: | :--- | :--- |
| **1. Topik / Area Riset** | *Music Information Retrieval* (MIR) & *Sequential Music Recommendation*, sub-masalah *Mood-Arc Playlist Generation* (pergerakan mood sekuensial sepanjang sesi dengar). | - [ ] Pastikan istilah bidang & sub-masalah konsisten di Bab I (`chapter-1.tex`). |
| **2. Judul** | *"Mood-Arc Playlist Generation Berbasis Dynamic Mood Trajectory Menggunakan K-Nearest Neighbors dan Trajectory Alignment"* (menyebut objek, pendekatan, dan metode). | - [ ] Cek kesesuaian antara `config/informations.tex`, `Slides/metadata.toml`, dan `chapter-1.tex`. |
| **3. Latar Belakang & Urgency** | Layanan *streaming* menuntut *playlist* sesuai aktivitas; pendekatan *static-point* gagal menangkap pergerakan emosi internal, sedangkan lompatan kasar ($\Delta > 0,25$) menaikkan *skip rate* hingga 37%. | - [ ] Pastikan alur industri $\rightarrow$ keterbatasan statis $\rightarrow$ fakta DEAM 98,11% mengalir logis di `chapter-1.tex`. |
| **4. Research Gap** | Pendekatan *static-point* Gaur & Donnelly (2023) mereduksi lagu menjadi satu titik $(\bar{v}, \bar{a})$ dan belum mempertimbangkan *trajectory* emosi dinamis sebagai kriteria *filtering* / penyelarasan transisi *outro-intro*. | - [ ] Pastikan kalimat gap riset tercantum tegas satu kalimat sebelum Rumusan Masalah (`chapter-1.tex:21`). |
| **5. Rumusan Masalah** | 3 pertanyaan eksperimental terukur (bukan ya/tidak): (1) Desain *pipeline* 2-tahap + *trajectory alignment*, (2) Kinerja $\mathcal{S}$, $\mathcal{E}$, $\mathcal{CBJC}$ vs baseline Gaur & Random, (3) Penerimaan perseptual (*Blind A/B*) & korelasinya dengan metrik objektif. | - [ ] Audit 3 butir RM di `chapter-1.tex:27-31`. |
| **6. Tujuan & Manfaat** | 3 Tujuan nyambung 1:1 dengan 3 RM (target $\mathcal{S}$ turun $\ge 15\%$, Wilcoxon $p < 0,05$, *Blind A/B* $N \ge 30$); Manfaat dipisah **Teoretis** (MIR/psikoakustik) dan **Praktis** (cetak biru *streaming*). | - [ ] Audit keterhubungan 1:1 RM $\leftrightarrow$ TP & pemisahan Manfaat di `chapter-1.tex:33-64`. |
| **7. Batasan / Scope** | 2D $V-A$ Russell $[-1,0, +1,0]$; DEAM 1.802 klip (buang 15s awal $\rightarrow$ 30s stabil / 60 *timestamp*, 2 Hz); *Blind A/B* fokus pada klip sambungan 30s ($N \ge 30$); KNN deterministik; non-*real-time*; panjang playlist $M \in \{5, 10, 15\}$. | - [ ] Verifikasi seluruh 7 butir batasan di `chapter-1.tex:46-55` sebagai tameng sidang. |
| **8. Landasan Teori** | Model Sirkumpleks Russell (1980) + validasi modern Belaref (2024), *Music Emotion Recognition* dinamis, representasi *trajectory* & *Boundary Jump Cost* (Wang 2024 REMAST), serta *Sequential Playlist Generation*. | - [ ] Audit kelengkapan rumus dan sitasi di `chapter-2.tex` (`2.1`). |
| **9. Dataset (DEAM)** | Sumber terbuka akademik DEAM: 1.802 klip 45s, anotasi kontinu 2 Hz, *song-level holdout split* (anti *data leakage*). Keterbatasan: ukuran lagu terbatas, klip pendek 45s, variabilitas anotasi *crowd*. | - [ ] Pastikan alasan kecocokan & keterbatasan DEAM tertulis eksplisit di `chapter-3.tex` (`3.2`). |
| **10. Metode (Kontribusi Inti)** | Prapemrosesan (30s stabil, normalisasi/smoothing) $\rightarrow$ Tahap 1 *KNN Candidate Retrieval* $\rightarrow$ Tahap 2 *Dynamic Trajectory Alignment* & penalti $\mathcal{BJC}$ $\rightarrow$ penyusunan *playlist* + *hyperparameter* ($k$, $\lambda$, panjang segmen ujung). | - [ ] Verifikasi seluruh persamaan (`eq:norm` s.d. `eq:score`) di `chapter-3.tex` (`3.3`). |
| **11. Baseline** | Mempertahankan 2 baseline dari literatur/kontrol: (1) **Replikasi Gaur & Donnelly (2023/2024)** (*static-point matching*) dan (2) **Naive Random Retrieval**. | - [ ] Pastikan skenario komparasi di `chapter-3.tex:156` dan Tabel 3.1 sinkron. |
| **12. Evaluasi, Ablasi, & Statistik** | Metrik kualitas *arc* (*Linearity Smoothness*, *Evenness Index* $\mathcal{E}$) & kualitas transisi (*Boundary Smoothness* $\mathcal{S}$, $\mathcal{CBJC}$); skenario diagonal (Q3–Q1) + lintas kuadran; **Uji Ablasi (*Trajectory Filter ON vs OFF*)** berlandaskan `meyes2019ablation` & `bendada2023scalable`; *Wilcoxon Signed-Rank* ($\alpha = 0,05$); *Blind A/B* ($N \ge 30$, Likert 5 poin, *Cronbach's Alpha* $\ge 0,70$, Spearman). | - [ ] Tambahkan subbagian/paragraf **Uji Ablasi (*Trajectory Filter ON vs OFF*)** ke `chapter-3.tex` (`3.5`) dengan sitasi `\cite{meyes2019ablation, bendada2023scalable}`. |
| **13. Hipotesis & Kontribusi** | **Hipotesis:** *Metode berbasis trajectory mood-arc menghasilkan Boundary Smoothness ($\mathcal{S}$) lebih rendah secara signifikan daripada static-point matching tanpa menurunkan Evenness, serta lebih disukai pendengar pada Blind A/B test, karena mempertimbangkan kecocokan vektor outro-intro.* **Kontribusi:** Replikasi (pipeline KNN 2-tahap Gaur, metrik PCC/Evenness) vs **Baru** (ekstraksi trajektori 2 Hz, *trajectory alignment* + $\mathcal{BJC}$, evaluasi lintas kuadran + ablasi + *Blind A/B*). | - [ ] Pastikan pemisahan kontribusi baru vs replikasi tertulis jelas di `chapter-1.tex` / `chapter-3.tex`. |
| **14. Tools & Environment** | Python, PyTorch, Librosa, NumPy/SciPy/scikit-learn, GPU/CPU lokal, versi library terkunci, *fixed random seed*, serta dokumentasi kode terstruktur untuk *Code Walkthrough* (10% bobot sidang). | - [ ] Verifikasi Subbab `3.4 Lingkungan Eksperimen` di `chapter-3.tex` mencantumkan versi, *seed*, dan struktur repositori. |
| **15. Timeline & Risiko (+ Fallback)** | Milestone bulanan (Studi Pustaka $\rightarrow$ Implementasi $\rightarrow$ Eksperimen & Ablasi $\rightarrow$ *Blind A/B* $\rightarrow$ Penulisan & Sidang). **Fallback Plan:** Jika *trajectory filter* tidak signifikan di seluruh rute, fokus pada analisis diagnostik per kuadran & pembuktian kelemahan artefak PCC statis pada rute lintas kuadran. | - [ ] Tambahkan catatan manajemen risiko & rencana cadangan ke log riset / jadwal Bab III. |
| **16. Etika & Validitas** | Lisensi akademik DEAM, *informed consent* & perlindungan data pribadi responden sesuai **UU PDP No. 27 Tahun 2022**, bias genre/anotasi *crowd*, serta **Threats to Validity** (Internal: pilihan *hyperparameter*/*smoothing*; Eksternal: generalisasi klip 45s ke lagu penuh). | - [ ] Tambahkan paragraf singkat *Threats to Validity* & bias dataset pada `chapter-3.tex` (`3.5` / `3.6`). |

---

## Bagian B: Langkah Penguatan Draf Naskah LaTeX

- [ ] **B.1 Integrasi Uji Ablasi di `chapter-3.tex`:** Tambahkan penjelasan protokol *Ablation Study* (*Trajectory Filter ON vs OFF* / variasi $\lambda = 0$ vs $\lambda > 0$) pada Subbab 3.5 menggunakan sitasi `\cite{meyes2019ablation, bendada2023scalable}`.
- [ ] **B.2 Integrasi *Threats to Validity* & Limitasi DEAM di `chapter-3.tex`:** Pastikan bias anotasi *crowd*, keterbatasan klip 45 detik, serta validitas internal/eksternal tercatat eksplisit.
- [ ] **B.3 Verifikasi Sitasi & Kompilasi LaTeX:** Jalankan `latexmk` / `pdflatex` pada `proposal-penelitian-andryano-123140205/thesis.tex` setelah pembaruan untuk memastikan tidak ada sitasi `[?]` (undefined citation) dari `meyes2019ablation` maupun `bendada2023scalable`.
- [ ] **B.4 Lanjut ke Slide Typst:** Setelah naskah Fase 0 terkunci, eksekusi [[09-todolist/14-Task-Generate-Slides-Typst-dari-Naskah]].
