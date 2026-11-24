---
title: "Sprint 3: Bab 3 & Metodologi (RE-BASELINE 16 NOV)"
status: "IN PROGRESS"
tags:
  - sprint
  - bab3
  - metodologi
window: "2026-11-19 → 2026-11-22"
deadline: 2026-11-22
---

# 🛠️ Sprint 3: Bab 3 & Desain Metodologi

> [!danger] Re-baseline 16 Nov 2026 — task lama tidak realistis
> Kalender lama menaruh T-10 (metrik) pada 16 Nov, padahal Bab 1–2 belum ada. Sekarang urutannya benar: diagram → metrik → PoC.
> Rencana induk: [[EMERGENCY-SEMPRO]] · Sheet: tab **🚨 EMERGENCY 16-25 NOV**

- **Status:** `IN PROGRESS`
- **Window:** 19 – 22 Nov 2026
- **Output:** Draf Bab 3 (`chapters/bab3.tex`) + Bukti PoC pipeline
- **Dashboard:** [[Master-Dashboard]] | [[Roadmap-Sempro]]

---

## 🎯 Target & Checklist Kerja

- [ ] **T-09** Diagram alir pipeline Mood-Arc Playlist → *Kam 19 Nov 17:30–19:30 + 19:30–21:45*
  - Output: diagram 2-tahap (ekstraksi trajectory → filtering alignment) + caption
- [ ] **T-10** Metrik evaluasi (Smoothness, Evenness, RMSE, Pearson) → *Jum 20 Nov 10:00–11:00*
  - Output: rumus smoothness & evenness playlist + RMSE/Pearson trajectory + justifikasi
- [ ] **T-11** Validasi pipeline ekstraksi trajectory & smoke test inference → *Sab 21 Nov 16:30–18:30, 19:30–21:45 & Min 22 Nov 07:00–11:00*
  - Output: log eksekusi tanpa error + screenshot + tabel validasi shape vektor trajectory
- [ ] **T-12** Kirim naskah utuh v1 & minta izin sempro → *Jum 20 Nov 19:30–21:45* 🚨 **HARD DEADLINE 22:00**
  - Output: PDF naskah v1 terkirim ke Pak Hafiz

---

## ⏱️ Alokasi Waktu (dari Google Calendar)

| Blok | Agenda | Output |
| :--- | :--- | :--- |
| Kam 17:30–19:30 | T-09 draft diagram | draft draw.io |
| Kam 19:30–21:45 | T-09 finalisasi | diagram v1 + caption |
| Jum 10:00–11:00 | T-10 metrik | rumus + justifikasi |
| Jum 19:30–21:45 | **T-12 KIRIM v1** | PDF terkirim ≤ 22:00 |
| Sab 16:30–18:30 | T-11 cluster | log tanpa error |
| Sab 19:30–21:45 | T-11 dummy inference | screenshot + log |
| Min 07:00–11:00 | T-11 dokumentasi PoC | tabel shape + narasi |

---

## 📝 Catatan Perkembangan Sprint
- **PoC tetap penuh** (keputusan 16 Nov): T-07 dan T-11 tidak dipotong, digeser ke weekend 21–22 Nov.
- Bila GPU tidak tersedia: jalankan CPU + subsample, tetap laporkan sebagai *proof of pipeline*, bukan hasil performa.
- Diagram harus konsisten dengan notasi di [[Kamus-Notasi-Glosarium]].
