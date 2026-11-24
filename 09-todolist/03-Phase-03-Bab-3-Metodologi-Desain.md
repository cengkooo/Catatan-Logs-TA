---
title: "Fase 03: Penulisan Bab 3 Metodologi Penelitian"
tags:
  - todolist
  - phase-3
  - bab3
  - naskah
status: "TODO"
aliases:
  - Phase-03-Bab-3-Metodologi-Desain
  - Bab 3 Metodologi Todolist
---
# 📐 Fase 03: Penulisan Bab 3 (Metodologi Penelitian)

> **Tujuan Akhir:** Menyusun metodologi riset matematis dan arsitektur pipeline yang presisi pada [[Bab-3-Metodologi]] dan LaTeX `chapters/chapter-3.tex`.
> **Standar:** Setiap persamaan matematika diberi nomor `(3.x)`, wajib ada diagram alir sistem, dan definisi variabel terperinci.

---

## 🎯 Sub-Fase 3.1: Alur Penelitian & Kerangka Konseptual (3.1)

- [ ] **Langkah 3.1.1 — Diagram Alir Sistem Utuh:**
  - Buat diagram alir pipeline dua tahap yang diperkaya *Trajectory Alignment*:
    1. Input: Titik Awal $P_{\text{start}}$, Titik Akhir $P_{\text{target}}$, Jumlah Lagu $M$, Bobot $\alpha$.
    2. Interpolasi Waypoint $P_i$.
    3. Tahap 1: KNN Candidate Retrieval di ruang V-A.
    4. Tahap 2: Ekstraksi Vektor Trajectory $\mathbf{v}_{\text{song}}$ & Trajectory Alignment Scoring.
    5. Seleksi Lagu Optimal & Penyusunan Playlist Final.
    6. Evaluasi Metrik Smoothness & Evenness.
- [ ] **Langkah 3.1.2 — Penjelasan Naratif Diagram:** Tulis penjelasan per blok modul.

---

## 🎯 Sub-Fase 3.2: Karakteristik & Pemrosesan Dataset DEAM (3.2)

- [ ] **Langkah 3.2.1 — Spesifikasi Korpus DEAM:**
  - 1.802 klip audio (format MP3, 45 detik, sampling rate anotasi 2 Hz $\rightarrow$ 90 timestamp per lagu).
  - Justifikasi pemilihan DEAM berbasis survei 47 dataset (rujuk [[Spreadsheet-Penjelasan-Dataset]]).
- [ ] **Langkah 3.2.2 — Preprocessing Sinyal Dinamis:**
  - Normalisasi nilai Valence dan Arousal ke rentang normatif $[-1, 1]$.
  - Pembersihan derau (*noise reduction*) menggunakan *moving average filter* jendela 3 timestamp (1,5 detik) untuk mereduksi fluktuasi persepsi sesaat.

---

## 🎯 Sub-Fase 3.3: Formulasi Matematis Pipeline (3.3)

- [ ] **Langkah 3.3.1 — Formulasi Waypoint Mood Arc:**
  $$P_i = P_{\text{start}} + \frac{i}{M} \cdot (P_{\text{target}} - P_{\text{start}}), \quad i \in \{1, \dots, M\}$$
- [ ] **Langkah 3.3.2 — Ekstraksi Trajectory Lagu:**
  - Vektor arah perubahan mood internal lagu:
    $$\mathbf{v}_{\text{song}} = (\Delta V, \Delta A) = (V_{\text{end}} - V_{\text{start}}, A_{\text{end}} - A_{\text{start}})$$
  - Atau regresi slope linear $\beta_V, \beta_A$.
- [ ] **Langkah 3.3.3 — Scoring Fungsi Seleksi Tahap 2 (Kombinasi Linier):**
  $$\text{Score}(L_j) = \alpha \cdot \text{Sim}_{\text{audio}}(L_j, L_{i-1}) + (1 - \alpha) \cdot \cos(\mathbf{v}_{\text{arc}}, \mathbf{v}_{\text{song}, j})$$

---

## 🎯 Sub-Fase 3.4: Metrik Evaluasi Kinerja Playlist (3.4)

- [ ] **Langkah 3.4.1 — Smoothness ($S$):** Kehalusan transisi antarlagu bertetangga.
- [ ] **Langkah 3.4.2 — Evenness ($E$):** Keseragaman jarak transisi di sepanjang playlist.
- [ ] **Langkah 3.4.3 — Trajectory Alignment Error:** Deviasi arah pergerakan lagu terhadap garis vektor mood-arc.
