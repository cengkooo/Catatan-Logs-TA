---
title: "Panduan Cepat: Format Isi Tugas Akhir (BAB 7)"
tags:
  - panduan-ta
  - format-isi
  - cheat-sheet
---

# 📖 Format Isi Tugas Akhir (BAB 7) — Versi Ringkas & ADHD-Friendly

> **Tujuan:** Panduan cepat struktur isi Bab I s/d Bab V tanpa bertele-tele. Langsung ke intinya!

---

## ⚡ TL;DR: Peta 5 Bab dalam 1 Tabel

| Bab | Nama Bab | Isi Inti yang Dicari Penguji |
| :---: | :--- | :--- |
| **I** | **Pendahuluan** | Mengapa masalah ini penting? Apa gap risetnya? Pertanyaan penelitiannya apa? |
| **II** | **Tinjauan Pustaka** | Teori dasar, tabel perbandingan riset terdahulu (*State of the Art*), dan kerangka pikir. |
| **III** | **Metodologi** | *Flowchart* langkah kerja, detail dataset, rancangan algoritma, metrik evaluasi. |
| **IV** | **Hasil & Pembahasan** | Grafik/tabel data hasil eksperimen + analisis mengapa hasilnya begitu + perbandingan ke baseline. |
| **V** | **Kesimpulan & Saran** | Jawaban langsung pertanyaan Bab I (tanpa muter-muter) + saran tindak lanjut konkret. |

---

## 📌 Rincian Per Bab (Checklist Praktis)

### 🔹 BAB I: PENDAHULUAN
* [ ] **1.1 Latar Belakang:** 
  * Buka dari masalah nyata industri (misal: transisi playlist Spotify/Deezer), bukan teori akademis basi.
  * Tunjukkan **GAP** (kelemahan model statis titik $V-A$ Gaur & Donnelly).
  * Wajib ada data empiris & referensi 5 tahun terakhir.
* [ ] **1.2 Rumusan Masalah:** Berupa kalimat tanya spesifik yang terukur (ada 3 poin di TA kita).
* [ ] **1.3 Tujuan Penelitian:** Menggunakan kata kerja operasional (*menganalisis, merancang, mengevaluasi*). Poinnya harus klop 1:1 dengan rumusan masalah.
* [ ] **1.4 Batasan Penelitian:** Kunci ruang lingkup agar tidak melebar (Dataset DEAM 45 detik, model emosi 2D Russell).
* [ ] **1.5 Manfaat Penelitian:** Manfaat teoretis (ilmu MIR) & praktis (pengembang aplikasi musik).
* [ ] **1.6 Sistematika Penulisan:** 1 paragraf ringkas merangkum Bab I–V.

---

### 🔹 BAB II: TINJAUAN PUSTAKA
* [ ] **2.1 Landasan Teori:** Konsep ruang emosi Valence-Arousal, fitur audio MIR, algoritma KNN.
* [ ] **2.2 Penelitian Terdahulu (*State of the Art*):** 
  * Wajib ada **Tabel Komparasi** (Peneliti, Tahun, Dataset, Metode, Hasil Utama, Limitasi).
  * *Bukan sekadar dongeng rangkuman paper!*
* [ ] **2.3 Kerangka Pemikiran:** Diagram alur konsep yang menjembatani teori ke metodologi Anda.

---

### 🔹 BAB III: METODOLOGI
* [ ] **3.1 Alur Penelitian:** Diagram alir (*flowchart*) langkah dari awal sampai laporan.
* [ ] **3.2 Pengumpulan Data:** Detail dataset DEAM (1802 lagu, sampling 2 Hz / 0.5s, sumber, data split).
* [ ] **3.3 Perancangan Model/Sistem:** Arsitektur pipeline 2-tahap (Tahap 1: KNN kandidat $\rightarrow$ Tahap 2: Filtering berbasis trajectory alignment).
* [ ] **3.4 Lingkungan Eksperimen:** Spesifikasi hardware (RAM, CPU/GPU) & software (Python versi X, Librosa, Scikit-learn).
* [ ] **3.5 Metode Pengujian & Evaluasi:** Rumus matematis metrik *Smoothness* ($\mathcal{S}$) dan *Evenness* ($\mathcal{E}$).

---

### 🔹 BAB IV: HASIL DAN PEMBAHASAN *(Untuk TA 2)*
* [ ] **4.1 Hasil Penelitian:** Tampilkan grafik dan tabel hasil perbandingan usulan vs baseline.
* [ ] **4.2 Analisis dan Pembahasan:** 
  * **Paling penting:** Jelaskan *mengapa* hasilnya begitu?
  * Hubungkan kembali dengan temuan paper di Bab II.
* [ ] **4.3 Keterbatasan:** Akui secara jujur limitasi eksperimen (durasi 45s, noise anotator).

---

### 🔹 BAB V: KESIMPULAN DAN SARAN *(Untuk TA 2)*
* [ ] **5.1 Kesimpulan:** Menjawab langsung butir-butir rumusan masalah di Bab I.
* [ ] **5.2 Saran:** Rekomendasi konkret untuk peneliti berikutnya (jangan cuma "perlu penelitian lebih lanjut").

---

## 🚫 Jebakan yang Bikin Dosen Penguji Marah (Do's & Don'ts)

| Dilarang (✗) | Lakukan (✓) |
| :--- | :--- |
| Judul tabel di bawah tabel | Judul tabel **SELALU di ATAS tabel** (center, bold). |
| Judul gambar di atas gambar | Judul gambar **SELALU di BAWAH gambar** (center, bold). |
| Menaruh tabel/gambar tanpa disebut di teks | Wajib ada kalimat: *"Hasil uji disajikan pada Tabel 4.1..."* sebelum tabel muncul. |
| Kesimpulan mengulang panjang isi Bab IV | Kesimpulan to-the-point, padat, berupa poin-poin penemuan. |
| Klaim "lebih baik" tanpa angka | Sertakan persentase atau metrik: *"Meningkatkan smoothness sebesar 14.2%"*. |
