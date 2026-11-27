---
title: "Alur Metode Usulan: Dynamic Trajectory Alignment & Penalti BJC"
tags:
  - eksperimen
  - metode-usulan
  - trajectory-alignment
  - diagram
  - tugas-akhir
date: 2026-11-26
---

# Alur Metode Usulan (*Dynamic Trajectory Alignment* & $\mathcal{BJC}$)

Mengacu langsung pada **Bab III Subbab 3.3** ([chapter-3.tex](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/proposal-penelitian-andryano-123140205/chapters/chapter-3.tex)) untuk menjawab **Rumusan Masalah 1 (RM 1)**.

> [!tip] Versi Node-Graph Interaktif (Obsidian Canvas)
> Buka **[[Alur-Metode-Usulan-Trajectory-Alignment.canvas]]** di Obsidian untuk tampilan *node-graph* interaktif.
> Pembanding baseline: **[[Alur-Uji-Coba-Baseline-Gaur]]** ([[Alur-Uji-Coba-Baseline-Gaur.canvas]]).

---

## 1. Diagram Alur Pipeline Usulan

```mermaid
flowchart TD
    subgraph S1["Tahap 1: Ekstraksi Dinamika 2 Hz & KNN Retrieval"]
        A["1. Time-Series DEAM 2 Hz\n30s stabil (60 timestamp)\n[Bab III 3.2]"]
        B["2. Ekstraksi Intro & Outro\n6 titik awal & 6 titik akhir\n[Eq. 3.3]"]
        C["3. Interpolasi Waypoint\nM titik acuan w_j\n[Eq. 3.1]"]
        D["4. Tahap 1: KNN Retrieval\nAmbil K=20 kandidat terdekat\n[Eq. 3.2]"]
        A --> B --> C --> D
    end

    subgraph S2["Tahap 2: Dynamic Trajectory Alignment Reranker"]
        E["5. Vektor Target Lintasan\nu_j = w_j - w_{j-1}\n[Eq. 3.4]"]
        F["6. Penyelarasan Trajektori\nCosine Sim(t_k, u_j)\n[Eq. 3.5]"]
        G["7. Penalti Boundary Jump\nBJC outro-intro fisik\n[Eq. 3.6 - Wang 2024]"]
        H["8. Skor Komposit\nGabung bobot w1, w2, w3\n[Eq. 3.7]"]
        D --> E --> F --> G --> H
    end

    subgraph S3["Tahap 3: Seleksi & Iterasi Playlist"]
        I["9. Pilih Skor Terendah\nLagu L_k* terbaik"]
        J{"j < M ?"}
        K["10. Playlist Mood-Arc\nPanjang M in {5,10,15}"]
        H --> I --> J
        J -- "Ya" --> D
        J -- "Tidak" --> K
    end
```

---

## 2. Rincian Formulasi Matematis (Bab III 3.3)

> [!info] Tahap 1 — Waypoint & Kandidat KNN (`3.3.1`)
> - **Waypoint ($\mathbf{w}_j$, Eq. 3.1):** $\mathbf{w}_j = \mathbf{p}_{\mathrm{start}} + \frac{j-1}{M-1}(\mathbf{p}_{\mathrm{target}} - \mathbf{p}_{\mathrm{start}})$
> - **KNN Euclidean (Eq. 3.2):** Mengambil **$K = 20$** kandidat terdekat di ruang 2D $V\text{-}A$ terhadap titik rata-rata $\bar{\mathbf{p}}_k$.

> [!abstract] Tahap 2 — Dynamic Trajectory Alignment & $\mathcal{BJC}$ (`3.3.2`)
> - **Vektor Internal Lagu (Eq. 3.3):** $\vec{\mathbf{t}}_k = \mathbf{p}_{\mathrm{outro}, k} - \mathbf{p}_{\mathrm{intro}, k}$, dengan *intro* = rata-rata 6 *timestamp* awal (15–18s) dan *outro* = rata-rata 6 *timestamp* akhir (42–45s).
> - **Keselarasan Arah (Eq. 3.5):** $\mathrm{Sim}_{\mathrm{traj}}(\vec{\mathbf{t}}_k, \vec{\mathbf{u}}_j) = \frac{\vec{\mathbf{t}}_k \cdot \vec{\mathbf{u}}_j}{\|\vec{\mathbf{t}}_k\|_2 \|\vec{\mathbf{u}}_j\|_2} \in [-1, +1]$.
> - **Boundary Jump Cost (Eq. 3.6):** $\mathcal{BJC}(L_{j-1}, L_k) = \|\mathbf{p}_{\mathrm{outro}}(L_{j-1}) - \mathbf{p}_{\mathrm{intro}}(L_k)\|_2$.
> - **Skor Komposit (Eq. 3.7):** $w_1 \frac{d_{\mathrm{target}}}{\max(d)} + w_2 \frac{1 - \mathrm{Sim}_{\mathrm{traj}}}{2} + w_3 \mathcal{BJC}$ ($w_1 + w_2 + w_3 = 1{,}0$), **skor terendah dipilih**.


---

## 3. Kamus Istilah Teknis & Arti Rumus (Bahasa Sederhana)

> [!note] Panduan Membaca Istilah Teknis
> - **Time-Series 2 Hz:** Data emosi lagu yang dicatat setiap setengah detik ($0{,}5$ detik = 2 titik per detik).
> - **30s Stabil (buang 15s awal):** 15 detik pertama pada klip DEAM dibuang karena pendengar/anotator masih beradaptasi di awal lagu (*transient*), sehingga hanya detik ke-15 sampai ke-45 (**60 titik**) yang dipakai.
> - **Intro & Outro:** Bagian pembuka lagu (rata-rata 6 titik awal, detik 15–18) dan penutup lagu (rata-rata 6 titik akhir, detik 42–45).
> - **Dynamic Trajectory Alignment:** Menyelaraskan arah gerak emosi di dalam lagu (dari *intro* ke *outro*) agar searah dengan alur perjalanan playlist.
> - **Boundary Jump Cost ($\mathcal{BJC}$):** "Biaya penalti" atau ukuran seberapa jauh mood melompat saat lagu sebelumnya berakhir (*outro*) dan lagu berikutnya dimulai (*intro*).

> [!tip] Arti Rumus Matematika
> - **Eq. 3.1 ($\mathbf{w}_j$):** Membagi lintasan dari mood awal ke mood tujuan menjadi $M$ titik perhentian (*waypoint*) yang berjarak sama.
> - **Eq. 3.2 ($d_{\mathrm{target}}$):** Jarak garis lurus (Euclidean) antara titik perhentian $\mathbf{w}_j$ dengan mood rata-rata lagu, dipakai di Tahap 1 untuk mengambil $K=20$ kandidat terdekat.
> - **Eq. 3.3 ($\vec{\mathbf{t}}_k = \mathbf{p}_{\mathrm{outro},k} - \mathbf{p}_{\mathrm{intro},k}$):** Anak panah arah perubahan mood di dalam satu lagu (dari pembuka menuju penutupnya).
> - **Eq. 3.4 ($\vec{\mathbf{u}}_j = \mathbf{w}_j - \mathbf{w}_{j-1}$):** Anak panah arah perjalanan mood yang diinginkan oleh playlist pada langkah ke-$j$.
> - **Eq. 3.5 ($\mathrm{Sim}_{\mathrm{traj}} \in [-1, +1]$):** Mengukur kekompakan arah antara panah lagu ($\vec{\mathbf{t}}_k$) dan panah playlist ($\vec{\mathbf{u}}_j$). Nilai $+1$ = searah persis, $0$ = tegak lurus, $-1$ = berlawanan arah.
> - **Eq. 3.6 ($\mathcal{BJC}$):** Jarak lompatan emosi tepat di sambungan antara akhir lagu lama dan awal lagu baru. Semakin kecil, sambungannya semakin mulus.
> - **Eq. 3.7 ($\mathrm{Score}(L_k)$):** Gabungan 3 nilai (jarak ke target + ketidaksearahan trajektori + lompatan sambungan) dengan bobot $w_1 + w_2 + w_3 = 1$. Lagu dengan **skor paling kecil** yang dipilih.
