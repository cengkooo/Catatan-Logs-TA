---
title: "Panduan Sidang Akhir (TA 2), Code Walkthrough & Batas Revisi IF ITERA"
tags:
  - panduan-ta
  - sidang-akhir
  - code-walkthrough
  - revisi
  - rubrik-penilaian
source_ref: "Pedoman TA IF ITERA Bab 5 & Bab 6"
---

# 🎓 Sidang Akhir (TA 2), Code Walkthrough & Ketentuan Revisi

> **Tujuan Sidang Akhir (Bab 5.1):** Menguji penguasaan komprehensif mahasiswa terhadap hasil penelitian/rekayasa perangkat lunak yang diselesaikan, keabsahan data, penguasaan kode program, serta kontribusi ilmiah/praktis.

---

## 📌 1. Persyaratan Pendaftaran Sidang Akhir (Tabel 5.5)

1. **Kelulusan Akademik:** Telah lulus TA 1 (Sempro) dan lulus seluruh mata kuliah wajib/pilihan (minimal **140 SKS** di luar mata kuliah TA 2).
2. **Form Validasi Dosen Wali:** Pernyataan tertulis/digital bahwa syarat SKS dan kelulusan MK prasyarat telah terpenuhi.
3. **Surat Persetujuan Sidang:** Disetujui Dosen Pembimbing (tanda tangan naskah atau persetujuan via **TASYS**).
4. **Log Bimbingan Intensif:** Form kendali bimbingan terisi lengkap membuktikan intensitas penyelesaian Bab IV dan V.
5. **Uji Turnitin / Plagiarisme:**
   - Similarity Index $\le \mathbf{25\%}$ (setelah exclude daftar pustaka).
   - Kutipan langsung $\le \mathbf{10\%}$.
6. **Halaman Pernyataan Penggunaan AI (Lampiran 2):** Terisi lengkap dan ditandatangani di atas meterai/digital.

---

## ⏱️ 2. Format Pelaksanaan & Alokasi Waktu Sidang (Total 85 Menit)

* **Sifat Ujian:** **TERTUTUP** (hanya dihadiri mahasiswa yang diuji, dosen pembimbing, dan majelis penguji).

| Sesi | Durasi | Fokus Kegiatan |
| :--- | :---: | :--- |
| **Pembukaan** | 5 Menit | Verifikasi administrasi dan pembacaan tata tertib oleh Ketua Majelis. |
| **Presentasi & Demo** | 15 Menit | Pemaparan hasil penelitian, temuan data Bab IV, dan demonstrasi sistem/prototype secara ringkas. |
| **Tanya Jawab & Code Walkthrough** | **50 Menit** | Pengujian substansi naskah, justifikasi metodologi, dan **bedah kode baris-demi-baris**. |
| **Deliberasi Majelis** | 10 Menit | Rapat penentuan kelulusan dan penetapan jenis revisi secara tertutup. |
| **Pengumuman Hasil** | 5 Menit | Pembacaan berita acara kelulusan dan rincian catatan revisi kepada mahasiswa. |

---

## 💻 3. Komponen Code Walkthrough (Bobot 10%)

Pada sidang akhir, penguji memiliki waktu khusus untuk menguji kepemilikan intelektual kode program mahasiswa:
* **Penguasaan Arsitektur:** Mahasiswa mampu menjelaskan diagram modul dan aliran data dari input ke output.
* **Tanya Jawab Baris Kode (*Line-by-line justification*):** Mahasiswa mampu membuka IDE/editor dan menjelaskan fungsi blok kode tertentu yang dipilih penguji.
* **Uji Skenario "What-If":** Mahasiswa mampu menjawab dampak perubahan parameter (misal: "Apa yang terjadi jika threshold kemiripan diubah dari 0.7 menjadi 0.4?").
* **Live Execution:** Kode program mampu dijalankan secara live tanpa error fatal saat didemonstrasikan di hadapan penguji.

---

## 📊 4. Komposisi Nilai Akhir TA 2 (Tabel 5.2 - Jalur 1 Penelitian Konvensional)

* Kualitas Laporan / Output TA: **30%**
* Presentasi & Pertahanan Jawaban: **20%**
* **Code Walkthrough / Penguasaan Teknis:** **10%**
* Proses Bimbingan & Sikap Ilmiah: **20%**
* Orisinalitas & Kontribusi: **20%**
* **Grade Kelulusan:** A ($\ge 80$), AB ($72,5–79,9$), B ($65,0–72,4$), Tidak Lulus ($< 65$).

---

## ⏳ 5. Batas Waktu Revisi Pasca-Sidang (Subbab 5.6)

> [!CAUTION]
> Melewati batas waktu maksimal revisi berakibat status kelulusan dibatalkan dan mahasiswa **wajib menempuh sidang akhir ulang**!

| Kategori Revisi | Kriteria Perbaikan | Batas Waktu Maksimal | Konsekuensi Status |
| :--- | :--- | :--- | :--- |
| **Lulus Murni** | Naskah sempurna tanpa revisi. | Langsung input nilai final. | Siap yudisium. |
| **Revisi Minor** | Perbaikan typo, tata kalimat, penyesuaian format referensi, perbaikan visual tabel/gambar (tidak mengubah Bab IV). | **14 hari kerja** | Nilai ditahan hingga lembar pengesahan ACC ditandatangani. |
| **Revisi Sedang** | Penambahan analisis terbatas, pengujian parameter tambahan, penyempurnaan metodologi ringan. | **30 hari kalender** | Nilai ditahan hingga lembar pengesahan ACC ditandatangani. |
| **Revisi Mayor** | Pengulangan eksperimen besar, perombakan Bab IV/V substansial. | **60 hari kalender** *(wajib izin tertulis Koordinator TA)* | Nilai ditahan; jika $>60$ hari belum selesai $\rightarrow$ Nilai E (Ulang Sidang). |
| **Belum Lulus** | Standar minimal penelitian tidak tercapai, plagiarisme fatal, atau gagal total dalam *code walkthrough*. | — | Dinyatakan Tidak Lulus, wajib mendaftar sidang ulang di periode berikutnya. |
