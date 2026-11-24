---
title: "Tutorial 03: Review Paper & Matriks Sintesis Literatur Otomatis"
tags:
  - tutorial
  - literatur
  - dataview
  - zotero
  - matriks-sintesis
date: 2026-11-24
---

# 📚 Tutorial 03: Review Paper & Matriks Sintesis Literatur Otomatis

Pedoman Tugas Akhir ITERA mewajibkan minimal **15 referensi primer** dengan minimal **70% berasal dari 3 tahun terakhir**. Di vault ini, Anda tidak perlu lagi membuat tabel rangkuman literatur secara manual di Word atau Excel. Sistem telah menggunakan mesin **Dataview** yang otomatis membuat tabel perbandingan dari setiap catatan paper yang Anda tulis.

---

## 📝 1. Cara Menulis Review Paper Baru

Setiap kali Anda selesai membaca satu jurnal/artikel dari folder `referensi/`:

1. Buka folder: `04-Literatur-Review/Papers/`.
2. Buat file baru dengan format penamaan standar: `PenulisTahun-TopikSingkat.md`  
   *(Contoh: `Schweiger2025-Playlist-Coherence.md` atau `Wen2025-Dynamic-Arousal.md`)*.
3. Sisipkan cetakan baku review:
   * Tekan **`Ctrl + P`** di keyboard.
   * Ketik **`Insert template`** lalu tekan `Enter`.
   * Pilih **`Template-Paper-Review`**.

---

## 🏷️ 2. Mengisi Frontmatter YAML (Kunci Otomatisasi Dataview)

Di bagian paling atas catatan paper, terdapat blok metadata di antara tanda `---`:

```yaml
---
title: "The Impact of Playlist Characteristics on Coherence"
author: "Schweiger et al."
year: 2025
dataset: "Spotify Millions User Playlists"
metode: "Sequential Transition Coherence Analysis"
tags:
  - paper-review
  - playlist-coherence
  - spotify
---
```

> [!IMPORTANT]
> **Aturan Wajib:**
> Selalu pastikan tag **`- paper-review`**, nama **`author`**, tahun **`year`**, **`dataset`**, dan **`metode`** terisi dengan benar. Properti inilah yang dibaca oleh mesin Dataview untuk dimasukkan ke tabel master.

---

## 🔬 3. Struktur Isi Review Paper (Anti-Lupa Saat Sidang)

Template ini menyediakan 4 bagian krusial yang paling sering ditanyakan dosen penguji saat Seminar Proposal:

1. **Gagasan Utama & Masalah yang Diselesaikan:** Apa yang diteliti penulis paper tersebut?
2. **Dataset & Fitur yang Digunakan:** Apa nama datasetnya, berapa ukuran audionya, dan fitur apa yang diekstrak?
3. **Hasil Temuan Kunci (*Key Findings*):** Angka keberhasilan apa yang mereka capai?
4. **Kelemahan & Keterbatasan (*Research Gap*):** Apa kekurangan paper ini yang bisa diserang dan diperbaiki oleh Tugas Akhir Anda?

---

## 📊 4. Melihat Matriks Sintesis yang Ter-update Otomatis

Setelah Anda menyimpan catatan paper baru:
1. Buka berkas: **`04-Literatur-Review/Matriks-Sintesis.md`**.
2. Anda akan melihat tabel komparasi otomatis yang disusun oleh Dataview:

```dataview
TABLE author AS "Penulis", year AS "Tahun", dataset AS "Dataset", metode AS "Metode"
FROM #paper-review
SORT year DESC
```

3. Tanpa perlu mengetik satu baris tabel pun, paper baru Anda langsung muncul di posisi teratas (terurut dari tahun terbaru), lengkap dengan link yang bisa diklik menuju catatan lengkapnya!

---

## 📑 5. Menghubungkan ke `references.bib` di LaTeX

Jika paper tersebut dikutip dalam draf naskah Bab 1 atau Bab 2:
1. Pastikan entri BibTeX paper tersebut ada di file `proposal-penelitian-andryano-123140205/references.bib`.
2. Gunakan *citekey* yang konsisten saat menulis draf, misalnya `\cite{Schweiger2025}` atau `\cite{Gaur2020}`.
