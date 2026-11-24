---
title: "Panduan Kebijakan AI & Integritas Akademik Tugas Akhir IF ITERA"
tags:
  - panduan-ta
  - etika-ai
  - integritas-akademik
  - turnitin
  - code-walkthrough
source_ref: "Pedoman TA IF ITERA Bab 2 & Bab 4"
---

# 🤖 Kebijakan Penggunaan Kecerdasan Buatan (AI) & Integritas Akademik

> **Prinsip Utama (Bab 4.1):** AI diakui sebagai **alat bantu augmentasi**, bukan pengganti proses berpikir kritis dan tanggung jawab intelektual mahasiswa. Seluruh isi naskah, kode program, dan analisis data tetap merupakan tanggung jawab penuh mahasiswa.

---

## ⚡ 1. Framework 5 Tingkat Penggunaan AI (Bab 4.2)

Prodi Teknik Informatika mengklasifikasikan penggunaan AI ke dalam 5 tingkatan:

| Tingkat | Nama Kategori | Definisi & Batasan | Status ITERA |
| :---: | :--- | :--- | :---: |
| **1** | Tanpa AI (*No AI*) | Pengerjaan sepenuhnya manual tanpa interaksi tools AI generatif. | Diperbolehkan |
| **2** | AI untuk Pencarian Ide (*Ideation*) | Brainstorming kerangka bab, pencarian literatur awal, eksplorasi ide riset. | **Sangat Dianjurkan** |
| **3** | AI dalam Alur Kerja (*Workflow*) | *Debugging*, *code completion*, *refactoring*, generasi *boilerplate*, perbaikan tata bahasa, parafrasa. | **Dianjurkan (Proporsional)** |
| **4** | AI Mengerjakan Penuh (*AI Dominant*) | Meminta AI menulis seluruh bab atau arsitektur sistem tanpa pemahaman mendalam mahasiswa. | 🚫 **DILARANG KERAS** |
| **5** | Fabrikasi / Pemalsuan AI | Membuat data sintetis fiktif, merekayasa hasil eksperimen, atau mengutip paper palsu hasil halusinasi AI. | 🛑 **PELANGGARAN BERAT** |

---

## ⚖️ 2. Matriks Boleh vs Dilarang (Bab 4.3)

| Aspek | Diizinkan (✓) | DILARANG KERAS (✗) |
| :--- | :--- | :--- |
| **Penulisan Narasi** | Pengecekan tata bahasa, perbaikan kalimat (parafrasa kritis), penerjemahan abstrak ke bahasa Inggris. | Menghasilkan draf bab utuh secara otomatis (*prompting dump*), menyalin langsung teks AI tanpa verifikasi. |
| **Sitasi & Referensi** | Membantu memformat BibTeX atau mencari kata kunci pencarian paper. | **Sitasi Palsu/Halusinasi:** Mencantumkan referensi fiktif yang digenerasi oleh AI. Sitasi wajib berasal dari paper asli. |
| **Koding & Software** | Pembuatan modul *boilerplate* umum, bantuan *syntax error*, optimasi algoritma, pembuatan unit test. | Menghasilkan arsitektur perangkat lunak utama tanpa pemahaman; mahasiswa gagal saat *code walkthrough*. |
| **Data & Eksperimen** | Bantuan formula statistik, visualisasi grafik (*matplotlib/seaborn*), skrip pra-pemrosesan umum. | **Fabrikasi/Falsifikasi:** Memanipulasi metrik hasil uji (akurasi/F1/MAE) atau menciptakan data palsu. |

---

## 📋 3. Empat Kewajiban Terkait Penggunaan AI (Bab 4.4 & 4.5)

1. **Halaman Pernyataan Penggunaan AI (Lampiran 2):**
   - **Wajib** disertakan pada *front matter* laporan akhir (setelah halaman orisinalitas).
   - Mahasiswa wajib mendokumentasikan: nama tool AI (e.g. Gemini, ChatGPT, Claude), versi/model, komponen yang dibantu, dan verifikasi validasi manusia yang dilakukan.
2. **Arsip Log Interaksi AI:**
   - Mahasiswa wajib menyimpan riwayat chat (*prompt-response* log atau ekspor PDF) pada repositori kode / drive penelitian sebagai bukti pembelaan akademik jika diminta tim penguji.
3. **Riwayat Version Control (Git) yang Bertahap:**
   - Perkembangan kode dan naskah wajib tercatat pada commit Git berkala (minimal mingguan). *Single commit* atau upload massal file mendekati tenggat sidang dapat dicurigai sebagai indikasi pelanggaran.
4. **Code Walkthrough (Uji Kode Program):**
   - Tim penguji berhak meminta mahasiswa menjelaskan baris kode secara acak, merekayasa parameter (*what-if test*), dan mendemonstrasikan eksekusi langsung saat sidang akhir (bobot **10%** dari total nilai TA 2).

---

## 🔍 4. Standar Uji Kemiripan (Turnitin / iThenticate) (Bab 2.4 & 5.7)

* **Batas Maksimal Similarity Index:** $\le \mathbf{25\%}$ (setelah mengecualikan daftar pustaka/bibliography).
* **Batas Maksimal Kutipan Langsung (*Direct Quotes*):** $\le \mathbf{10\%}$ dari keseluruhan panjang dokumen.
* **Pengecualian Tim pada Capstone/Kelompok (Changelog 1.1.0 / Subbab 5.1.3):**
  - Kemiripan antar-laporan anggota satu tim pada bagian **konteks proyek bersama** (latar belakang mitra, arsitektur umum, tinjauan pustaka umum) diperbolehkan dan dapat dikecualikan dari perhitungan plagiarisme.
  - Metodologi, hasil eksperimen, analisis, dan kesimpulan bagian individu **wajib berbeda** dan tidak boleh tumpang-tindih.
