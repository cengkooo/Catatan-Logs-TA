---
title: "Indeks Presentasi Progres Mingguan Bimbingan TA"
tags:
  - slides
  - progress
  - bimbingan
  - typst
  - mingguan
---

# Indeks Presentasi Progres Mingguan ke Dosen Pembimbing

Folder ini menyimpan outline, materi diskusi, dan arsip catatan untuk presentasi progres mingguan kepada dosen pembimbing (**Hafiz Budi Firmansyah, S.Kom., M.Sc.**). Setiap catatan di sini terhubung langsung ke sumber slide Typst pada direktori [`Slides/02-Progress/`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Slides/02-Progress/).

---

## Daftar Presentasi Progres Mingguan

| Pekan | Tanggal Pertemuan | Topik Utama | Status Slide | Catatan Outline (Obsidian) | Berkas Typst & PDF |
| :---: | :--- | :--- | :---: | :--- | :--- |
| **#01** | 21 November 2026 | Validasi Replikasi Baseline Gaur (2020) & Eksplorasi DEAM | Selesai | [[01-Minggu-01-Baseline-DEAM]] | [`progres_m01.typ`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Slides/02-Progress/01-Minggu-01-Baseline-DEAM/progres_m01.typ) / [PDF](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Slides/02-Progress/01-Minggu-01-Baseline-DEAM/progres_m01.pdf) |
| **#02** | 27 November 2026 (Tentatif) | Penguatan Fundamental Literatur, Revalidasi Russell 1980, & Penentuan Skenario Evaluasi | Draf Outline | [[02-Minggu-02-Penguatan-Fundamental-dan-Skenario]] | Belum dikompilasi (target: `Slides/02-Progress/02-Minggu-02-...`) |

---

## Alur Pembuatan Slide Progres Pekan Baru

1. **Susun outline di Obsidian:** Buat catatan baru di folder `10-Slides/Progress/` memakai format dari [[99-Templates/Template-Slide-Bimbingan-Mingguan]].
2. **Duplikasi template Typst:** Salin folder [`Slides/02-Progress/00-Template-Mingguan/`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Slides/02-Progress/00-Template-Mingguan/) menjadi folder pekan baru, misalnya `02-Minggu-02-Nama-Topik/`.
3. **Sinkronkan aset eksperimen (jika ada grafik baru):**
   ```powershell
   powershell -File "Slides\scripts\sync_experiment_assets.ps1"
   ```
4. **Kompilasi dengan Live-Watch:**
   ```powershell
   cd "Slides"
   .\run_watch.ps1 -Target 02
   ```
   Atau langsung dari folder `Slides\02-Progress`:
   ```powershell
   .\run_watch.ps1 -Minggu 02
   ```
5. **Catat arahan pembimbing:** Setelah sesi bimbingan selesai, salin keputusan dosen ke [[03-Bimbingan/01-Notulensi-Bimbingan]].

---

## Tautan Terkait

- **Indeks Utama Slides:** [[00-Index-Slides-Engine]]
- **Template Catatan Progres:** [`Template-Slide-Bimbingan-Mingguan.md`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Catatan-Memori/Catatan-Memori-Logs/99-Templates/Template-Slide-Bimbingan-Mingguan.md)
- **Template Typst Mingguan:** [`template_mingguan.typ`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Slides/02-Progress/00-Template-Mingguan/template_mingguan.typ)
- **Notulensi Bimbingan:** [[03-Bimbingan/01-Notulensi-Bimbingan]]
