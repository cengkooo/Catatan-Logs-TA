---
title: "Todolist Coding Typst: Slide Progres Bimbingan #01 (6 Slide — Baseline, Bab 1, & Gaur 2023)"
tags:
  - todolist
  - typst
  - slides
  - progress
  - baseline
  - bab-1
  - gaur-2023
  - coding
status: "COMPLETED"
target_output: "Slides/02-Progress/01-Minggu-01-Baseline-DEAM/progres_m01.pdf (6 Slide)"
ssot_source: "proposal-penelitian-andryano-123140205/chapters/chapter-1.tex"
staging_note: "10-Slides/Progress/03-Staging-Materi-Naskah-ke-Slides.md"
---

# Todolist Coding Typst: Generate Slide Progres Bimbingan #01 (6 Slide)

> **Tujuan:** Mengimplementasikan kode Typst pada [`Slides/02-Progress/01-Minggu-01-Baseline-DEAM/progres_m01.typ`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Slides/02-Progress/01-Minggu-01-Baseline-DEAM/progres_m01.typ) menjadi **6 slide** siap presentasi untuk bimbingan perdana ke Pak Hafiz Budi Firmansyah, S.Kom., M.Sc.
>
> **Batasan Ruang Lingkup (Hard Constraint):**
> - **Hanya** memasukkan materi: (1) Hasil Replikasi Baseline DEAM, (2) Bab 1 (`chapter-1.tex`: Latar Belakang 1.1, RM & TP 1.2–1.3, dan catatan teknis DEAM 30s dari 1.4), serta (3) Kutipan fundamental **Gaur (2023)** (`gaur2023mooddynamic`).
> - **Dilarang** memasukkan konten Bab 2 (Tinjauan Pustaka) maupun Bab 3 (Metodologi / protokol lanjutan).

---

## Tahap 1: Audit Pra-Coding & Sinkronisasi Aset

- [x] **1.1 Sinkronkan aset eksperimen:** Jalankan skrip berikut dari root repositori agar plot dan CSV terbaru tersedia di `Slides/assets/experiments/`:
  ```powershell
  powershell -File "Slides\scripts\sync_experiment_assets.ps1"
  ```
- [x] **1.2 Verifikasi berkas sumber data & visual:** Pastikan kedua berkas ini ada dan terbaca:
  - `Slides/assets/experiments/baseline_deam_traversal_plot.png`
  - `Slides/assets/experiments/metrics_comparison_deam.csv`
- [x] **1.3 Verifikasi fungsi tema Typst:** Buka [`Slides/templates/itera_theme.typ`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Slides/templates/itera_theme.typ) dan pastikan pemakaian komponen berikut konsisten:
  - `#itera-presentation.with(...)`
  - `#cover-slide(...)`
  - `#slide-header(tag: ..., title: ..., subtitle: ...)`
  - `#card-box(title: ..., fill: ..., stroke: ..., height: ..., body: [...])`
  - `#status-badge("DONE" | "IN_PROGRESS" | "BLOCKED")`
  - `#memory-recall(obsidian: ..., code: ..., artifact: ...)`
- [x] **1.4 Audit batasan konten:** Pastikan seluruh poin diambil dari [[10-Slides/Progress/03-Staging-Materi-Naskah-ke-Slides]] dan tidak ada materi Bab 2 maupun Bab 3 yang masuk.

---

## Tahap 2: Coding Slide per Slide di `progres_m01.typ` (6 Slide)

### Slide 1 — Cover & Identitas Pertemuan
- [x] **2.1 Perbarui `#show: itera-presentation.with(...)` dan `#cover-slide(...)`:**
  ```typst
  #show: itera-presentation.with(
    title: "Laporan Progres Mingguan #01",
    subtitle: "Replikasi Baseline Gaur (2023) & Pemetaan Bab I",
    stage: "Bimbingan Mingguan #01",
    course-code: "Tugas Akhir (IF25-40033)",
  )

  #cover-slide(
    title: [Replikasi Baseline Gaur (2023) & Pemetaan Masalah Bab I pada Korpus DEAM],
    subtitle: "Laporan Progres Bimbingan Tugas Akhir — Pertemuan #01",
    author: "Andryano Kadarisman",
    nim: "123140205",
    advisor: "Hafiz Budi Firmansyah, S.Kom., M.Sc.",
    specialization: "Sistem Cerdas dan Sains Data Terapan",
    stage: "Bimbingan Mingguan #01",
    institution: "Program Studi Teknik Informatika, Institut Teknologi Sumatera",
    year: "2026",
    created-date: "25 November 2026",
    meeting-date: "Jadwal Bimbingan #01",
  )
  ```

### Slide 2 — Matriks Progres Pekan Ini
- [x] **2.2 Susun `#grid(columns: (1fr, 1fr, 1fr), gutter: 0.22in)` dengan 3 `#card-box` (`height: 3.00in`, `#set text(size: 13pt)`):**
  - **Kartu `DONE` (`fill: rgb("f0fdf4")`, `stroke: 0.5pt + clr-success`):**
    - Replikasi baseline Gaur (2023) pada 1.802 klip DEAM dan 540 *batch run*.
    - Penyusunan Bab I (`chapter-1.tex`: Latar Belakang, RM, TP, Batasan, Manfaat).
    - Kajian pustaka acuan utama Gaur (2023).
  - **Kartu `IN_PROGRESS` (`fill: rgb("fffbeb")`, `stroke: 0.5pt + clr-warning`):**
    - Penyiapan slide pemaparan Bimbingan #01.
    - Persiapan penyusunan bab lanjutan setelah arahan pembimbing.
  - **Kartu `BLOCKED` (`fill: rgb("fef2f2")`, `stroke: 0.5pt + clr-danger`):**
    - Menunggu validasi pembimbing atas keselarasan Bab I dan temuan *The Boundary Jump Problem*.
- [x] **2.3 Tambahkan `#memory-recall` di bagian bawah Slide 2.**

### Slide 3 — Latar Belakang, Limitasi Gaur (2023), & Gap Riset
- [x] **2.4 Buat `#slide-header`:**
  - `tag`: `"Bimbingan Mingguan #01 | Bab I & Gaur (2023)"`
  - `title`: `"Latar Belakang, Limitasi Gaur (2023), & Gap Riset"`
  - `subtitle`: `"Urgensi skip rate 37%, asumsi titik statis, dan The Boundary Jump Problem"`
- [x] **2.5 Isi `#grid(columns: (1fr, 1fr), gutter: 0.22in)` dengan 2 `#card-box` (`height: 2.35in`, `#set text(size: 12pt)`), lalu tambahkan banner Gap Riset di bawahnya (`height: 0.60in`):**
  - **Kolom Kiri (`fill: clr-soft1`, judul `"Urgensi & Baseline Gaur (2023)"`):**
    ```typst
    • *Urgensi Industri:* Lompatan emosi ($Delta > 0,25$) menaikkan *skip rate* pendengar hingga *37%*.
    #v(0.04in)
    • *Alur Gaur (2023):* Penelusuran KNN di sekitar waypoint + penyaringan fitur akustik.
    #v(0.04in)
    • *Asumsi Statis:* Tiap lagu diringkas menjadi satu titik rata-rata $(overline(v), overline(a))$.
    ```
  - **Kolom Kanan (`fill: rgb("fef2f2")`, `stroke: 0.5pt + clr-danger`, judul `"Fakta DEAM & Akar Masalah (Bab I)"`):**
    ```typst
    • *Dinamika Internal:* *98,11%* dari 1.802 klip DEAM (2 Hz) bergeser secara internal.
    #v(0.04in)
    • *Besar Pergeseran:* Rata-rata awal-akhir $Delta = 0,1937$, rentang dinamis hingga $0,5950$.
    #v(0.04in)
    • *Boundary Jump Problem:* Outro lagu $i$ melompat tajam ke intro lagu $i+1$ meski rata-ratanya dekat.
    ```
  - **Banner Gap Riset (di bawah grid, sebelum `#memory-recall`):**
    ```typst
    #v(0.08in)
    #card-box(
      title: none,
      fill: clr-soft2,
      body: [
        #set text(size: 11.5pt)
        *Gap Riset:* Belum ada studi yang menguji apakah pemanfaatan trajektori dinamis mood internal lagu menghasilkan transisi *mood-arc* yang lebih koheren dibandingkan *static-point matching*.
      ]
    )
    ```

### Slide 4 — Bukti Empiris Replikasi Baseline pada DEAM
- [x] **2.6 Buat `#slide-header` untuk bukti empiris replikasi:**
  - `tag`: `"Bimbingan Mingguan #01 | Bukti Empiris"`
  - `title`: `"Hasil Replikasi Baseline Gaur (2023) pada DEAM"`
  - `subtitle`: `"Visualisasi traversal kuadran, 3 metrik jarak, dan catatan segmen stabil 30s"`
- [x] **2.7 Susun `#grid(columns: (1.12fr, 1fr), gutter: 0.22in)`:**
  - **Kolom Kiri:** `#image("/assets/experiments/baseline_deam_traversal_plot.png", height: 2.85in)`
  - **Kolom Kanan (`height: 2.85in`, `#set text(size: 11pt)`):**
    ```typst
    #card-box(
      title: "Metrik Replikasi & Catatan DEAM",
      fill: clr-soft1,
      height: 2.85in,
      body: [
        #set text(size: 11pt)
        #table(
          columns: (1.1fr, 0.85fr, 1fr, 1fr),
          inset: 4.5pt,
          stroke: 0.4pt + gray,
          [*Jarak*], [*PCC*], [*Even. V-A*], [*Step Audio*],
          [Cosine], [0,9781], [0,000349], [0,3506],
          [Euclidean], [0,9876], [0,000238], [0,3106],
          [Manhattan], [0,9762], [0,000290], [0,2895],
        )
        #v(0.05in)
        • *Artefak Rute:* PCC $> 0,97$ muncul di rute diagonal Q3–Q1 ($0,9950$); rute lintas kuadran (Q1–Q2/Q4) turun ke *$0,6628$–$0,7189$*.
        #v(0.04in)
        • *Segmen Stabil DEAM (1.4):* 15s awal klip diabaikan (adaptasi anotator), analisis memakai *30s segmen stabil (60 timestamp)*.
      ]
    )
    ```
- [x] **2.8 Tambahkan `#memory-recall` merujuk `metrics_comparison_deam.csv`, `baseline_deam_traversal_plot.png`, dan `chapter-1.tex:17,49`.**

### Slide 5 — Keselarasan Rumusan Masalah & Tujuan Penelitian (Subbab 1.2 & 1.3)
- [x] **2.9 Buat `#slide-header` untuk RM & TP:**
  - `tag`: `"Bimbingan Mingguan #01 | Rumusan & Tujuan"`
  - `title`: `"Keselarasan Rumusan Masalah & Tujuan Penelitian"`
  - `subtitle`: `"Pemetaan 1:1 antara Subbab 1.2 dan Subbab 1.3 pada Bab I"`
- [x] **2.10 Susun tabel berpasangan RM $\leftrightarrow$ TP di dalam `#card-box` (`height: 2.95in`, `#set text(size: 11.5pt)`):**
  ```typst
  #card-box(
    title: "Matriks 1:1 Rumusan Masalah & Tujuan (Bab I)",
    fill: clr-soft1,
    height: 2.95in,
    body: [
      #set text(size: 11.5pt)
      #table(
        columns: (0.45fr, 1.3fr, 1.3fr),
        inset: 6pt,
        stroke: 0.4pt + gray,
        [*Butir*], [*Rumusan Masalah (1.2)*], [*Tujuan & Indikator (1.3)*],
        [*#1*], [Merancang pipeline *mood-arc* 2 tahap (KNN + penyelarasan trajektori dinamis) pada DEAM.], [Mengimplementasikan modul kode deterministik & dapat direproduksi.],
        [*#2*], [Kinerja kelancaran transisi, keseragaman, dan reduksi lompatan batas vs *static-point*.], [Menurunkan *Boundary Smoothness* minimal *15%* tanpa menurunkan *Evenness* (540 batch run).],
        [*#3*], [Tingkat penerimaan perseptual pendengar & korelasinya dengan metrik objektif.], [Validasi perseptual pendengar *(rencana tahap lanjut — butuh arahan pembimbing)*.],
      )
    ]
  )
  ```
- [x] **2.11 Tambahkan `#memory-recall` merujuk `chapter-1.tex:23-41`.**

### Slide 6 — Poin Konsultasi Pembimbing & Target Pekan Depan
- [x] **2.12 Buat `#slide-header` untuk penutup & diskusi:**
  - `tag`: `"Bimbingan Mingguan #01 | Diskusi & Rencana"`
  - `title`: `"Poin Konsultasi & Rencana Kerja Pekan Depan"`
  - `subtitle`: `"Validasi arah Bab I dan hasil replikasi baseline sebelum menyusun bab lanjutan"`
- [x] **2.13 Susun `#grid(columns: (1.05fr, 1fr), gutter: 0.24in)` dengan 2 `#card-box` (`height: 2.95in`, `#set text(size: 12.5pt)`):**
  - **Kolom Kiri (`fill: rgb("fffbeb")`, `stroke: 0.5pt + clr-warning`, judul `"Poin Diskusi dengan Pak Hafiz"`):**
    1. Validasi alur Bab I (*skip rate* 37% $\rightarrow$ limitasi Gaur 2023 $\rightarrow$ gap $\rightarrow$ RM 1–3 & TP 1–3).
    2. Konfirmasi kecukupan bukti replikasi DEAM (plot + tabel 3 metrik jarak).
    3. Arahan pembimbing mengenai ruang lingkup RM 3 / TP 3 (evaluasi perseptual).
  - **Kolom Kanan (`fill: clr-soft2`, judul `"Rencana Kerja Pekan Depan"`):**
    1. Menyempurnakan Bab I sesuai catatan bimbingan.
    2. Menyusun tinjauan pustaka dan peta penelitian terdahulu.
    3. Merancang metodologi penyelesaian *The Boundary Jump Problem*.

---

## Tahap 3: Aturan Tata Letak & Anti-Overflow

- [x] **3.1 Kendali tinggi kartu:** Pada Slide 3 (yang memiliki banner Gap Riset di bawah grid), jaga tinggi dua kartu atas sekitar `2.25in`–`2.35in` agar banner + `#memory-recall` tidak meluber ke halaman baru.
- [x] **3.2 Kepadatan teks:** Pertahankan ukuran huruf `11pt`–`13pt` dan maksimal 3 butir per kartu.
- [x] **3.3 Penanda halaman:** Pastikan hanya ada tepat **5 pemisah `#pagebreak()`** untuk menghasilkan total **6 halaman**.
- [x] **3.4 Audit batasan Bab 2 & Bab 3:** Periksa kembali `progres_m01.typ` agar tidak ada materi Bab 2 maupun Bab 3 yang terbawa.

---

## Tahap 4: Kompilasi & Verifikasi PDF

- [x] **4.1 Kompilasi berkas Typst:**
  ```powershell
  & "D:\Typst\typst-x86_64-pc-windows-msvc\typst.exe" compile --root "Slides" "Slides\02-Progress\01-Minggu-01-Baseline-DEAM\progres_m01.typ" "Slides\02-Progress\01-Minggu-01-Baseline-DEAM\progres_m01.pdf"
  ```
- [x] **4.2 Mode Live-Watch (opsional saat penyuntingan interaktif):**
  ```powershell
  cd "Slides"
  .\run_watch.ps1 -Target 01
  ```
- [x] **4.3 Verifikasi akhir PDF:** Buka [`progres_m01.pdf`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Slides/02-Progress/01-Minggu-01-Baseline-DEAM/progres_m01.pdf) dan pastikan:
  - Total halaman tepat **6 halaman**.
  - Gambar `baseline_deam_traversal_plot.png` tampil tajam dan tidak terpotong.
  - Tabel metrik Slide 4 cocok dengan `metrics_comparison_deam.csv`, dan matriks RM $\leftrightarrow$ TP Slide 5 cocok dengan `chapter-1.tex`.
