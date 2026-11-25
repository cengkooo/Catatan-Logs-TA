---
title: "Task 14: Coding Typst Slides dari Fundamental TA & Naskah LaTeX"
tags:
  - todolist
  - typst
  - slides
  - metadata-toml
  - progress
  - sempro
status: "READY FOR EXECUTION"
ssot_source: "proposal-penelitian-andryano-123140205/chapters/"
phase_0_ref: "09-todolist/00-Phase-00-Fundamental-TA-dan-Penguatan-Naskah.md"
---

# Task 14: Generate & Sinkronisasi Slide Typst dari Fundamental TA

> **Prasyarat:** Pastikan poin-poin pada [[09-todolist/00-Phase-00-Fundamental-TA-dan-Penguatan-Naskah]] sudah dikunci sehingga seluruh angka, batasan, baseline, dan metode uji antara naskah LaTeX dan slide Typst **100% konsisten**.

---

## Bagian I: Ringkasan Fondasi yang Wajib Terlihat di Slide (Anti-Goyah)

1. **Identitas & Judul:** Terpusat di [`Slides/metadata.toml`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Slides/metadata.toml) (selaras dengan `proposal-penelitian-andryano-123140205/config/informations.tex`).
2. **Urgency & Research Gap:** Pengalaman dengar sekuensial vs *static-point* Gaur & Donnelly (2023); *skip rate* naik 37% ($\Delta > 0,25$); 98,11% klip DEAM bergeser internal ($\Delta = 0,1937$).
3. **Keselarasan 1:1 (RM $\leftrightarrow$ TP):** 3 Rumusan Masalah dan 3 Tujuan Penelitian terukur (arsitektur 2-tahap, reduksi $\mathcal{S} \ge 15\%$ via Wilcoxon $p < 0,05$, serta *Blind A/B Listening Test* $N \ge 30$).
4. **Tameng Scope & Validitas:** 2D $V-A$ Russell, DEAM 30s segmen stabil (60 *timestamp*), *Blind A/B* klip sambungan 30s, KNN deterministik, $M \in \{5, 10, 15\}$, non-*real-time*.
5. **Evaluasi & Uji Ablasi:** Replikasi Gaur + Naive Random + **Ablation (*Trajectory Filter ON vs OFF*)** berlandaskan `meyes2019ablation` dan `bendada2023scalable`.

---

## Bagian II: Todolist Coding Typst (Arsitektur Terbaru `Slides/`)

### Tahap 1: Metadata & Sinkronisasi Aset
- [ ] **1.1 Isi `Slides/metadata.toml` dengan data resmi:** Pastikan `student.name`, `student.nim`, `research.title`, `research.specialization`, `research.stage`, dan `supervision.advisor` sesuai dengan `config/informations.tex` (bukan placeholder `[...]`) saat hendak dipakai presentasi resmi.
- [ ] **1.2 Sinkronkan aset eksperimen:**
  ```powershell
  powershell -File "Slides\scripts\sync_experiment_assets.ps1"
  ```
- [ ] **1.3 Verifikasi arsitektur tema:** Pastikan seluruh berkas `.typ` memakai *relative path* (`../../templates/itera_theme.typ` untuk `02-Progress/` dan `../templates/itera_theme.typ` untuk `01-Sempro/`) serta **tidak** memakai `#memory-recall(...)`.

### Tahap 2: Pembuatan / Pemutakhiran Slide Progres Bimbingan (`Slides/02-Progress/`)
- [ ] **2.1 Gunakan template mingguan terbaru:** Salin [`Slides/02-Progress/00-Template-Mingguan/template_mingguan.typ`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Slides/02-Progress/00-Template-Mingguan/template_mingguan.typ) (atau perbarui `01-Minggu-01-Baseline-DEAM/progres_m01.typ`).
- [ ] **2.2 Slide 1 (`#cover-slide`):** Cukup isi `title` dan `subtitle: "Laporan Progress Bimbingan Tugas Akhir — Pertemuan #[x] — [Tanggal]"`, serta pertahankan `specialization: none, stage: none, meeting-date: none` agar hanya `Judul`, `Nama dan NIM`, dan `Pembimbing` yang tampil dari `metadata.toml`.
- [ ] **2.3 Slide 2 (Matriks Progres):** Isi 3 `#card-box` (`DONE`, `IN_PROGRESS`, `BLOCKED`) yang mencerminkan capaian riil Fase 0, replikasi baseline DEAM, dan poin keputusan pembimbing.
- [ ] **2.4 Slide 3 (Bukti Empiris DEAM):** Tampilkan `#image("../../assets/experiments/baseline_deam_traversal_plot.png")` dan ringkasan `metrics_comparison_deam.csv` + temuan artefak rute diagonal vs lintas kuadran.
- [ ] **2.5 Slide 4 (Konsultasi & Action Items):** Cantumkan poin diskusi validasi *Blind A/B*, *Ablation Study* (`meyes2019ablation`, `bendada2023scalable`), dan target pekan depan.

### Tahap 3: Promosi Materi ke Slide Seminar Proposal (`Slides/01-Sempro/sempro_slides.typ`)
- [ ] **3.1 Sinkronkan 15 Slide Sempro:** Setelah materi disetujui pembimbing, petakan 16 pilar dari Fase 0 ke [`Slides/01-Sempro/sempro_slides.typ`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Slides/01-Sempro/sempro_slides.typ) (fokus presentasi Sempro: Slide 1, 4, 5, 6, 7, 8, dan 15 untuk durasi tepat 10 menit).
- [ ] **3.2 Pastikan konsistensi angka:** Cek ulang bahwa seluruh angka di `sempro_slides.typ` (98,11% DEAM, 540 *batch run*, $\mathcal{S} \ge 15\%$, $N \ge 30$) sama persis dengan `chapters/chapter-1.tex` s.d. `chapter-3.tex`.

### Tahap 4: Kompilasi Otomatis (`Ctrl + S`) & Audit Visual PDF
- [ ] **4.1 Uji Auto-Build VS Code:** Buka file `.typ` dan tekan `Ctrl + S` — pastikan Tinymist (`.vscode/settings.json`) langsung memperbarui PDF di folder yang sama.
- [ ] **4.2 Kompilasi cadangan via CLI:**
  ```powershell
  & "D:\Typst\typst-x86_64-pc-windows-msvc\typst.exe" compile --root "Slides" "Slides\02-Progress\00-Template-Mingguan\template_mingguan.typ" "Slides\02-Progress\00-Template-Mingguan\template_mingguan.pdf"
  ```
- [ ] **4.3 Audit Visual:** Pastikan tidak ada halaman yang mengalami *overflow* (Slide 1 tetap 1 halaman penuh, setiap `#card-box` muat tanpa terpotong).
