---
title: "Lembar Konsultasi Pembimbing: 3 Skenario Pengujian User Listening Study"
tags:
  - bimbingan
  - user-study
  - skenario
  - kuesioner
  - evaluasi
date: 2026-11-24
mahasiswa: "Andryano (123140205)"
pembimbing: "Hafiz Budi Firmansyah, S.Kom., M.Sc."
---

# 📑 Lembar Konsultasi Pembimbing: 3 Skenario Pengujian Kuesioner Pengguna (*User Listening Study*)

**Topik Tugas Akhir:**  
*Mood-Arc Playlist Generation Berbasis Dynamic Mood Trajectory (Dataset DEAM, KNN & Trajectory Alignment)*

Yth. Bapak **Hafiz Budi Firmansyah, S.Kom., M.Sc.**,  
Menindaklanjuti arahan Bapak mengenai rencana pengujian kuesioner ke pendengar (*User Listening Study*) untuk menguji apakah playlist yang dihasilkan model benar-benar mulus dan sesuai mood manusia, berikut saya susun **3 alternatif skenario pengujian komparatif** untuk didiskusikan:

---

## 📊 Matriks Perbandingan 3 Alternatif Pengujian

| Parameter Evaluasi | Skenario 1: Murni Komputasional Objektif (Baseline Awal) | Skenario 2: Uji Klip Sambungan Transisi (30s) — ⭐ *Rekomendasi* | Skenario 3: Uji Playlist Utuh (Full Experience) |
| :--- | :--- | :--- | :--- |
| **Fokus yang Diuji** | Penurunan matematis Smoothness Index ($\mathcal{S}$) dan Evenness ($\mathcal{E}$) di GPU. | Kehalusan momen pergantian lagu (*The Boundary Jump Problem*). | Keseluruhan rute emosi dari lagu 1 sampai lagu 5 di sepanjang playlist. |
| **Bentuk Stimulus Audio** | Murni komputasi tensor PyTorch (tanpa audio ke manusia). | **Potongan sambungan 30 detik** (15s akhir lagu A + 15s awal lagu B). | **Playlist utuh** (5 lagu $\times$ 45 detik = 3,75 menit per playlist). |
| **Metode Pengujian** | Simulasi batch 540 playlist di Python. | **Blind A/B Listening Test** (Versi X vs Versi Y acak tanpa label algoritma). | **Blind A/B Listening Test** mendengarkan playlist penuh secara berurutan. |
| **Jumlah Responden** | 0 responden. | **$N = 30$ responden** (memenuhi *Central Limit Theorem*). | **$N = 30$ responden**. |
| **Waktu per Responden** | 0 menit. | **Efisien (± 5–7 menit)** untuk 4 pasang transisi. | **Lama (± 15–20 menit)**, rentan kelelahan dengar (*listener fatigue*). |
| **Risiko Ilmiah / Bias** | Bebas bias manusia, tapi tidak mengukur persepsi telinga. | **Sangat Rendah.** Responden fokus 100% pada sambungan transisi. | **Tinggi.** Nilai transisi rentan bias oleh selera genre musik atau vokal. |
| **Analisis Statistik** | Rata-rata & standar deviasi metrik $\mathcal{S}$ & $\mathcal{E}$. | **Wilcoxon Signed-Rank Test** ($p < 0.05$) + Korelasi Spearman metrik $\mathcal{S}$ vs Skor Manusia. | **Wilcoxon Signed-Rank Test** + ANOVA pengaruh genre. |
| **Timeline Pengerjaan** | TA 1 (Sempro) selesai. | **Metodologi di Bab 3 Proposal (TA 1)**; pengambilan data 30 orang saat **TA 2**. | **Metodologi di Bab 3 Proposal (TA 1)**; pengambilan data 30 orang saat **TA 2**. |

---

## 💡 Usulan Skenario Terbaik: Skenario 2 (Uji Klip Sambungan 30 Detik)

### Mengapa Skenario 2 Paling Kuat & Realistis?
1. **Tepat Sasaran Membuktikan Novelty:** Inti inovasi penelitian ini adalah mengatasi sentakan pergantian trek (*The Boundary Jump Problem*). Mendengarkan potongan sambungan 30 detik (15s outro Lagu A + 15s intro Lagu B) adalah cara paling tajam untuk menguji apakah telinga manusia merasa "kaget" atau merasa "mulus".
2. **Responden Tidak Lelah (*Zero Listener Fatigue*):** Responden hanya butuh waktu 6 menit untuk mengevaluasi 4 variasi transisi (misal: Tenang $\rightarrow$ Ceria, Sedih $\rightarrow$ Bersemangat). Kualitas data kuesioner jauh lebih objektif karena responden tidak bosan.
3. **Kombinasi Dual Evaluation yang Elegan:** Kita bisa membuktikan korelasi kuantitatif-kualitatif: *"Ketika Smoothness Index $\mathcal{S}$ algoritma turun $\ge 15\%$, skor kehalusan persepsi manusia terbukti meningkat secara signifikan secara statistik ($p < 0.05$)*".

### Contoh 3 Butir Pertanyaan Kuesioner (Skala Likert 1–5):
1. **Kehalusan Pergantian (*Perceived Smoothness*):**  
   *"Seberapa mulus pergantian antarlagu yang Anda dengarkan pada titik transisi?"*  
   (1 = Sangat kasar/menyentak $\longleftrightarrow$ 5 = Sangat mulus/alami)
2. **Kenyamanan Akustik (*Acoustic Continuity*):**  
   *"Seberapa nyaman kesinambungan energi dan tempo saat lagu berganti?"*  
   (1 = Sangat terputus $\longleftrightarrow$ 5 = Sangat berkesinambungan)
3. **Pilihan Preferensi Langsung (*Direct Preference*):**  
   *"Di antara Versi X dan Versi Y, sambungan mana yang terdengar lebih menyenangkan untuk playlist perjalanan suasana hati?"*  
   (Pilihan biner: [ ] Versi X | [ ] Versi Y)

---

## ❓ Poin Konsultasi yang Dimohonkan Arahan Bapak:
1. Apakah Bapak menyetujui penerapan **Skenario 2 (Uji Sambungan Transisi 30s)** sebagai bagian dari evaluasi penelitian?
2. Apakah Bapak sepakat bahwa pada naskah Proposal Sempro (TA 1) kita fokus mematangkan **desain metodologi & instrumen kuesionernya di Bab 3**, sedangkan penyebaran kuesioner ke 30 responden dan analisis datanya dieksekusi pada tahap **TA 2** sebelum Sidang Akhir?
