---
title: Panduan & Indeks Riwayat Prompt Harian
tags:
  - prompt-history
  - index
  - logs
---

# 💬 Indeks & Direktori Riwayat Prompt Harian

Folder ini berfungsi sebagai **rekam jejak (audit trail) dan arsip prompt harian** antara pengguna (Andryano) dan AI Agent (Antigravity/Gemini) selama pengerjaan Tugas Akhir.

---

## 🎯 Tujuan & Manfaat

1. **Akuntabilitas Akademik:** Memenuhi panduan etika penggunaan AI ITERA (Tingkat 2 & 3) dengan mendokumentasikan setiap instruksi dan arahan manusia secara transparan.
2. **Konteks Persisten:** Memudahkan penelusuran kembali keputusan teknis, instruksi formula matematika, arsitektur sistem, dan evaluasi sebelumnya.
3. **Tracking Produktivitas:** Melihat pola interaksi, kendala harian, dan evolusi ide riset.

---

## 📑 Format Standar Entri Prompt

Setiap file harian dinamai dengan format: `Prompt-YYYY-MM-DD.md`.
Template tersedia di: [[Template-Prompt-Log]]

Struktur setiap entri memuat:
- **Timestamp:** Waktu prompt dikirim.
- **Teks Prompt Pengguna:** Kutipan instruksi asli.
- **Konteks & Kebutuhan:** Maksud dan target dari instruksi.
- **Aksi & Solusi Agen:** Langkah penyelesaian dan rekomendasi teknis.
- **Artefak / Berkas Terkait:** Tautan ke naskah, kode, atau konfigurasi yang disentuh.

---

## 🗂️ Daftar Riwayat Prompt Terkini

```dataview
TABLE file.mtime AS "Terakhir Diperbarui", total_prompts AS "Total Prompt", tags AS "Tags"
FROM "08-Prompt-History"
WHERE file.name != "README"
SORT file.name DESC
```
