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

Folder ini menyimpan outline, staging materi dari naskah LaTeX, dan arsip catatan untuk presentasi progres mingguan kepada dosen pembimbing (**Hafiz Budi Firmansyah, S.Kom., M.Sc.**). Setiap catatan di sini terhubung ke sumber slide Typst pada direktori [`Slides/02-Progress/`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Slides/02-Progress/).

- **Acuan Utama Materi (*Single Source of Truth*):** [`proposal-penelitian-andryano-123140205/chapters/`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/proposal-penelitian-andryano-123140205/chapters/) (`chapter-1.tex` s.d. `chapter-3.tex`)
- **Referensi Sekunder:** [[06-Naskah-Draft/README]]

---

## Daftar Presentasi Progres Mingguan

| Pekan | Status Pertemuan | Topik Utama | Status Slide | Catatan Outline & Staging (Obsidian) | Berkas Typst & PDF |
| :---: | :--- | :--- | :---: | :--- | :--- |
| **#01** | Bimbingan Perdana (Siap Presentasi) | Validasi Proposal Bab I–III (*Dual Evaluation*) & Replikasi Baseline DEAM | Pembaruan (Staging Siap) | [[01-Minggu-01-Baseline-DEAM]] · [[03-Staging-Materi-Naskah-ke-Slides]] | [`progres_m01.typ`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Slides/02-Progress/01-Minggu-01-Baseline-DEAM/progres_m01.typ) / [PDF](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Slides/02-Progress/01-Minggu-01-Baseline-DEAM/progres_m01.pdf) |

---

## Alur Kerja Pembuatan & Pembaruan Slide Progres

1. **Ekstrak materi dari SSOT LaTeX:** Ambil angka, rumus, tabel, dan temuan terbaru dari [`proposal-penelitian-andryano-123140205/chapters/`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/proposal-penelitian-andryano-123140205/chapters/) lalu catat dalam format ringkas di `10-Slides/Progress/` (contoh: [[03-Staging-Materi-Naskah-ke-Slides]]).
2. **Eksekusi todolist coding Typst:** Ikuti daftar tugas teknis pada [[09-todolist/14-Task-Generate-Slides-Typst-dari-Naskah]].
3. **Sinkronkan aset eksperimen (jika ada grafik baru):**
   ```powershell
   powershell -File "Slides\scripts\sync_experiment_assets.ps1"
   ```
4. **Kompilasi dengan Live-Watch:**
   ```powershell
   cd "Slides"
   .\run_watch.ps1 -Target 01
   ```
5. **Catat arahan pembimbing:** Setelah sesi bimbingan selesai, salin keputusan dosen ke [[03-Bimbingan/01-Notulensi-Bimbingan]].

---

## Tautan Terkait

- **Indeks Utama Slides:** [[00-Index-Slides-Engine]]
- **Todolist Coding Typst:** [[09-todolist/14-Task-Generate-Slides-Typst-dari-Naskah]]
- **Template Catatan Progres:** [`Template-Slide-Bimbingan-Mingguan.md`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Catatan-Memori/Catatan-Memori-Logs/99-Templates/Template-Slide-Bimbingan-Mingguan.md)
- **Template Typst Mingguan:** [`template_mingguan.typ`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Slides/02-Progress/00-Template-Mingguan/template_mingguan.typ)
- **Notulensi Bimbingan:** [[03-Bimbingan/01-Notulensi-Bimbingan]]
