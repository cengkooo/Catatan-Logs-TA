---
title: "Pusat Catatan Pembelajaran & Tech Stack (11-Catatan-Belajar)"
tags:
  - index
  - knowledge-base
  - overview
  - second-brain
---

# 📚 Pusat Catatan Pembelajaran & Tech Stack

Selamat datang di **Second Brain & Knowledge Base** Tugas Akhir! Folder ini didedikasikan untuk mendokumentasikan pemahaman konseptual mandiri, pendalaman materi dari [[Matriks-Sintesis|04-Literatur-Review]], serta panduan teknis rekayasa kode dari [[05-Eksperimen]].

> [!TIP]
> **Alur Kerja Pembuatan Catatan Baru:**
> 1. Gunakan `Template-Catatan-Konsep.md` untuk mencatat teori/domain MIR ke subfolder `01-Konsep-Teori/`.
> 2. Gunakan `Template-Catatan-Techstack.md` untuk menyimpan sintaks, snippet, dan cheatsheet ke subfolder `02-Tech-Stack/`.
> 3. Tuliskan ide kreatif, formulasi hipotesis baru, atau persiapan bimbingan/sidang di subfolder `03-Sintesis-dan-Ide/`.
> 4. Seluruh tabel di bawah ini akan terisi dan terbarui secara **otomatis melalui Dataview**.

---

## 🧠 1. Konsep & Teori Musik / MIR (`01-Konsep-Teori`)

```dataview
TABLE topik AS "Topik Utama", rujukan_paper AS "Rujukan Paper", status AS "Status Pemahaman", file.mtime AS "Terakhir Diupdate"
FROM "11-Catatan-Belajar/01-Konsep-Teori" or #note/konsep
SORT file.mtime DESC
```

---

## ⚙️ 2. Tech Stack & Engineering Guides (`02-Tech-Stack`)

```dataview
TABLE stack AS "Teknologi", versi AS "Versi", file.mtime AS "Terakhir Diupdate"
FROM "11-Catatan-Belajar/02-Tech-Stack" or #note/techstack
SORT file.name ASC
```

---

## 💡 3. Sintesis & Ide Kreatif (`03-Sintesis-dan-Ide`)

```dataview
TABLE file.folder AS "Sub-Folder", file.mtime AS "Terakhir Diupdate"
FROM "11-Catatan-Belajar/03-Sintesis-dan-Ide"
SORT file.mtime DESC
```

---

## 🔗 Navigasi Cepat
- 🏠 **Dashboard Utama:** [[Master-Dashboard]]
- 📖 **Paper Asli:** [[Matriks-Sintesis|04-Literatur-Review/Papers]]
- 🔬 **Eksperimen & Data:** [[05-Eksperimen]] | [[Dataset-DEAM]]
- 📝 **Draf Naskah Bab:** [[06-Naskah-Draft/Bab-2-Tinjauan-Pustaka]] | [[06-Naskah-Draft/Bab-3-Metodologi]]
