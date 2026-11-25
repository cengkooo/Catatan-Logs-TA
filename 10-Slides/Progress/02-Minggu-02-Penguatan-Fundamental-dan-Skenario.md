---
title: "Outline Slide Bimbingan Mingguan #02: Penguatan Fundamental & Pemilihan Skenario Evaluasi"
tags:
  - bimbingan
  - slides
  - typst
  - progres
  - minggu-02
  - draft
---

# Outline Slide Bimbingan Mingguan #02 (Draf)

> **Tanggal Pembuatan:** 25 November 2026  
> **Jadwal Bimbingan:** 27 November 2026 (Tentatif)  
> **Dosen Pembimbing:** Hafiz Budi Firmansyah, S.Kom., M.Sc.  
> **Target Lokasi File Typst:** `Slides/02-Progress/02-Minggu-02-Penguatan-Fundamental-dan-Skenario/progres_m02.typ` (belum dibuat)  
> **Sumber Rujukan Utama:** [[02-Daily-Logs/2026-11-24]], [[03-Bimbingan/04-Lembar-Diskusi-Skenario-User-Study]]

---

## 1. Matriks Status Progres (Target vs Realisasi)

| Kategori | Butir Capaian / Pekerjaan | Status | Catatan / Bukti |
| :--- | :--- | :---: | :--- |
| **Tercapai (Done)** | 1. Bedah forensik 23 paper primer dan klasifikasi 3 Tier | Selesai | `04-Literatur-Review/Papers/` (Tier 1, 2, 3) |
| | 2. Revalidasi modern teori Russell 1980 (Opsi A: *Golden Pairing*) | Selesai | Wang et al. (2024) REMAST & Belaref et al. (2024) ($r > 0,82$) |
| | 3. Integrasi hasil replikasi baseline Gaur ke Bab III Subbab 3.5.4 (Tabel 3.1) | Selesai | Cosine PCC 0,9781; Euclidean 0,9876; Manhattan 0,9762 |
| | 4. Penyusunan lengkap draf Bab I, II, dan III untuk kedua skenario | Selesai | `06-Naskah-Draft/01-Skenario-...` & `02-Skenario-...` |
| **Sedang Berjalan (In Progress)** | 1. Persiapan transfer naskah skenario terpilih ke LaTeX UNESCO | Berjalan | `proposal-penelitian-andryano-123140205/` |
| | 2. Penyusunan dan latihan slide Seminar Proposal 10 menit (14 slide) | Berjalan | `Slides/01-Sempro/sempro_slides.typ` |
| **Butuh Keputusan (Blocked)** | 1. Pemilihan final skenario evaluasi TA: murni komputasional vs evaluasi ganda (*User Study*) | Diskusi | Perlu arahan Pak Hafiz sebelum finalisasi LaTeX |

---

## 2. Bukti Teknis & Temuan Literatur (Deep Dive)

- **Benchmark Awal Baseline Gaur (Tabel 3.1 pada Bab III Subbab 3.5.4):**
  - *Cosine* PCC: `0,9781`
  - *Euclidean* PCC: `0,9876`
  - *Manhattan* PCC: `0,9762`
- **Landasan Teori Mutakhir (Memenuhi Syarat Kebaruan $\ge 70\%$ 3 Tahun Terakhir):**
  - **Belaref et al. (2024):** Membuktikan secara matematis bahwa representasi AI audio modern membentuk struktur sirkumpleks Russell ($r > 0,82$), sehingga pemilihan model 2D $V-A$ memiliki landasan kontemporer.
  - **Wang et al. (2024 - REMAST, IEEE TAC):** Menunjukkan bahwa peredaman lonjakan transisi emosi (*Soft Transition*) mereduksi kekacauan progresi akor hingga 50,6% ($p < 0,03$), menjadi landasan metrik *Boundary Jump Cost* ($\mathcal{BJC}$).
  - **Wen et al. (2025):** Menegaskan penggunaan *Song-Level Holdout Split* untuk mencegah kebocoran data (*data leakage*).

---

## 3. Konsultasi Kendala & Usulan Solusi (Diskusi Bimbingan)

- **Keputusan yang Diminta dari Dosen Pembimbing:**
  - Penetapan skenario penelitian pada Bab I sampai Bab III (mengacu pada [[03-Bimbingan/04-Lembar-Diskusi-Skenario-User-Study]]).
- **Opsi Skenario yang Diajukan:**
  - **Opsi 1 (`01-Skenario-Murni-Komputasional`):** Fokus pada evaluasi metrik objektif (3 rumusan masalah/tujuan, 540 *batch run*, uji Wilcoxon). Waktu eksekusi lebih terkendali, namun tidak mengukur persepsi pendengar secara langsung.
  - **Opsi 2 (`02-Skenario-Dual-Evaluation-User-Study`, Direkomendasikan):** Menggabungkan evaluasi komputasional dan *User Study* pada Subbab 3.6 (uji *Blind A/B*, klip 30 detik, skala Likert 5 poin, $N \ge 30$, *Cronbach's Alpha*, dan uji Wilcoxon) untuk menjawab pertanyaan penguji mengenai kualitas transisi menurut persepsi manusia.
- **Keputusan / Arahan Dosen (Diisi saat sesi bimbingan):**
  - _[Catat di sini dan salin ke [[03-Bimbingan/01-Notulensi-Bimbingan]]]_

---

## 4. Rencana Kerja Pekan Depan (Next Week Action Items)

1. [ ] **Kompilasi LaTeX Final UNESCO:** Memindahkan naskah Bab I sampai Bab III dari skenario terpilih ke `thesis.tex` dan memverifikasi format margin, penomoran halaman, serta daftar pustaka.
2. [ ] **Finalisasi Slide Sempro:** Menyelaraskan isi [`Slides/01-Sempro/sempro_slides.typ`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Slides/01-Sempro/sempro_slides.typ) dengan skenario terpilih dan target durasi 9 menit 30 detik.
3. [ ] **Kelengkapan Administrasi Sempro:** Memeriksa status prasyarat pada [[03-Bimbingan/03-Tracker-Prasyarat-Sempro]].
- **Target Tanggal Bimbingan Berikutnya:** `YYYY-MM-DD`
