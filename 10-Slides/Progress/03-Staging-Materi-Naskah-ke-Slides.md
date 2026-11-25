---
title: "Staging Materi Naskah Proposal ke Slide Bimbingan #01 (6 Slide — Baseline, Bab 1, & Gaur 2023)"
tags:
  - slides
  - progress
  - staging
  - bab-1
  - baseline
  - gaur-2023
  - typst
date: 2026-11-25
---

# Staging Materi: Baseline, Bab 1 Latar Belakang, & Gaur (2023) (6 Slide)

> **Acuan Utama:** [`proposal-penelitian-andryano-123140205/chapters/chapter-1.tex`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/proposal-penelitian-andryano-123140205/chapters/chapter-1.tex) (Subbab 1.1–1.3 + catatan teknis DEAM dari 1.4), hasil replikasi baseline di [`metrics_comparison_deam.csv`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Slides/assets/experiments/metrics_comparison_deam.csv), dan tesis fundamental **Gaur (2023)** (`gaur2023mooddynamic`).  
> **Batasan Ruang Lingkup:** Dokumen ini tidak memuat materi Bab 2 maupun Bab 3.  
> **Target Slide Typst:** [`Slides/02-Progress/01-Minggu-01-Baseline-DEAM/progres_m01.typ`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Slides/02-Progress/01-Minggu-01-Baseline-DEAM/progres_m01.typ) (6 Slide)

---

## Pemetaan Materi per Slide (6 Slide)

### Slide 1: Cover & Identitas Bimbingan #01
- **Komponen Typst:** `#cover-slide(...)`
- **Judul:** Replikasi Baseline Gaur (2023) & Pemetaan Masalah Bab I pada Korpus DEAM
- **Subjudul:** Laporan Progres Bimbingan Tugas Akhir (Pertemuan #01)
- **Identitas:** Andryano Kadarisman (`123140205`), Pembimbing: Hafiz Budi Firmansyah, S.Kom., M.Sc.

---

### Slide 2: Matriks Status Progres Pekan Ini
- **Komponen Typst:** `#slide-header(...)` + 3 `#card-box(...)` (`DONE`, `IN_PROGRESS`, `BLOCKED`) + `#memory-recall(...)`
- **Tercapai (`DONE`):**
  - Replikasi baseline Gaur (2023) pada 1.802 klip korpus DEAM dan 540 *batch run*.
  - Penyusunan Bab I (`chapter-1.tex`: Latar Belakang, Rumusan Masalah, Tujuan, Batasan, Manfaat).
  - Kajian pustaka fundamental Gaur (2023): *Mood-Dynamic Playlist: Interpolating a Path of Emotions Using a KNN Algorithm*.
- **Sedang Berjalan (`IN_PROGRESS`):**
  - Penyempurnaan slide Bimbingan #01 (`progres_m01.typ`) untuk pemaparan perdana ke pembimbing.
  - Persiapan penyusunan bab lanjutan setelah arahan pembimbing.
- **Butuh Diskusi (`BLOCKED`):**
  - Validasi pembimbing atas keselarasan Bab I dan temuan *The Boundary Jump Problem*.

---

### Slide 3: Latar Belakang, Limitasi Gaur (2023), & Gap Riset
- **Komponen Typst:** `#slide-header(...)` + 2 `#card-box(...)` sejajar + kotak ringkas Gap Riset / `#memory-recall(...)`
- **Kolom Kiri — Urgensi Industri & Pendekatan Gaur (2023):**
  - **Urgensi Industri:** Transisi antarlagu yang melompat kasar di ruang emosi ($\Delta > 0,25$) menaikkan tingkat pembatalan dengar (*skip rate*) hingga **37%**.
  - **Baseline Gaur (2023):** Pembangkitan *mood-arc* 2 tahap (KNN di sekitar *waypoint* + penyaringan akustik) memakai titik rata-rata statis $(\bar{v}, \bar{a})$ per lagu.
- **Kolom Kanan — Akar Masalah DEAM (`chapter-1.tex:15-17`):**
  - **98,11% dari 1.802 klip DEAM** (anotasi 2 Hz) mengalami pergeseran emosi internal ($\Delta = 0,1937$, rentang dinamis $0,5950$).
  - **The Boundary Jump Problem:** *Outro* lagu $i$ melompat tajam saat bertemu *intro* lagu $i+1$, meskipun rata-rata statis keduanya berdekatan.
- **Penutup Slide 3 (Kalimat Gap Riset):**
  - *Gap:* Belum ada studi yang menguji apakah pemanfaatan trajektori dinamis *mood* internal lagu menghasilkan transisi *mood-arc* yang lebih koheren dibanding *static-point matching*.

---

### Slide 4: Bukti Empiris Replikasi Baseline pada Korpus DEAM
- **Komponen Typst:** `#slide-header(...)` + `#grid(columns: (1.12fr, 1fr))` berisi `#image(...)` dan `#table(...)` + `#memory-recall(...)`
- **Aset Visual Kiri:** [`Slides/assets/experiments/baseline_deam_traversal_plot.png`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Slides/assets/experiments/baseline_deam_traversal_plot.png)
- **Tabel Metrik Kanan (sumber: `metrics_comparison_deam.csv`):**

| Metrik Jarak | PCC | Evenness V-A | Step Audio |
| :--- | :---: | :---: | :---: |
| Cosine | `0,9781` | `0,000349` | `0,3506` |
| Euclidean | `0,9876` | `0,000238` | `0,3106` |
| Manhattan | `0,9762` | `0,000290` | `0,2895` |

- **Interpretasi & Catatan Teknis DEAM (`chapter-1.tex:17, 49`):**
  - PCC $> 0,97$ merupakan artefak rute diagonal buatan (Q3–Q1 hingga `0,9950`); pada rute lintas kuadran (Q1–Q2/Q4) turun ke `0,6628`–`0,7189`.
  - **Catatan Prapemrosesan DEAM (Batasan 1.4):** 15 detik awal klip diabaikan (adaptasi anotator), sehingga analisis bertumpu pada **30 detik segmen stabil (60 timestamp)**.

---

### Slide 5: Keselarasan Rumusan Masalah & Tujuan Penelitian (Subbab 1.2 & 1.3)
- **Komponen Typst:** `#slide-header(...)` + `#table(...)` atau 2 `#card-box(...)` berpasangan RM $\leftrightarrow$ TP + `#memory-recall(...)`
- **Pasangan 1 (Arsitektur):**
  - **RM 1:** Bagaimana merancang *pipeline* *mood-arc* 2 tahap berbasis KNN + penyelarasan trajektori dinamis pada korpus DEAM?
  - **TP 1:** Mengimplementasikan modul kode deterministik dan dapat direproduksi.
- **Pasangan 2 (Evaluasi Objektif):**
  - **RM 2:** Bagaimana kinerja kelancaran transisi, keseragaman, dan reduksi lompatan batas dibanding *static-point matching*?
  - **TP 2:** Menurunkan jarak lompatan batas (*Boundary Smoothness*) minimal **15%** tanpa menurunkan *Evenness Index* (540 *batch run*).
- **Pasangan 3 (Penerimaan Perseptual):**
  - **RM 3:** Bagaimana tingkat penerimaan perseptual pendengar dan korelasinya dengan metrik objektif?
  - **TP 3:** Mengukur validasi perseptual pendengar *(rencana tahap lanjut / butuh arahan pembimbing)*.

---

### Slide 6: Poin Konsultasi Pembimbing & Target Pekan Depan
- **Komponen Typst:** `#slide-header(...)` + 2 `#card-box(...)` + `#memory-recall(...)`
- **Poin Diskusi dengan Pak Hafiz:**
  1. Validasi ketajaman alur Bab I (Urgensi *skip rate* 37% $\rightarrow$ Limitasi Gaur 2023 $\rightarrow$ Gap Riset $\rightarrow$ RM 1–3 & TP 1–3).
  2. Konfirmasi kecukupan bukti replikasi DEAM (`baseline_deam_traversal_plot.png` + `metrics_comparison_deam.csv`) sebagai pijakan masalah.
  3. Arahan pembimbing terkait ruang lingkup RM 3 / TP 3 (evaluasi perseptual) sebelum masuk ke penyusunan bab lanjutan.
- **Rencana Kerja Pekan Depan:**
  1. Menyempurnakan Bab I sesuai arahan pembimbing.
  2. Menyusun tinjauan pustaka dan peta penelitian terdahulu.
  3. Merancang metodologi penyelesaian *The Boundary Jump Problem*.
