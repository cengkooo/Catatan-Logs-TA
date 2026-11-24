---
title: "Tutorial 05: Persiapan Bimbingan Dosen & Pemenuhan Syarat TASYS"
tags:
  - tutorial
  - bimbingan
  - tasys
  - sempro
  - administrasi
date: 2026-11-24
---

# 💬 Tutorial 05: Persiapan Bimbingan Dosen & Pemenuhan Syarat TASYS

Berdasarkan **Pedoman TA ITERA [1.2.0] Subbab 5.2**, mahasiswa wajib memenuhi syarat administratif dan mencatatkan minimal **4 kali bimbingan substansi yang disetujui pembimbing di portal TASYS** sebelum berkas pendaftaran Seminar Proposal dapat diproses oleh Program Studi.

Folder `03-Bimbingan/` dirancang untuk mengawal proses ini tanpa ada berkas yang tertinggal.

---

## 📋 1. Sebelum Bimbingan: Apa yang Wajib Disiapkan?

### Langkah 1: Buka Lembar Diskusi / Catatan Progres
* Jika Anda ingin mendiskusikan rencana pengujian kuesioner pengguna, buka berkas:  
  👉 **`03-Bimbingan/04-Lembar-Diskusi-Skenario-User-Study.md`**.
* Berkas ini adalah dokumen ringkas 1 halaman yang membandingkan Skenario 1 (Murni Komputasional), Skenario 2 (Uji Klip 30s), dan Skenario 3 (Playlist Utuh 15 Menit). Anda bisa langsung menunjukkan tabel perbandingannya di HP atau laptop kepada Pak Hafiz.

### Langkah 2: Cek Kesiapan Prasyarat Sempro
Buka berkas **`03-Bimbingan/03-Tracker-Prasyarat-Sempro.md`**:
- [x] Pastikan SKS $\ge 100$, IPK $\ge 2.00$, dan tidak ada nilai E.
- [ ] Pastikan Anda sudah mengantongi bukti hadir minimal **2 seminar proposal mahasiswa lain** (tanda tangan form fisik atau approval di TASYS).

---

## ✍️ 2. Saat Bimbingan: Mencatat Notulensi & Arahan Revisi

1. Buka berkas: **`03-Bimbingan/01-Notulensi-Bimbingan.md`**.
2. Tambahkan sesi pertemuan baru di bawah judul pertemuan terakhir:
   ```markdown
   ## Pertemuan #X — Tanggal: YYYY-MM-DD
   - **Media / Tempat:** Luring (Ruang Dosen) / Google Meet
   - **Materi yang Dibahas:** Review draf Bab 1–3 dan rencana User Listening Study.
   - **Poin Masukan & Arahan Pak Hafiz:**
     1. [Catat poin 1]
     2. [Catat poin 2]
   - **Action Items / PR Mahasiswa:**
     - [ ] Perbaiki batasan masalah sesuai Skenario 2
     - [ ] Siapkan 14 slide sempro alokasi 10 menit
   ```

---

## 🌐 3. Setelah Bimbingan: Rekonsiliasi Portal TASYS

Pedoman ITERA mewajibkan log bimbingan tercatat resmi di sistem informasi:
1. Segera buka portal akademik TASYS ITERA di browser.
2. Ajukan sesi bimbingan baru dengan menyalin ringkasan materi dan poin arahan yang sudah Anda catat di `Notulensi-Bimbingan.md`.
3. Informasikan secara sopan kepada Pak Hafiz untuk meminta persetujuan (*approval*) di akun dosen TASYS.
4. Tandai checklist pada tabel pertemuan di `Tracker-Prasyarat-Sempro.md`.

---

## 🛡️ 4. Menghadapi Pertanyaan Dosen Penguji (`Bank-Pertanyaan-Dosen.md`)

Sebelum maju Sempro, latih mental Anda dengan membaca **`03-Bimbingan/02-Bank-Pertanyaan-Dosen.md`** dan **`10-Slides/03-Speaker-Notes-Dan-Antisipasi-QnA.md`**. 

Di sana sudah disiapkan strategi jawaban berbasis data (*data-driven defense*) untuk 4 pertanyaan paling kritis penguji:
1. *Kenapa pakai DEAM bukan Spotify Web API?*
2. *Kenapa memilih algoritma KNN bukan Transformer / Deep RL?*
3. *Kenapa durasi audio 45 detik cukup merepresentasikan lagu utuh?*
4. *Bagaimana membuktikan secara objektif bahwa playlist lebih mulus?*
