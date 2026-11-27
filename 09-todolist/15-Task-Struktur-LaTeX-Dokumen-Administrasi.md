---
title: "Task 15: Struktur LaTeX & Metadata untuk Dokumen Administrasi TA"
tags:
  - todolist
  - latex
  - administrasi
  - sempro
  - metadata
  - iterasi-ta1
status: "TODO"
source_templates: "dokumen-template-if/"
ssot_metadata: "proposal-penelitian-andryano-123140205/config/informations.tex"
---

# Task 15: Struktur Folder LaTeX & Metadata Dokumen Administrasi TA

> **Tujuan:** Membangun sistem *Single Source of Truth* (SSOT) berbasis LaTeX untuk seluruh berkas administrasi Tugas Akhir IF ITERA (mengacu pada [`dokumen-template-if/`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/dokumen-template-if)) sehingga data mahasiswa, judul, dosen pembimbing, penguji, dan tanggal cukup diisi **satu kali** di `metadata.tex` lalu dikompilasi menjadi PDF siap cetak/tanda tangan.

---

## Bagian I: Rancangan Struktur Folder & Metadata

```text
📁 administrasi-ta/
├── 📄 metadata.tex                  # SSOT: Nama, NIM, Judul (ID/EN), Dosbing, Penguji, Kaprodi, Dosen Wali, Tanggal
├── 📄 build.ps1                     # Skrip compile batch (xelatex / latexmk) semua formulir ke folder out/
├── 📂 style/
│   ├── 📄 itera_admin.sty           # Layout A4, margin resmi surat, kop ITERA/FTI/IF, blok TTD & tabel
│   └── 📂 assets/
│       └── 🖼️ itera_logo.png        # Salinan logo resmi ITERA untuk kop surat
├── 📂 forms/
│   ├── 📂 01-sempro/                # Prioritas utama pendaftaran & pelaksanaan Sempro
│   │   ├── 📄 form_persetujuan_sempro.tex
│   │   ├── 📄 kartu_kendali_bimbingan.tex
│   │   ├── 📄 daftar_hadir_sempro.tex
│   │   ├── 📄 persetujuan_dosen_wali.tex
│   │   ├── 📄 pernyataan_orisinalitas.tex
│   │   └── 📄 pernyataan_penggunaan_ai.tex
│   └── 📂 02-sidang-akhir/          # Prioritas tahap TA 2 / Sidang Akhir
│       ├── 📄 daftar_perbaikan.tex
│       ├── 📄 surat_cek_turnitin.tex
│       ├── 📄 pernyataan_sidang_yudisium.tex
│       └── 📄 surat_penyelesaian_ta.tex
└── 📂 out/                          # Output PDF hasil kompilasi (di-ignore git jika perlu)
```

---

## Bagian II: Todolist Eksekusi Bertahap

### Tahap 1: Setup Struktur & Metadata SSOT
- [ ] **1.1 Buat kerangka folder `administrasi-ta/`** beserta subfolder `style/`, `style/assets/`, `forms/01-sempro/`, `forms/02-sidang-akhir/`, dan `out/`.
- [ ] **1.2 Salin aset kop surat:** Salin `itera_logo.png` dari `proposal-penelitian-andryano-123140205/` ke `administrasi-ta/style/assets/`.
- [ ] **1.3 Buat `metadata.tex` (SSOT):**
  - Sinkronkan makro identitas dengan [`config/informations.tex`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/proposal-penelitian-andryano-123140205/config/informations.tex) (`\thetitle`, `\theauthor`, `\theauthornim`, `\namadosbinga`, `\nipdosbinga`, `\namakaprodi`, dll.).
  - Tambahkan field khusus administrasi yang belum ada di naskah TA: `\namadosenwali`, `\nipdosenwali`, `\semesteraktif`, `\totalsks`, `\ipk`, `\emailmahasiswa`, `\nohp`, `\tanggalpengajuan`.
  - Opsional: buat skrip kecil atau aturan sinkronisasi agar perubahan judul/NIP di `informations.tex` otomatis terpantau.
- [ ] **1.4 Buat `style/itera_admin.sty`:**
  - Atur kertas **A4** (`21 cm x 29.7 cm`), font Times New Roman / TeX Gyre Termes 11–12 pt (via `fontspec` untuk XeLaTeX).
  - Buat makro reusable: `\kopiterafakultas`, `\blokidentitasmahasiswa`, `\blokttddua{...}{...}`, `\blokttdsatu{...}`, dan `\kotakmaterai`.

### Tahap 2: Replikasi Form Prioritas Sempro (`forms/01-sempro/`)
Mengacu pada berkas resmi di `dokumen-template-if/` dan checklist [`03-Tracker-Prasyarat-Sempro`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Catatan-Memori/Catatan-Memori-Logs/03-Bimbingan/03-Tracker-Prasyarat-Sempro.md):
- [ ] **2.1 `form_persetujuan_sempro.tex`** $\leftarrow$ `FORM PERSETUJUAN SIDANG PROPOSAL DAN AKHIR.docx` (dengan opsi mode `[sempro]` / `[akhir]`).
- [ ] **2.2 `kartu_kendali_bimbingan.tex`** $\leftarrow$ `KARTU KENDALI BIMBINGAN TUGAS AKHIR.docx` (tabel log pertemuan bimbingan, tanggal, materi/arahan, dan kolom paraf dosen).
- [ ] **2.3 `daftar_hadir_sempro.tex`** $\leftarrow$ `DAFTAR HADIR SEMINAR PROPOSAL.docx` (log menghadiri minimal 2× Sempro mahasiswa lain).
- [ ] **2.4 `persetujuan_dosen_wali.tex`** $\leftarrow$ `SURAT PERNYATAAN PERSETUJUAN DOSEN WALI.docx`.
- [ ] **2.5 `pernyataan_penggunaan_ai.tex` & `pernyataan_orisinalitas.tex`** $\leftarrow$ `draft-deklarasi-ai.docx` & `lampiran-1-pernyataan-orisinalitas.docx` (pastikan selaras dengan Lampiran 1 & 2 Pedoman TA IF ITERA 1.2.0).

### Tahap 3: Replikasi Form Sidang Akhir & Pasca-Sidang (`forms/02-sidang-akhir/`)
- [ ] **3.1 `daftar_perbaikan.tex`** $\leftarrow$ `Daftar Perbaikan.docx`.
- [ ] **3.2 `surat_cek_turnitin.tex`** $\leftarrow$ `Surat Keterangan Cek Turnitin TA Mahasiwa.docx`.
- [ ] **3.3 `pernyataan_sidang_yudisium.tex`** $\leftarrow$ `SURAT PERNYATAAN MENGIKUTI SIDANG AKHIR DAN YUDISIUM.docx`.
- [ ] **3.4 `surat_penyelesaian_ta.tex`** $\leftarrow$ `Surat Penyelesaian TA.docx`.

### Tahap 4: Otomasi Build & Verifikasi Layout
- [ ] **4.1 Buat `build.ps1`:** Kompilasi seluruh `.tex` di `forms/` menggunakan `xelatex -output-directory=out` (0 error, bersih dari file aux sementara).
- [ ] **4.2 Audit visual 1:1:** Bandingkan hasil PDF di `out/` secara berdampingan dengan `.docx` asli di `dokumen-template-if/` untuk memastikan teks, tabel, dan posisi tanda tangan sesuai standar prodi.
- [ ] **4.3 Uji isi metadata:** Pastikan seluruh placeholder `[...]` pada `metadata.tex` sudah terisi sebelum mencetak berkas pendaftaran Sempro.
