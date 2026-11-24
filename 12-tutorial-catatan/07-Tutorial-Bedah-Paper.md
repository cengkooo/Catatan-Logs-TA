---
title: "Panduan Master: Framework Bedah Paper Ilmiah 11 Langkah (Step 0 s.d. Step 10)"
tags:
  - tutorial
  - literatur
  - paper-review
  - research-gap
  - audit-forensik
date: 2026-11-24
---

# 🔬 Framework Bedah Paper Ilmiah (11 Langkah: Step 0 s.d. Step 10)

Dokumen ini memuat protokol baku audit forensik karya ilmiah untuk menyaring substansi, memverifikasi klaim empiris, mendeteksi cacat eksperimental (*red flags*), dan merumuskan *research gap* 3 lapis untuk Tugas Akhir Teknik Informatika ITERA.

---

## 🧭 Langkah Operasional Bedah Paper

### Step 0: Metadata dan Konteks
* **Venue Publikasi:** Jurnal atau konferensi apa, reputasi/kuartil (Q1–Q4 Scopus, SINTA 1–2, atau IEEE/ACM/ISMIR prosiding), tahun terbit, status peer-review vs preprint (arXiv).
* **Penulis & Afiliasi:** Rekam jejak riset laboratorium penulis pada topik Music Information Retrieval (MIR) atau Recommender Systems.
* **Tujuan Membaca:** Replikasi algoritma, benchmarking baseline, adopsi representasi fitur, atau sintesis gap.

### Step 1: Abstrak (Bedah 5 Komponen Inti)
* Konteks dan urgensi masalah riil.
* Gap spesifik yang diklaim belum terselesaikan.
* Pendekatan/metode yang diajukan.
* Hasil kuantitatif: Apakah menyajikan metrik numerik konkret atau sekadar klaim kualitatif seperti *"outperforms state-of-the-art"*?
* Implikasi praktis/teoretis.
* *Acid Test:* Apakah setelah membaca abstrak Anda dapat menjelaskan apa yang dikerjakan tanpa membaca isi? Jika hanya klaim kualitatif tanpa angka, beri tanda **Red Flag**.

### Step 2: Pendahuluan (Problem Framing)
* **Spesifisitas Masalah:** Seberapa terukur definisi masalahnya?
* **Motivasi:** Apakah memiliki *real-world impact* (pengalaman pengguna pada streaming platform) atau murni artifisial akademis?
* **Gap Statement Audit:** Penulis menyatakan *"belum ada penelitian tentang X"*. Verifikasi apakah klaim tersebut faktual atau sekadar literatur yang kurang lengkap.
* **Kontribusi:** Tulis ulang daftar kontribusi di akhir pendahuluan menggunakan bahasa sendiri.

### Step 3: Related Work (Telaah Kritis)
* Bagaimana penulis mengelompokkan taksonomi pendekatan terdahulu?
* Apakah perbandingan dengan model pembanding dilakukan secara adil (*fair comparison*)?
* *Citation Gap:* Apakah ada paper seminal atau metode mutakhir yang sengaja dilewati?

### Step 4: Metodologi (Komponen Paling Kritis)
* **Formulasi Masalah:** Input, output, dan *objective function* eksplisit secara matematis atau hanya tersirat?
* **Asumsi Teoretis:** Distribusi data stasioner? Label independen? Kualitas anotasi?
* **Reproduktibilitas Algoritma:** Apakah hyperparameter dan arsitektur cukup detail untuk direplikasi mandiri dalam kode Python?
* **Komponen Novel vs Pinjaman:** Mana kontribusi yang benar-benar baru dibanding modul pustaka umum (*off-the-shelf*)?
* **Kompleksitas Komputasi:** Big-O waktu ($O(N)$), kebutuhan memori RAM/VRAM, dan latensi inferensi.

### Step 5: Setup Eksperimen (Titik Rawan Cacat Riset)
* **Dataset:** Sumber data, ukuran korpus, durasi klip, distribusi kelas emosi, dan potensi bias sampling.
* **Data Split & Leakage Audit:** Apakah train/validation/test terpisah bersih? **Peringatan Keras:** *Random split* pada data deret waktu (*time series*) atau klip dari artis/lagu yang sama adalah **Red Flag** fatal (*data leakage*).
* **Kekuatan Baseline:** Apakah baseline kuat (*state-of-the-art*) atau sekadar *strawman baseline* yang sengaja diset tanpa tuning agar metode usulan terlihat unggul?
* **Kesesuaian Metrik:** Apakah metrik evaluasi objektif dan sensitif terhadap dinamika masalah?
* **Rigoritas Pengujian:** Jumlah percobaan multi-seed, standar deviasi ($\pm \sigma$), atau *Confidence Interval* (CI 95%). *Single-run score* sangat lemah.

### Step 6: Hasil (Klaim vs Bukti Empiris)
* **Transparansi Tabel Utama:** Menampilkan seluruh skenario atau hanya metrik terbaik yang dipilih (*cherry-picked*)?
* **Besaran Peningkatan (*Effect Size*):** Apakah lompatan performa melampaui variasi acak (*noise*) antar run?
* **Ablation Study:** Apakah ada pengujian modular untuk membuktikan setiap komponen usulan memang berkontribusi nyata?
* **Analisis Galat (*Error Analysis*):** Apakah penulis secara transparan membahas kasus kegagalan (*failure cases*) modelnya?
* **Generalisasi:** Apakah metode diuji pada dataset eksternal lintas domain?

### Step 7: Diskusi & Limitasi
* **Limitasi Tertulis vs Limitasi Tersembunyi:** Bandingkan limitasi yang diakui penulis dengan limitasi struktural yang tidak disebutkan (misal: ketergantungan pada anotasi manual mahal, komputasi berat, boundary jump).
* **Ancaman Validitas (*Threats to Validity*):** Internal validity (kausalitas performa), External validity (aplikabilitas dunia nyata), dan Construct validity (apakah metrik benar-benar mengukur kelancaran emosi pendengar).

### Step 8: Kesimpulan & Future Work
* **Overclaim Audit:** Apakah klaim di kesimpulan melampaui bukti numerik di bab hasil?
* **Petunjuk Arah Masa Depan:** *Future work* yang ditulis penulis sering kali menjadi kunci *research gap* yang siap kita ambil.

### Step 9: Sintesis Pencapaian (3 Kalimat Kunci)
Tuliskan sintesis padat dalam 3 kalimat:
1. **Kalimat 1 (Fakta Terbukti):** Apa yang secara empiris terbukti didukung data eksperimen.
2. **Kalimat 2 (Lompatan SOTA):** Seberapa signifikan lompatannya dibanding model acuan terdahulu.
3. **Kalimat 3 (Kegunaan Praktis):** Untuk siapa atau konteks sistem apa hasil ini paling bernilai.

### Step 10: Research Gap Tiga Lapis (*Three-Tier Gap*)
1. **Lapis 1 (Gap Klaim Penulis):** Masalah yang diidentifikasi oleh penulis di naskah aslinya.
2. **Lapis 2 (Gap Temuan Audit Kritis):** Limitasi yang tidak diselesaikan, asumsi yang belum diuji, atau cacat metodologi yang ditemukan saat membedah naskah.
3. **Lapis 3 (Gap Sintesis Multi-Paper):** Gap hasil kombinasi silang antar beberapa paper dalam matriks literatur (misal: Metode A + Dataset B + Metrik C yang belum pernah disatukan).

> **Formula Gap Statement Akademis:**  
> *"Meskipun [pendekatan A] terbukti [hasil] pada [konteks], belum ada kajian yang [menguji atau membandingkan X] pada [Y], padahal [alasan krusial mengapa ini penting]."*

---

## 🚩 Radar Red Flags (Waspadai Cacat Metodologis)
- [ ] Hasil hanya menyajikan 1 angka terbaik tanpa standar deviasi / multi-seed.
- [ ] Model pembanding (*baseline*) lemah atau tidak dioptimasi (*strawman*).
- [ ] Tidak ada *ablation study* yang memverifikasi kontribusi tiap modul.
- [ ] Evaluasi hanya pada 1 dataset kecil tanpa uji generalisasi.
- [ ] *Random split* pada data beruntun (*time-series* / klip potongan lagu serupa).
- [ ] Kode sumber dan dataset tertutup / tidak dapat direproduksi.
- [ ] Kesimpulan melebih-lebihkan bukti (*overclaim*).
- [ ] Metrik evaluasi tidak berkorelasi dengan persepsi pendengar manusia riil.
