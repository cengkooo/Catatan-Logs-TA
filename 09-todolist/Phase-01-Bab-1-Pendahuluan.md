---
title: "Fase 01: Penulisan dan Penguatan Bab 1 Pendahuluan"
tags:
  - todolist
  - phase-1
  - bab1
  - naskah
  - unesco
  - toulmin
status: "COMPLETED / READY TO COMPILE"
opsi_terpilih: "Opsi A (Narasi Empiris dan Eliminasi Boundary Jump)"
gaya_penulisan: "Standar UNESCO ITERA, Bahasa Indonesia Baku, Tanpa Huruf Tebal, Tanpa Emdash"
---

# Fase 01: Penulisan dan Penguatan Bab 1 (Pendahuluan)

Tujuan dokumen ini adalah memberikan panduan eksekusi mikro yang sangat mendetail, tahap demi tahap, untuk menyusun dan menyinkronkan naskah Bab 1 ke proposal-penelitian-andryano-123140205/chapters/chapter-1.tex.

Seluruh butir tugas mematuhi Pedoman Penyelenggaraan Tugas Akhir Program Studi Teknik Informatika ITERA Tahun Akademik Genap 2025/2026, pedoman penulisan bahasa Indonesia teknis, serta arahan khusus pengguna: tanpa huruf tebal dan tanpa tanda baca emdash.

---

## 🏛️ Ketentuan Mutu dan Kepatuhan Akademik ITERA

Sebelum mengeksekusi setiap langkah, verifikasi pemenuhan parameter berikut:
* Ukuran dan Tata Letak: Standar UNESCO (15,5 cm x 23 cm), margin atas 2 cm, bawah 2 cm, luar 2 cm, dalam 2,5 cm.
* Tipografi: Huruf Times New Roman 11 pt, spasi baris 1,5, indentasi awal paragraf 1 cm, rata kiri-kanan (justify).
* Integritas Ilmiah: Indeks kemiripan Turnitin maksimal 25 persen setelah eksklusi daftar pustaka, batas kutipan langsung maksimal 10 persen, tanpa fabrikasi data atau referensi fiktif.
* Sitasi Pustaka: Menggunakan format IEEE, seluruh referensi wajib terdaftar pada references.bib, minimal 15 sumber primer dengan 70 persen terbitan 3 tahun terakhir (2023-2026).
* Batasan Khusus: Tidak menggunakan karakter emdash (sebagai pengganti, gunakan tanda koma, titik dua, tanda kurung, atau titik), serta tidak menggunakan huruf tebal pada isi teks narasi.

---

## 🎯 Sub-Fase 1.1: Penguatan Latar Belakang Masalah

- [x] Langkah 1.1.1: Narasi Urgensi Industri Streaming Musik
  - Aksi: Susun narasi pembuka mengenai pergeseran kebutuhan pendengar musik dari pencarian berbasis preferensi historis statis menuju transisi suasana hati yang terkontrol sepanjang sesi mendengarkan (mood arc).
  - Integrasi Data Industri: Rujuk adopsi fitur Flow Moods pada platform Deezer (Bontempelli et al., 2022) yang digunakan jutaan pengguna harian, serta penerapan reinforcement learning untuk sekuensial playlist di lingkungan industri (Tomasi et al., 2023).
  - Justifikasi Psikologis: Integrasikan temuan Schweiger et al. (2025) mengenai pengaruh koherensi sekuensial antarlagu terhadap kenyamanan dan retensi pendengar.
  - Kriteria Selesai: Pembaca memahami bahwa pengendalian lintasan emosi sekuensial adalah kebutuhan industri nyata berskala besar, bukan sekadar eksplorasi teoritis.

- [x] Langkah 1.1.2: Pemetaan Literatur Akademis dan Landasan Afektif
  - Aksi: Hubungkan gagasan mood arc dengan eksplorasi awal pada prototipe MOODetector (Cardoso et al., 2011) yang memetakan jalur pada ruang emosi 2D Arousal-Valence.
  - Landasan Teoretis: Jelaskan fondasi model sirkumpleks Russell (1980) yang mendasari komputasi afektif musik dengan memetakan emosi ke dalam dimensi arousal (energi) dan valence (derajat kesenangan).
  - Pemaparan Acuan Utama: Jelaskan metodologi dua tahap Gaur dan Donnelly (2024) yang mengombinasikan K-Nearest Neighbors (KNN) dan penyaringan kemiripan akustik pada dataset DMDD (Delbouys et al., 2018).
  - Kriteria Selesai: Silsilah metodologi tersusun runtut dari model psikologi emosi hingga algoritma acuan utama.

- [x] Langkah 1.1.3: Dekonstruksi Struktural Baseline Gaur dan Identifikasi The Boundary Jump Problem
  - Aksi: Bedah limitasi mendasar pendekatan pencocokan titik statis (static-point matching) Gaur dan Donnelly (2024). Tegaskan bahwa akar kelemahan terletak pada struktur data DMDD yang hanya menyediakan satu nilai rata-rata per lagu, bukan pada desain algoritmanya.
  - Penamaan Fenomena Resmi (Opsi A): Perkenalkan secara eksplisit konsep The Boundary Jump Problem, yaitu diskontinuitas perseptual tajam yang terjadi ketika detik-detik akhir lagu pertama bersambung dengan detik-detik awal lagu berikutnya yang berkarakter kontras, meskipun kedua lagu memiliki nilai rata-rata yang sama.
  - Penyajian Bukti Replikasi Baseline: Paparkan fakta empiris hasil pengujian 540 batch run bahwa nilai smoothness Gaur yang tinggi (0,9950) hanya merupakan artefak rute diagonal buatan (Q3 ke Q1), sedangkan pada rute lintas kuadran (Q1 ke Q2 dan Q1 ke Q4), skor smoothness baseline anjlok ke rentang 0,6628 hingga 0,7189 akibat ketiadaan informasi titik batas sambungan.
  - Kriteria Selesai: Kelemahan acuan utama terbedah secara matematis-struktural tanpa merendahkan reputasi paper publikasi aslinya.

- [x] Langkah 1.1.4: Injeksi Bukti Empiris Keras dari Dataset DEAM
  - Aksi: Tampilkan profil komputasional dataset benchmark DEAM (Aljanaki et al., 2017) yang memuat 1.802 lagu dengan anotasi kontinu 2 Hz yang dinilai manusia setiap 0,5 detik.
  - Data Kuantitatif Keras: Sajikan fakta empiris bahwa 98,11 persen lagu pada DEAM mengalami pergeseran posisi koordinat afektif nyata sepanjang durasinya, dengan rata-rata perpindahan jarak Euclidean awal ke akhir sebesar delta = 0,1937 dan rentang dinamis intra-lagu mencapai hingga 0,5950.
  - Penegasan Konsekuensi: Tuliskan argumen bahwa menyederhanakan lagu menjadi satu titik rata-rata statis sama dengan membuang 15 hingga 35 persen variansi informasi afektif yang terkandung di dalam rekaman musik.
  - Kriteria Selesai: Urgensi penelitian berdiri di atas data empiris terukur, bukan sekadar asumsi kualitatif.

- [x] Langkah 1.1.5: Pernyataan Kesenjangan Riset (Research Gap) Eksplisit
  - Aksi: Rumuskan satu kalimat tegas kesenjangan riset: Belum ada studi yang menguji apakah mempertimbangkan orientasi pergerakan trajectory dinamis mood dalam lagu menghasilkan transisi playlist mood-arc yang lebih koheren dan minim lonjakan batas dibandingkan pendekatan static-point matching.
  - Penjelasan Kontekstual: Jelaskan bahwa penelitian terdahulu tidak dapat menjawab pertanyaan ini karena dataset DMDD tidak menyediakan dimensi waktu deret berkala emosi.
  - Kriteria Selesai: Kesenjangan riset terbaca jelas, mandiri, dan tidak dapat dibantah penguji.

- [x] Langkah 1.1.6: Pemosisian Kontribusi dan Usulan Solusi
  - Aksi: Posisikan kontribusi tugas akhir secara proporsional sebagai perluasan inovatif pada dimensi trajectory dinamis.
  - Peran Peneliti: Rancang pipeline end-to-end yang mengintegrasikan kriteria penyelarasan trajektori (trajectory alignment) pada tahap penyaringan lagu, pembentukan metrik evaluasi Arc-Trajectory Alignment Score, serta pembuktian empiris komparatif.
  - Kriteria Selesai: Kontribusi tugas akhir didefinisikan secara realistis dan terukur.

---

## 🎯 Sub-Fase 1.2: Perumusan Masalah Berbasis SMART

- [x] Langkah 1.2.1: Rumusan Masalah 1 (Aspek Rekayasa dan Desain Sistem)
  - Rumusan: Bagaimana merancang dan mengimplementasikan pipeline mood-arc playlist generation modular dua tahap yang mengintegrasikan dynamic mood trajectory alignment ke dalam mekanisme penyaringan lagu setelah pengambilan kandidat berbasis K-Nearest Neighbors?
  - Target Jawaban: Spesifikasi modul dua tahap, representasi vektor lereng (slope), dan formulasi fungsi biaya penalti transisi batas.

- [x] Langkah 1.2.2: Rumusan Masalah 2 (Aspek Evaluasi Komparatif Objektif)
  - Rumusan: Apakah playlist yang dihasilkan dengan mempertimbangkan trajectory alignment menghasilkan reduksi The Boundary Jump Problem serta peningkatan metrik smoothness dan evenness yang signifikan dibandingkan replikasi baseline static-point matching Gaur dan Donnelly?
  - Target Jawaban: Tabel perbandingan metrik head-to-head disertai uji signifikansi statistik Wilcoxon signed-rank test.

- [x] Langkah 1.2.3: Rumusan Masalah 3 (Aspek Karakterisasi Dinamika dan Batas Ambang)
  - Rumusan: Pada karakteristik variabilitas dinamika intra-lagu seperti apa pendekatan trajectory alignment memberikan peningkatan kualitas playlist paling signifikan, dan pada batas ambang variansi berapakah metode ini secara asimtotik tereduksi menjadi static-point matching?
  - Target Jawaban: Analisis batas ambang (epsilon-threshold) yang membuktikan kapan trajectory-aware unggul mutlak dan kapan sistem tereduksi mulus tanpa degradasi.

- [x] Langkah 1.2.4: Justifikasi Kelayakan Akademik
  - Aksi: Paparkan bahwa ketiga pertanyaan di atas memenuhi syarat kelayakan tugas akhir ITERA: mencakup proses perancangan sistem utuh, implementasi perangkat lunak mandiri, dan pengujian empiris yang dapat diverifikasi pada code walkthrough.

---

## 🎯 Sub-Fase 1.3: Penyelarasan Tujuan Penelitian

- [x] Langkah 1.3.1: Perumusan Tujuan Umum
  - Rumusan: Mengembangkan dan mengevaluasi sistem mood-arc playlist generation yang mengintegrasikan penyelarasan trajectory dinamis emosi lagu guna menghasilkan transisi antarlagu yang mulus, teratur, dan minim lonjakan batas emosional.

- [x] Langkah 1.3.2: Perumusan Lima Tujuan Khusus Terukur
  - Butir 1: Mengimplementasikan pipeline dua tahap yang modular: tahap pertama pencarian kandidat lagu terdekat menggunakan KNN pada ruang emosi Arousal-Valence, dan tahap kedua penyaringan yang dapat menerima kriteria akustik konvensional maupun trajectory alignment.
  - Butir 2: Mengekstraksi vektor lereng trajectory dari anotasi dinamis DEAM untuk 1.802 lagu sebagai representasi arah pergerakan emosi internal lagu.
  - Butir 3: Merumuskan dan menghitung metrik Arc-Trajectory Alignment Score sebagai instrumen evaluasi keselarasan arah orientasi mikro-lagu terhadap target makro-arc playlist.
  - Butir 4: Mengevaluasi dan membandingkan performa playlist pada kondisi trajectory-aware, replikasi baseline Gaur dan Donnelly, serta baseline acak menggunakan metrik smoothness, evenness, boundary jump cost, dan Arc-Trajectory Alignment Score.
  - Butir 5: Menganalisis kondisi ambang batas variabilitas musik di mana trajectory alignment memberikan keunggulan paling signifikan serta mengidentifikasi kondisi saat metode tereduksi secara mulus menjadi model titik statis.

---

## 🎯 Sub-Fase 1.4: Batasan Masalah dan Rebuttal Falsifikasi

- [x] Langkah 1.4.1: Batasan Korpus Dataset
  - Menggunakan dataset publik DEAM (1.802 lagu, lisensi Creative Commons) dengan anotasi kontinu 2 Hz. Mengabaikan 15 detik pertama sesuai rekomendasi resmi dataset untuk menghindari instabilitas anotasi awal.
- [x] Langkah 1.4.2: Batasan Model Dimensi Emosi
  - Dibatasi pada ruang 2D kontinu Arousal-Valence Russell rentang [-1, 1]. Dimensi dominansi dan model emosi kategorikal tidak dimodelkan.
- [x] Langkah 1.4.3: Batasan Representasi Trajektori
  - Vektor pergerakan emosi lagu diturunkan dari koefisien lereng regresi linear deret waktu valence dan arousal yang dinormalisasi menjadi vektor satuan. Model deret waktu berbobot komputasi berat seperti recurrent neural network atau transformer tidak digunakan agar sistem tetap ringan dan deterministik.
- [x] Langkah 1.4.4: Batasan Ekstraksi Fitur Akustik
  - Menggunakan ekstraksi fitur akustik baku berbasis librosa (tempo, MFCC, spectral contrast, chroma). Representasi embedding deep learning skala besar seperti model MERT berada di luar cakupan.
- [x] Langkah 1.4.5: Batasan Skenario Lintasan Playlist
  - Pengujian dijalankan pada 3 hingga 5 rute mood arc tipikal dengan panjang playlist sekitar 10 trek lagu dan variasi parameter pembobotan seleksi alfa.
- [x] Langkah 1.4.6: Batasan Lingkup Pengujian
  - Evaluasi mutu playlist difokuskan pada pengujian komputasional objektif. Uji dengar subjektif manusia berskala luas ditempatkan sebagai rekomendasi penelitian lanjutan.
- [x] Langkah 1.4.7: Lingkungan Komputasi Sistem
  - Sistem direkayasa sebagai pipeline luring berbasis Python yang dapat direproduksi penuh pada perangkat keras lokal mahasiswa.
- [x] Langkah 1.4.8: Mekanisme Reduksi Mulus (Kondisi Rebuttal Toulmin)
  - Jika sistem memproses katalog lagu yang tidak memiliki dinamika afektif internal yang nyata, fungsi penalti seleksi secara matematis tereduksi menjadi model static-point matching konvensional tanpa menimbulkan kegagalan sistem.

---

## 🎯 Sub-Fase 1.5: Artikulasi Manfaat Penelitian dan Sistematika Penulisan

- [x] Langkah 1.5.1: Penulisan Manfaat Akademik dan Praktis
  - Manfaat Akademik: Membuka wawasan pemanfaatan anotasi dinamis musik di luar tugas regresi emosi kontinu, yakni sebagai sinyal penentu sekuensial playlist.
  - Manfaat Praktis: Memberikan panduan kelayakan teknis bagi industri musik digital mengenai efektivitas investasi anotasi dinamis terhadap mutu kurasi playlist.
  - Manfaat bagi Mahasiswa dan Institusi: Memperkuat penguasaan pemrosesan sinyal audio dan rekayasa machine learning, serta mendukung luaran publikasi ilmiah bagi Program Studi Teknik Informatika ITERA.
- [x] Langkah 1.5.2: Penyusunan Sistematika Penulisan Laporan
  - Rangkum secara padat intisari Bab 1 Pendahuluan, Bab 2 Tinjauan Pustaka, Bab 3 Metodologi Penelitian, Bab 4 Hasil dan Pembahasan, serta Bab 5 Kesimpulan dan Saran.

---

## 🎯 Sub-Fase 1.6: Sinkronisasi LaTeX, Audit Kepatuhan, dan Kompilasi UNESCO

- [x] Langkah 1.6.1: Penulisan Kode LaTeX chapter-1.tex
  - Terapkan seluruh narasi hasil rekonstruksi ke dalam berkas proposal-penelitian-andryano-123140205/chapters/chapter-1.tex.
  - Pastikan tidak ada karakter tanda pisah emdash dan tidak ada tag huruf tebal di dalam paragraf narasi.

- [x] Langkah 1.6.2: Verifikasi Sitasi dan Entri references.bib
  - Pastikan seluruh kunci sitasi (bontempelli2022flowmoods, tomasi2023automatic, schweiger2025impact, eerola2026metaanalysis, gaur2024smooth, delbouys2018mood, aljanaki2017developing, russell1980circumplex, cardoso2011moodetector, li2024mert, gaur2023mooddynamic) terdaftar sah pada references.bib.

- [ ] Langkah 1.6.3: Kompilasi Dokumen LaTeX thesis.tex
  - Rantai kompilasi pdflatex dan bibtex siap dijalankan pada lingkungan kompilator LaTeX pengguna (Overleaf atau VS Code).

- [x] Langkah 1.6.4: Audit Tata Letak UNESCO dan Kesiapan Sidang
  - Periksa kesesuaian margin, font, dan pemisahan baris agar memenuhi standar naskah resmi Teknik Informatika ITERA.
  - Pastikan naskah siap digunakan sebagai bahan presentasi Sempro dan kartu kendali bimbingan dengan Dosen Pembimbing.
