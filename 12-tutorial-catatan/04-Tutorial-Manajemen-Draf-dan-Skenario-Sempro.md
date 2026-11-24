---
title: "Tutorial 04: Manajemen Draf Naskah & Dua Skenario Evaluasi Sempro"
tags:
  - tutorial
  - naskah
  - skenario
  - turnitin
  - unesco-standard
date: 2026-11-24
---

# ✍️ Tutorial 04: Manajemen Draf Naskah & Dua Skenario Evaluasi Sempro

Folder `06-Naskah-Draft/` adalah ruang kerja utama Anda untuk menulis naskah proposal skripsi (Bab I, II, dan III) sebelum dikompilasi ke dalam template LaTeX standar buku UNESCO ITERA ($15,5 \times 23,0$ cm).

---

## 🧭 1. Memilih Antara Dua Skenario Naskah

Untuk mengantisipasi arahan dosen pembimbing (**Pak Hafiz Budi Firmansyah**), sistem telah menyediakan dua set naskah utuh yang independen:

### 🅰️ Folder `01-Skenario-Murni-Komputasional/`
* **Gunakan Skenario Ini Jika:** Pak Hafiz menyetujui evaluasi komputasional murni tanpa kuesioner pendengar manusia.
* **Ciri Khas Naskah:**
  - **Rumusan Masalah:** 3 butir (Arsitektur Pipeline KNN, Komparasi Head-to-Head vs Gaur 2020, Kuantifikasi Dinamika DEAM).
  - **Tujuan Penelitian:** 3 butir (Pipeline PyTorch GPU, Reduksi Smoothness $\ge 15\%$, Penurunan Penalti Batas $\mathcal{B}$).
  - **Batasan Masalah:** Butir 4 tegas mengecualikan uji dengar kuesioner (*user listening study*).
  - **Bab 3 Metodologi:** Berhenti pada Subbab 3.5 (Pengujian Metrik Matematis $\mathcal{S}, \mathcal{E}, \mathcal{B}$).

---

### 🅱️ Folder `02-Skenario-Dual-Evaluation-User-Study/` ⭐ *(Disarankan)*
* **Gunakan Skenario Ini Jika:** Pak Hafiz menginginkan adanya validasi persepsi langsung oleh manusia.
* **Ciri Khas Naskah:**
  - **Rumusan Masalah:** 4 butir (Memuat RM 4: Korelasi metrik matematis komputer dengan respon kenyamanan telinga manusia).
  - **Tujuan Penelitian:** 4 butir (Memuat TP 4: Uji signifikansi non-parametrik **Wilcoxon Signed-Rank Test $p < 0.05$**).
  - **Batasan Masalah:** Butir 4 membatasi pengujian pada **klip sambungan transisi 30 detik terhadap $N \ge 30$ responden** untuk mencegah kelelahan dengar (*listener fatigue*).
  - **Bab 3 Metodologi:** Memuat tambahan lengkap **Subbab 3.6 Metode Pengujian Subjektif (User Listening Study)** lengkap dengan formula korelasi peringkat Spearman.

---

## 🛡️ 2. Pemantauan Similarity Turnitin (`Turnitin-Similarity-Ledger.md`)

Sebelum diserahkan ke dewan penguji atau diunggah ke portal pendaftaran, naskah wajib memenuhi batasan keras etika akademik ITERA:
* **Maksimum Similarity Total:** $\le \mathbf{25\%}$ (setelah eksklusi daftar pustaka).
* **Maksimum Kutipan Langsung:** $\le \mathbf{10\%}$ dari keseluruhan naskah.

Buka berkas `06-Naskah-Draft/Turnitin-Similarity-Ledger.md` setiap kali Anda melakukan pengecekan Turnitin:
1. Catat tanggal pengecekan dan nama berkas.
2. Catat skor similarity index per bab.
3. Jika skor $> 25\%$, catat kalimat yang terkena *highlight* dan tuliskan hasil parafrasa akademisnya di tabel penanganan (*remediation log*).

---

## 🖨️ 3. Mentransfer Draf Markdown ke Berkas LaTeX UNESCO

Setelah naskah di draf Markdown disetujui:
1. Salin teks per bab ke dalam folder `proposal-penelitian-andryano-123140205/chapters/`:
   * Bab I $\rightarrow$ `chapters/chapter-1.tex`
   * Bab II $\rightarrow$ `chapters/chapter-2.tex`
   * Bab III $\rightarrow$ `chapters/chapter-3.tex`
2. Jalankan kompilasi multi-pass XeLaTeX melalui terminal PowerShell:
   ```powershell
   cd "proposal-penelitian-andryano-123140205"
   xelatex -interaction=nonstopmode thesis.tex
   bibtex thesis
   xelatex -interaction=nonstopmode thesis.tex
   xelatex -interaction=nonstopmode thesis.tex
   ```
3. Dokumen resmi **`thesis.pdf`** siap dicetak bolak-balik dengan geometri UNESCO presisi, penomoran halaman ganjil/genap sesuai Tabel 8.4 Pedoman TA, dan bebas galat!
