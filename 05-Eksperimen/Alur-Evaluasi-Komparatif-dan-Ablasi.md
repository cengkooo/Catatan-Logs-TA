---
title: "Alur Evaluasi Komparatif, Uji Ablasi (ON vs OFF), & Wilcoxon"
tags:
  - eksperimen
  - evaluasi
  - ablation-study
  - wilcoxon
  - diagram
  - tugas-akhir
date: 2026-11-26
---

# Alur Evaluasi Komparatif, Uji Ablasi, & Uji Statistik

Mengacu pada **Bab III Subbab 3.5** ([chapter-3.tex](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/proposal-penelitian-andryano-123140205/chapters/chapter-3.tex)) untuk menjawab **Rumusan Masalah 2 (RM 2)**.

> [!tip] Versi Node-Graph Interaktif (Obsidian Canvas)
> Buka **[[Alur-Evaluasi-Komparatif-dan-Ablasi.canvas]]** di Obsidian untuk tampilan *node-graph* interaktif.

---

## 1. Diagram Alur Evaluasi & Ablasi

```mermaid
flowchart TD
    subgraph S1["1. Model & Konfigurasi yang Diadu"]
        M1["1A. Naive Random\nKontrol batas bawah"]
        M2["1B. Baseline Gaur\nStatic-Point Matching"]
        M3["1C. Model Usulan\nAblasi OFF vs ON\n[Meyes 2019; Bendada 2023]"]
    end

    subgraph S2["2. Eksekusi Benchmark Terkontrol"]
        D["2. Korpus DEAM\nHoldout split, seed=42"]
        R["3. 6 Rute Kuadran\n540 batch run per model"]
        P["4. Output Playlist\nKoordinat intro & outro"]
        M1 --> D
        M2 --> D
        M3 --> D
        D --> R --> P
    end

    subgraph S3["3. Metrik & Uji Signifikansi"]
        E["5. Hitung 3 Metrik\nS, E, dan CBJC\n[Eq. 3.8 - 3.10]"]
        W["6. Wilcoxon Signed-Rank\nAlpha = 0,05 berpasangan\n[Bab III 3.5.3 & 3.5.5]"]
        K["7. Keputusan Hipotesis\nS turun >= 15% & p < 0,05"]
        P --> E --> W --> K
    end
```

---

## 2. Rincian Komponen Evaluasi (Bab III 3.5)

> [!info] Komparasi 3 Model + Uji Ablasi (`3.5.2` & `3.5.5`)
> - **Naive Random:** Pemilihan acak sebagai batas bawah (*lower bound*).
> - **Baseline Gaur (2023/2024):** *Static-point matching* 2-tahap KNN + 12D PCA.
> - **Uji Ablasi Model Usulan (`meyes2019ablation`, `bendada2023scalable`):**
>   1. **Trajectory Filter OFF ($\lambda_{\mathrm{traj}} = 0$):** Hanya penyaringan titik statis tanpa arah trajektori & $\mathcal{BJC}$.
>   2. **Trajectory Filter ON ($\lambda_{\mathrm{traj}} > 0$):** *Pipeline* lengkap dengan penyelarasan *outro-intro* & $\mathcal{BJC}$.

> [!warning] Metrik Objektif & Uji Statistik (`3.5.1` & `3.5.3`)
> - **Boundary Smoothness ($\mathcal{S}$, Eq. 3.8):** Rata-rata jarak lonjakan $\|\mathbf{p}_{\mathrm{outro}}(L_j) - \mathbf{p}_{\mathrm{intro}}(L_{j+1})\|_2$ (target turun **$\ge 15\%$**).
> - **Evenness Index ($\mathcal{E}$, Eq. 3.9):** Variansi jarak langkah antar-waypoint.
> - **Cumulative BJC ($\mathcal{CBJC}$, Eq. 3.10):** Akumulasi total penalti lompatan batas sepanjang playlist.
> - **Wilcoxon Signed-Rank ($\alpha = 0{,}05$):** Menguji signifikansi selisih $\mathcal{S}$, $\mathcal{E}$, $\mathcal{CBJC}$ pada seluruh **540 *batch run***.


---

## 3. Kamus Istilah Teknis & Arti Rumus (Bahasa Sederhana)

> [!note] Panduan Membaca Istilah Teknis
> - **Naive Random:** Pemilih lagu acak tanpa aturan apa pun, dipakai sebagai batas bawah (*lower bound*) untuk memastikan model jauh lebih baik daripada menebak acak.
> - **Uji Ablasi (*Ablation Study*):** Pengujian dengan cara "mematikan" satu komponen (*Trajectory Filter OFF* vs *ON*) sementara hal lain dibuat sama persis, untuk membuktikan bahwa perbaikan hasil memang berasal dari komponen tersebut.
> - **Seed = 42:** Kunci pengacakan tetap supaya setiap kali eksperimen diulang, hasil pengacakannya sama persis (*reproducible*).
> - **Holdout Split:** Memisahkan data uji agar tidak pernah disentuh saat penyetelan model.
> - **Wilcoxon Signed-Rank Test ($\alpha = 0{,}05$):** Uji statistik berpasangan (tanpa syarat data harus berdistribusi normal) untuk membuktikan apakah selisih skor antara dua model benar-benar nyata ($p < 0{,}05$) atau sekadar kebetulan.

> [!tip] Arti Rumus Matematika
> - **Eq. 3.8 ($\mathcal{S}$, *Boundary Smoothness*):** Rata-rata besarnya lompatan mood di setiap sambungan antarlagu (*outro* ke *intro*). **Semakin kecil semakin halus** (target turun $\ge 15\%$).
> - **Eq. 3.9 ($\mathcal{E}$, *Evenness Index*):** Variansi jarak langkah antar-waypoint. Nilai mendekati $0$ berarti kecepatan perpindahan mood stabil dan seragam.
> - **Eq. 3.10 ($\mathcal{CBJC}$, *Cumulative BJC*):** Total penjumlahan seluruh lompatan batas dari lagu pertama sampai lagu terakhir dalam satu playlist.
