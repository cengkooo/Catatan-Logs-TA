---
title: "Alur Blind A/B Listening Test (Evaluasi Perseptual Manusia)"
tags:
  - eksperimen
  - blind-ab-test
  - user-study
  - diagram
  - tugas-akhir
date: 2026-11-26
---

# Alur *Blind A/B Listening Test* (Uji Persepsi Manusia)

Mengacu pada **Bab III Subbab 3.6** ([chapter-3.tex](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/proposal-penelitian-andryano-123140205/chapters/chapter-3.tex)) untuk menjawab **Rumusan Masalah 3 (RM 3)**.

> [!tip] Versi Node-Graph Interaktif (Obsidian Canvas)
> Buka **[[Alur-Blind-AB-Listening-Test.canvas]]** di Obsidian untuk tampilan *node-graph* interaktif.

---

## 1. Diagram Alur Uji Dengar Manusia

```mermaid
flowchart TD
    subgraph S1["1. Pembuatan Stimulus Audio Terisolasi"]
        A["1. Seleksi 6 Pasang Transisi\nQ3->Q1, Q1->Q4, Q4->Q1\n[Bab III 3.6.2]"]
        B["2. Audio Stitching Klip 30s\n15s outro + 15s intro\nVersi A Usulan vs B Gaur"]
        C["3. Blind Randomization\nCounterbalanced order\n[Bab III 3.6.1]"]
        A --> B --> C
    end

    subgraph S2["2. Sampling, Etika, & Pengambilan Data"]
        D["4. Sampling & Etika UU PDP\nN >= 30, Informed Consent\nAnonimisasi R01-R30"]
        E["5. Sesi Dengar Terstandar\nHeadphone tertutup 65-70 dB\n[Bab III 3.6.3]"]
        F["6. Kuesioner Likert 5 Poin\n3 dimensi persepsi\n[Bab III 3.6.4]"]
        C --> D --> E --> F
    end

    subgraph S3["3. Uji Reliabilitas & Statistik Inferensial"]
        G["7. Cronbach's Alpha\nSyarat alpha >= 0,70\n[Eq. 3.12]"]
        H["8. Uji Beda MOS Wilcoxon\nMOS Usulan > MOS Gaur\nAlpha = 0,05"]
        I["9. Korelasi Spearman r_s\nMetrik S & BJC vs MOS\n[Eq. 3.13]"]
        F --> G --> H --> I
    end
```

---

## 2. Rincian Protokol Uji Dengar (Bab III 3.6)

> [!info] Stimulus & Kontrol Bias (`3.6.1`–`3.6.2`)
> - **6 Pasang Stimulus:** 2 pasang diagonal (**Q3 $\to$ Q1**), 2 pasang relaksasi (**Q1 $\to$ Q4**), 2 pasang naik energi (**Q4 $\to$ Q1**).
> - **Klip 30 Detik (Eq. 3.11):** `15s outro` $L_j$ + `15s intro` $L_{j+1}$, dibuat versi **A (Usulan)** dan **B (Gaur)** lalu diacak *counterbalanced* tanpa memberi tahu responden algoritma penghasilnya.

> [!abstract] Responden, Etika, & Instrumen (`3.6.3`–`3.6.4`, `3.6.6`)
> - **Sampel:** Minimal **$N \ge 30$** responden (usia 19–25 tahun, pendengar aktif $\ge 1$ jam/hari) di ruang tenang dengan *headphone* tertutup (**65–70 dB SPL**).
> - **Etika (UU PDP No. 27 Tahun 2022):** *Informed consent* tertulis (durasi 15–20 menit) dan anonimisasi kode `R01–R30`.
> - **Likert 5 Poin (3 Dimensi):** (1) *Transition smoothness*, (2) *Acoustic & energy continuity*, (3) *Emotional naturalness*.

> [!warning] Analisis Statistik (`3.6.5`)
> - **Reliabilitas:** *Cronbach's Alpha* $\alpha \ge 0{,}70$ (Eq. 3.12).
> - **Uji Beda:** *Wilcoxon Signed-Rank Test* ($\alpha = 0{,}05$) menguji $\mathrm{MOS}_{\mathrm{Usulan}} > \mathrm{MOS}_{\mathrm{Gaur}}$.
> - **Korelasi:** Korelasi peringkat *Spearman* ($r_s$, Eq. 3.13) antara metrik objektif ($\mathcal{S}$, $\mathcal{BJC}$) dan skor MOS manusia.
