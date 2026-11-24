---
title: "Tutorial 02: Otomatisasi Pencadangan GitHub pada Setiap Perubahan (CRUD)"
tags:
  - tutorial
  - git
  - github
  - auto-backup
  - backup-workflow
date: 2026-11-24
---

# 🔄 Tutorial 02: Otomatisasi Pencadangan GitHub pada Setiap Perubahan (CRUD)

> [!tip] 💡 Jawaban Cepat (TL;DR): "Tekan Tombol Apa atau Biarin Aja? Emang Gak Berat?"
> 1. **Apakah harus tekan tombol?** $\rightarrow$ **Biarin aja! 100% Otomatis.** Anda cukup mengetik seperti biasa. Setiap kali Anda berhenti mengetik selama 15 detik, sistem di latar belakang akan otomatis meng-commit dan mem-push catatan ke GitHub.
> 2. **Apakah bakal bikin laptop berat/lag?** $\rightarrow$ **Sama sekali TIDAK!** Git hanya memproses file teks Markdown kecil (2–10 KB) di latar belakang (*background*). Konsumsi CPU saat Anda mengetik adalah **0%** (berkat debounce), dan file audio berat sudah diblokir oleh `.gitignore`.

Kehilangan catatan penelitian Tugas Akhir akibat harddisk rusak, laptop bermasalah, atau salah hapus adalah mimpi buruk mahasiswa. Vault ini telah dilengkapi sistem pencadangan otomatis multi-lapis (*multi-tier auto-backup*) langsung ke repositori GitHub pribadi Anda.

---

## ⚡ 1. Cara Kerja Otomatis di Dalam Obsidian (Native CRUD Triggers)

Anda **tidak perlu** membuka terminal Git atau mengetik perintah `git add` dan `git commit` secara manual setiap kali mengedit catatan. 

Plugin `obsidian-shellcommands` telah memantau empat aksi siklus hidup dokumen (**CRUD**):
1. **Create (`file-created`):** Terpicu saat Anda membuat catatan baru.
2. **Read/Update (`file-modified`):** Terpicu saat Anda mengetik, menghapus paragraf, atau mengedit naskah.
3. **Delete (`file-deleted`):** Terpicu saat Anda membuang catatan ke tempat sampah.
4. **Rename (`file-renamed`):** Terpicu saat Anda mengubah judul catatan atau memindahkannya ke folder lain.

### ⏱️ Mengapa Ada Jeda Waktu (Debounce 15 Detik)?
Bayangkan jika Anda sedang mengetik 1 paragraf (100 huruf). Jika Git bekerja pada setiap ketukan tuts keyboard, repositori Anda akan dipenuhi oleh 100 commit yang mengotori riwayat versi!

Oleh karena itu, sistem menerapkan **Debounce 15 Detik**:
* Saat Anda mulai mengetik, sistem mencatat adanya perubahan.
* Sistem akan menunggu hingga Anda **berhenti mengetik selama 15 detik**.
* Setelah 15 detik hening, sistem langsung menjalankan skrip `sync_vault_now.ps1` untuk meng-stage semua perubahan, membuat commit dengan cap waktu, dan mem-push ke GitHub.
* Notifikasi hijau akan muncul di pojok kanan bawah Obsidian: *"Berhasil sinkronisasi vault ke GitHub!"*.

---

## ⌨️ 2. Pemicu Cadangan Manual Instan (Force Backup)

Jika Anda baru saja menulis bagian yang sangat krusial dan ingin memastikan data langsung terkirim ke GitHub saat itu juga tanpa menunggu 15 detik:

1. Di dalam Obsidian, tekan tombol pintas: **`Ctrl + P`**.
2. Ketik kata kunci: **`Git: Backup`**.
3. Pilih perintah: **`Git: Backup Vault ke GitHub Sekarang`** lalu tekan `Enter`.
4. Sistem akan langsung memproses sinkronisasi dalam hitungan detik.

---

## 🖥️ 3. Background Watcher Eksternal (Saat Mengedit Lewat VS Code / Notepad)

Jika suatu saat Anda membuka repositori ini lewat VS Code atau AI coding assistant (bukan di dalam antarmuka Obsidian), pemicu internal Obsidian tentu tidak aktif. 

Untuk situasi ini, jalankan background file watcher mandiri via PowerShell:
1. Buka PowerShell di folder Tugas Akhir.
2. Jalankan perintah:
   ```powershell
   powershell -ExecutionPolicy Bypass -File "scripts\watch_vault_git_sync.ps1"
   ```
3. Script ini akan terus berjalan di latar belakang, memantau setiap folder di `Catatan-Memori-Logs`, dan otomatis melakukan commit & push dengan debouncing yang sama (15 detik).
4. Tekan `Ctrl + C` jika ingin menghentikan pemantauan.

---

## 🔗 4. Langkah Menghubungkan ke GitHub Pribadi Anda (Cukup 1 Kali)

Vault lokal Anda sudah siap sebagai repositori Git lokal dengan commit awal yang bersih. Untuk menghubungkannya ke akun GitHub Anda:

### Langkah A: Buat Repositori Baru di GitHub
1. Buka browser, masuk ke akun [GitHub](https://github.com).
2. Klik tombol **New Repository**.
3. Beri nama repositori, misalnya: `tugas-akhir-vault-catatan` atau `Catatan-Memori-Logs`.
4. **Sangat Disarankan:** Pilih opsi **Private** (agar catatan internal TA Anda tidak diakses publik sebelum sidang).
5. **Jangan centang** "Add a README file" atau ".gitignore" (karena kita sudah punya keduanya di lokal).
6. Klik **Create repository**, lalu salin URL repositorinya (misal: `https://github.com/UsernameAnda/Catatan-Memori-Logs.git`).

### Langkah B: Daftarkan Remote di Terminal Lokal
Buka PowerShell, lalu jalankan dua perintah ini:
```powershell
cd "D:\Kuliah\Semester 7\Tugas Akhir\Proposal Tugas Akhir\Catatan-Memori\Catatan-Memori-Logs"
git remote add origin https://github.com/<UsernameAnda>/<NamaRepoAnda>.git
git push -u origin master
```

Selesai! Mulai detik ini, setiap kata yang Anda tulis di Obsidian akan dicadangkan secara otomatis dan abadi di cloud GitHub Anda.

---

## 🛡️ 5. Apa yang Terjadi Jika Sedang Tidak Ada Koneksi Internet (Offline)?

Jangan khawatir! Jika laptop Anda sedang tidak terhubung ke WiFi atau internet sedang putus:
* Git akan tetap meng-commit catatan Anda secara **lokal di laptop**. Seluruh riwayat perubahan Anda 100% aman tersimpan di folder `.git`.
* Skrip akan menampilkan peringatan bahwa push ditunda karena offline.
* Begitu laptop Anda kembali terhubung ke internet dan terjadi perubahan berikutnya, seluruh tumpukan commit lokal akan otomatis terdorong (*pushed*) ke GitHub tanpa ada data yang tercecer.
