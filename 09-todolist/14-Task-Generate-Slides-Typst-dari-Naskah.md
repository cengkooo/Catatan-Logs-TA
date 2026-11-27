---
title: "Task 14: Coding Typst Slides dari Fundamental TA & Naskah LaTeX"
tags:
  - todolist
  - typst
  - slides
  - metadata-toml
  - progress
  - sempro
  - fundamental-ta
status: "IN PROGRESS (Slide M01 Selesai, Menunggu Audit Visual & Promosi Sempro)"
ssot_source: "proposal-penelitian-andryano-123140205/chapters/"
phase_0_ref: "09-todolist/00-Phase-00-Fundamental-TA-dan-Penguatan-Naskah.md"
---

# Task 14: Generate & Sinkronisasi Slide Typst dari Fundamental TA

> **Prasyarat:** Pastikan poin-poin pada [[09-todolist/00-Phase-00-Fundamental-TA-dan-Penguatan-Naskah]] sudah dikunci sehingga seluruh angka, batasan, baseline, dan metode uji antara naskah LaTeX dan slide Typst **100% konsisten**.

---

## Bagian I: Fondasi Fundamental TA yang Wajib Dijelaskan ke Dosen (16 Pilar $\to$ 5 Slide Dasar)

Sebelum menunjukkan progres coding atau grafik eksperimen, susun **5 Slide Fundamental (F0–F4)** tepat setelah `#cover-slide` agar dosen pembimbing langsung memahami judul dan logika riset Anda dari paling dasar (*judul $\to$ problem/urgency $\to$ gap $\to$ method $\to$ proof*):

### Slide F0 — Bedah Kata per Kata Judul TA (Slide 2, Tepat Setelah Cover)
Judul: *"Mood-Arc Playlist Generation Berbasis Dynamic Mood Trajectory Menggunakan K-Nearest Neighbors dan Trajectory Alignment"*
- **`Mood-Arc Playlist Generation`:** Pembuatan daftar putar musik yang alur emosinya bergerak bertahap dari mood awal ke mood tujuan (mis. *Sad* Q3 $\to$ *Happy* Q1), bukan satu mood statis.
- **`Berbasis Dynamic Mood Trajectory`:** Memanfaatkan jejak perubahan emosi **2 Hz (per 0,5 detik)** di dalam lagu (dari *intro* ke *outro*), bukan mereduksi satu lagu menjadi satu titik rata-rata.
- **`Menggunakan K-Nearest Neighbors (KNN)`:** Tahap 1 — mencari $K=20$ lagu kandidat terdekat di sekitar titik acuan (*waypoint*) pada bidang 2D *Valence-Arousal*.
- **`dan Trajectory Alignment`:** Tahap 2 — menyelaraskan arah gerak emosi internal lagu dengan arah lintasan playlist sekaligus meminimalkan lompatan sambungan *outro-intro* ($\mathcal{BJC}$).

### Slide F0.5 — Contoh Penerapan Algoritma di Platform Musik Mainstream (Konteks Industri & Q&A)
Untuk memperkuat urgensi di depan dosen pembimbing sebelum masuk ke masalah teknis:
- **Spotify (`tomasi2023automatic`, `schweiger2025impact`):** Menggunakan *Simulation-based Reinforcement Learning* untuk urutan trek sekuensial (*Autoplay/Daily Mix*) dan fitur audio (*Valence/Energy*). *Batasan:* *black-box*, biaya latih tinggi, dan lompatan emosi kasar ($\Delta > 0{,}25$) tetap memicu *skip rate* **37%**.
- **Deezer (`bontempelli2022flowmoods`, `bendada2023scalable`):** Menerapkan *Flow Moods* (radio kuadran afektif) dan arsitektur 2-tahap (*Candidate Generation + Reranking*). *Batasan:* *Flow Moods* masih terkunci pada satu kategori mood tunggal (*single-mood*), belum *mood-arc* kontinu.
- **YouTube Music (Fitur Produk *Mood Filters* & *Up Next*):** Memakai filter suasana hati (*Energize, Relax, Focus, Sad*) dan rekomendasi sekuensial berbasis sesi. *Batasan:* Fokus pada *engagement* & riwayat tonton/dengar, belum menyelaraskan trajektori emosi *outro-intro* 2 Hz.
- **Apple Music (Fitur Produk *Mood Stations* & *Crossfade/AutoMix*):** Menggabungkan kurasi editorial manusia, *collaborative filtering*, dan transisi *beat/tempo*. *Batasan:* Halus di sisi ritme audio saat *crossfade*, namun belum memodelkan lintasan emosi 2D $V\text{-}A$ secara matematis.

### Slide F1 — Urgency, Akar Masalah, & Gap Riset (Pilar 1–4)
- **Topik & Judul (Pilar 1–2):** *Music Information Retrieval* (MIR) / *Sequential Music Recommendation* — *"Mood-Arc Playlist Generation Berbasis Dynamic Mood Trajectory Menggunakan K-Nearest Neighbors dan Trajectory Alignment"*.
- **Urgensi Industri & Akar Masalah (Pilar 3):** Layanan *streaming* butuh playlist yang mengalir mengikuti aktivitas; lompatan mood kasar ($\Delta > 0{,}25$) menaikkan *skip rate* hingga **37%**.
- **Kritik Baseline & Bukti Empiris (Pilar 4):** Model acuan Gaur & Donnelly (2023) masih memakai *static-point matching* $(\bar{v}, \bar{a})$ per lagu, padahal **98,11%** (1.768/1.802) klip DEAM bergeser kuadran secara internal ($\Delta = 0{,}1937$).
- **Kalimat Gap Tegas:** *"Belum ada studi yang menguji apakah mempertimbangkan trajectory dinamis mood dalam lagu menghasilkan transisi playlist mood-arc yang lebih koheren dibandingkan pendekatan static-point matching."*

### Slide F2 — Rumusan Masalah, Tujuan 1:1, & Batasan (Pilar 5–7)
- **Keselarasan 1:1 RM $\leftrightarrow$ TP (Pilar 5–6):**
  1. **RM 1 $\leftrightarrow$ TP 1:** Merancang *pipeline* 2-tahap (KNN + *Dynamic Trajectory Alignment* & $\mathcal{BJC}$).
  2. **RM 2 $\leftrightarrow$ TP 2:** Menguji $\mathcal{S}$, $\mathcal{E}$, $\mathcal{CBJC}$ vs Baseline Gaur & Naive Random (target $\mathcal{S}$ turun $\ge 15\%$, Wilcoxon $p < 0{,}05$).
  3. **RM 3 $\leftrightarrow$ TP 3:** Validasi perseptual via *Blind A/B Listening Test* ($N \ge 30$) & korelasi Spearman dengan metrik objektif.
- **7 Batasan Masalah (Pilar 7):** 1) 2D $V\text{-}A$ Russell $[-1{,}0, +1{,}0]$; 2) DEAM 1.802 klip (45s); 3) buang 15s awal $\to$ 30s stabil (60 *timestamp*, 2 Hz); 4) *Blind A/B* klip sambungan 30s; 5) KNN deterministik; 6) non-*real-time*; 7) panjang playlist $M \in \{5, 10, 15\}$.

### Slide F3 — Landasan Teori, Data DEAM, & Metode Usulan (Pilar 8–10, 13–14)
- **Landasan Teori (Pilar 8):** Model Sirkumpleks Russell (1980) + Belaref (2024), *Boundary Jump Cost* (Wang 2024 REMAST), & retensi pendengar (Schweiger 2025).
- **Dataset & Anti-Leakage (Pilar 9):** DEAM 1.802 klip 45s (2 Hz), *song-level holdout split* (Train 70% / Val 15% / Test 15%), serta catatan limitasi klip 45s & anotasi *crowd*.
- **Arsitektur 2-Tahap Usulan (Pilar 10, 14):**
  - **Tahap 1:** Linear *waypoint* $\mathbf{w}_j$ + KNN Retrieval ($K=20$).
  - **Tahap 2 (Kontribusi Inti):** Ekstraksi vektor *intro* (15–18s) & *outro* (42–45s), cosine similarity arah trajektori ($\mathrm{Sim}_{\mathrm{traj}}$), penalti $\mathcal{BJC}$, dan skor komposit berbobot ($w_1+w_2+w_3=1$).
- **Pemisahan Kontribusi (Pilar 13):** **Replikasi** (pipeline KNN Gaur, metrik PCC/Evenness) vs **Baru** (trajektori 2 Hz, *trajectory alignment* + $\mathcal{BJC}$, evaluasi lintas kuadran + ablasi + *Blind A/B*).

### Slide F4 — Evaluasi, Uji Ablasi, Risiko, & Etika (Pilar 11–12, 15–16)
- **Komparasi & Uji Ablasi (Pilar 11–12):** Replikasi Gaur + Naive Random + **Ablation (*Trajectory Filter ON vs OFF*)** berlandaskan `meyes2019ablation` & `bendada2023scalable` pada **540 *batch run*** (6 rute kuadran) + Wilcoxon ($\alpha = 0{,}05$).
- **Validasi Manusia & Etika (Pilar 16):** *Blind A/B* ($N \ge 30$, Likert 5 poin, *Cronbach's Alpha* $\ge 0{,}70$, *Spearman*), *informed consent*, dan anonimisasi `R01–R30` sesuai **UU PDP No. 27/2022**.
- **Manajemen Risiko & Fallback (Pilar 15):** Jika *trajectory filter* tidak signifikan di semua rute, fokus analisis diagnostik per kuadran & pembuktian artefak PCC statis pada rute lintas kuadran.

> [!tip] Acuan Diagram Alur Visual (`05-Eksperimen/`)
> Saat menjelaskan F1–F4 ke dosen, gunakan 4 diagram alur & kamus istilah sederhana di:
> - [[05-Eksperimen/Alur-Uji-Coba-Baseline-Gaur]]
> - [[05-Eksperimen/Alur-Metode-Usulan-Trajectory-Alignment]]
> - [[05-Eksperimen/Alur-Evaluasi-Komparatif-dan-Ablasi]]
> - [[05-Eksperimen/Alur-Blind-AB-Listening-Test]]

---

## Bagian II: Todolist Coding Typst (Arsitektur Terbaru `Slides/`)

### Tahap 1: Metadata & Sinkronisasi Aset
- [x] **1.1 Isi `Slides/metadata.toml` dengan data resmi:** Pastikan `student.name`, `student.nim`, `research.title`, `research.specialization`, `research.stage`, dan `supervision.advisor` sesuai dengan `config/informations.tex` (bukan placeholder `[...]`) saat hendak dipakai presentasi resmi.
- [ ] **1.2 Sinkronkan aset eksperimen:**
  ```powershell
  powershell -File "Slides\scripts\sync_experiment_assets.ps1"
  ```
- [x] **1.3 Verifikasi arsitektur tema:** Pastikan seluruh berkas `.typ` memakai *relative path* (`../../templates/itera_theme.typ` untuk `02-Progress/` dan `../templates/itera_theme.typ` untuk `01-Sempro/`) serta **tidak** memakai `#memory-recall(...)`.

### Tahap 2: Pembuatan Slide Bimbingan dari Fundamental TA (`Slides/02-Progress/`)
- [x] **2.1 Gunakan template mingguan terbaru:** Salin [`Slides/02-Progress/00-Template-Mingguan/template_mingguan.typ`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Slides/02-Progress/00-Template-Mingguan/template_mingguan.typ) (atau perbarui `01-Minggu-01-Baseline-DEAM/progres_m01.typ`).
- [x] **2.2 Slide 1 (`#cover-slide`):** Isi `title` dan `subtitle: "Laporan Progress Bimbingan Tugas Akhir — Pertemuan #[x] — [Tanggal]"`, serta pertahankan `specialization: none, stage: none, meeting-date: none` agar hanya `Judul`, `Nama dan NIM`, dan `Pembimbing` yang tampil dari `metadata.toml`.
- [x] **2.3 Blok Slide Fundamental TA (Slide F0–F4 — Penjelasan dari Paling Dasar):** Tambahkan 5 slide ringkas memakai `#slide-header`, `#grid`, dan `#card-box` sebelum masuk ke progres teknis:
  - **F0 (Slide 2):** Bedah kata per kata dari Judul TA (4 `#card-box`: `Mood-Arc Playlist Generation`, `Dynamic Mood Trajectory`, `K-Nearest Neighbors`, `Trajectory Alignment`).
  - **F1 (Slide 3 — Urgency & Gap):** Masalah industri (*skip rate* 37%), kritik *static-point* Gaur, fakta 98,11% DEAM, & *Research Gap*.
  - **F2 (Slide 4):** Peta 1:1 (3 RM $\leftrightarrow$ 3 TP) + 7 butir *Scope/Batasan*.
  - **F3 (Slide 5):** DEAM 2 Hz + Arsitektur 2-Tahap (*KNN* $K=20$ + *Dynamic Trajectory Alignment* & $\mathcal{BJC}$) + tabel **Replikasi vs Kontribusi Baru**.
  - **F4 (Slide 6):** Skema Uji (540 *batch run*, *Ablation ON vs OFF*, Wilcoxon, *Blind A/B* $N \ge 30$, UU PDP 27/2022, *Fallback Plan*).
- [x] **2.4 Slide Matriks Progres:** Isi 3 `#card-box` (`DONE`, `IN_PROGRESS`, `BLOCKED`) yang mencerminkan capaian riil Fase 0, replikasi baseline DEAM, dan poin keputusan pembimbing.
- [x] **2.5 Slide Bukti Empiris DEAM:** Tampilkan `#image("../../assets/experiments/baseline_deam_traversal_plot.png")` dan ringkasan `metrics_comparison_deam.csv` + temuan artefak rute diagonal vs lintas kuadran.
- [x] **2.6 Slide Konsultasi (Dipisah: Fokus Bab I vs Bridging ke Bab II) & Slide Rencana Kerja:**
  - **Kartu A — Fokus Langsung Bab I (`chapter-1.tex`):**
    1. **Topik MIR (`1.1`):** Apakah topik *Mood-Arc Playlist Generation* sudah tepat dan layak untuk Tugas Akhir?
    2. **Relevansi Dataset DEAM (`1.1 & 1.4`):** Dataset DEAM rilis 2017/2018 — apakah masih relevan & diterima penguji karena anotasi kontinu 2 Hz-nya?
    3. **RM, Tujuan 1:1, & 7 Batasan (`1.2–1.4`):** Apakah target ($\mathcal{S}$ turun $\ge 15\%$, Wilcoxon $p < 0{,}05$, $N \ge 30$) dan 7 Batasan Masalah sudah realistis untuk S1?
  - **Kartu B — Pertanyaan Bridging ke Bab II (`chapter-2.tex`):**
    1. **Geometri & Kritik Statis (`2.1.1 & 2.1.3`):** Apakah landasan Russell + Belaref (2024) dan hilangnya 15–35% variansi (Pyrovolakis 2022) cukup membenarkan kritik terhadap Gaur?
    2. **Boundary Jump ke Kerangka (`2.1.4, 2.2.1, 2.3`):** Apakah alur dari *Boundary Jump Problem* (Wang 2024 REMAST) ke Sintesis Kesenjangan Riset & Kerangka Pemikiran sudah mulus?
    3. **Dual Evaluation (`2.1.5`):** Karena *agreement* metrik vs manusia hanya $r = 0{,}42$–$0{,}58$ (Daikoku 2022), apakah protokol *Blind A/B* (Likert, $\alpha \ge 0{,}70$, UU PDP 27/2022) di Bab II sudah memadai?

### Tahap 3: Promosi Materi ke Slide Seminar Proposal (`Slides/01-Sempro/sempro_slides.typ`)
- [ ] **3.1 Sinkronkan 15 Slide Sempro:** Setelah materi fundamental & progres disetujui pembimbing, petakan 16 pilar dari Fase 0 ke [`Slides/01-Sempro/sempro_slides.typ`](file:///D:/Kuliah/Semester%207/Tugas%20Akhir/Proposal%20Tugas%20Akhir/Slides/01-Sempro/sempro_slides.typ) (fokus presentasi Sempro: Slide 1, 4, 5, 6, 7, 8, dan 15 untuk durasi tepat 10 menit).
- [ ] **3.2 Pastikan konsistensi angka:** Cek ulang bahwa seluruh angka di `sempro_slides.typ` (98,11% DEAM, 540 *batch run*, $\mathcal{S} \ge 15\%$, $N \ge 30$) sama persis dengan `chapters/chapter-1.tex` s.d. `chapter-3.tex`.

### Tahap 4: Kompilasi Otomatis (`Ctrl + S`) & Audit Visual PDF
- [ ] **4.1 Uji Auto-Build VS Code:** Buka file `.typ` dan tekan `Ctrl + S` — pastikan Tinymist (`.vscode/settings.json`) langsung memperbarui PDF di folder yang sama.
- [ ] **4.2 Kompilasi cadangan via CLI:**
  ```powershell
  & "D:\Typst\typst-x86_64-pc-windows-msvc\typst.exe" compile --root "Slides" "Slides\02-Progress\00-Template-Mingguan\template_mingguan.typ" "Slides\02-Progress\00-Template-Mingguan\template_mingguan.pdf"
  ```
- [ ] **4.3 Audit Visual:** Pastikan tidak ada halaman yang mengalami *overflow* (Slide 1 tetap 1 halaman penuh, setiap `#card-box` di F0–F4 muat tanpa terpotong).
