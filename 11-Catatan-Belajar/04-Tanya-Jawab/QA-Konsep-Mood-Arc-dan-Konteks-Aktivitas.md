---
title: "Fungsi Konteks Aktivitas vs. Mood Dasar pada Mood-Arc Playlist"
tags:
  - note/tanya-jawab
  - learning-qa
  - mood-arc
  - bab-1
topik: "Konsep Mood-Arc dan Konteks Aktivitas"
status: "berkembang"
rujukan_paper:
  - "[[01-Gaur2023-Mood-Dynamic]]"
  - "[[06-Bontempelli2022-Flow-Moods-Deezer]]"
  - "[[03-Russell1980-Circumplex-Model]]"
created: 2026-11-28
updated: 2026-11-28
---

# 💬 Fungsi Konteks Aktivitas vs. Mood Dasar pada Mood-Arc Playlist

- **Topik:** `Konsep Mood-Arc dan Konteks Aktivitas`
- **Status Pemahaman:** `berkembang`

---

## ❓ Pertanyaan #1
> Pada `chapter-1.tex` tertulis: *"Kebutuhan pendengar modern bergeser ke arah daftar putar berbasis konteks dan aktivitas, seperti belajar, berolahraga, meditasi, dan tidur, yang menuntut perubahan suasana hati (mood) mengikuti lintasan afektif terkontrol."* Mengapa yang disebut adalah konteks aktivitas, bukan mood seperti senang, bahagia, sedih, atau marah seperti pada paper yang membahas mood? Apa fungsi aktivitas tersebut?

### 💡 Jawaban

Penyebutan **aktivitas** (belajar, berolahraga, meditasi, tidur) bukanlah pengganti konsep *mood* (senang, sedih, marah, tenang), melainkan **lapisan konteks dunia nyata** yang menjelaskan *mengapa* manusia membutuhkan **perubahan mood secara bertahap (*mood arc*)**, bukan sekadar satu *mood* diam.

#### 1. Mengapa Aktivitas, Bukan Sekadar "Senang / Sedih / Marah"?
- **Mood tunggal bersifat statis:** Jika pendengar hanya ingin mendengarkan lagu "sedih" atau "senang", sistem cukup mengambil lagu dari satu kuadran emosi yang sama dari awal sampai akhir (seperti 6 tombol kategori statis pada *Deezer Flow Moods*).
- **Aktivitas memiliki fase waktu (*awal -> tengah -> akhir*) yang menuntut *mood regulation*:** Sebagaimana dijelaskan dalam motivasi riil paper acuan **Gaur & Donnelly (2023)**, kebutuhan utama *mood-arc* adalah *mood regulation*:
  - **Tidur:** Pendengar sering memulai dalam kondisi masih terjaga/gelisah (*Arousal* tinggi), lalu membutuhkan musik yang menurunkan ketegangan secara bertahap menuju kondisi rileks/mengantuk (*Arousal* rendah, Kuadran 4) agar transisi tidurnya alami.
  - **Berolahraga:** Dimulai dari pemanasan (*Arousal* sedang), naik ke puncak intensitas latihan (*Arousal* tinggi, Kuadran 1), lalu turun saat pendinginan (*cool-down*).
  - **Belajar / Meditasi:** Berpindah dari pikiran yang ramai atau terdistraksi menuju kondisi fokus dan tenang yang stabil.

#### 2. Hubungan Aktivitas dengan Ruang Emosi (Senang, Sedih, Marah, Tenang)
Keduanya bekerja di lapisan yang berbeda namun saling terhubung:
- **Lapisan Konteks Pengguna (Bab 1 - Urgensi Dunia Nyata):** Aktivitas (*belajar, olahraga, tidur*) menjelaskan **untuk apa** *mood arc* dipakai oleh pengguna aplikasi streaming.
- **Lapisan Representasi Matematis (Bab 2 & Bab 3):** Di dalam sistem, aktivitas tersebut diterjemahkan menjadi titik awal dan titik tujuan ($\mathbf{p}_{\text{start}} \to \mathbf{p}_{\text{target}}$) pada **Model Sirkumpleks Russell (Valence-Arousal)** yang memang memetakan emosi dasar seperti *Marah/Tegang* (Q2), *Senang/Bersemangat* (Q1), *Sedih* (Q3), dan *Tenang/Damai* (Q4).

#### 3. Tiga Fungsi Utama Kalimat Aktivitas di Bab 1 Proposal
1. **Membedakan sistem Anda dari rekomendasi berbasis riwayat biasa:** Seperti dicatat pada paper **Bontempelli et al. (2022)** (Deezer *Flow Moods*), rekomendasi yang hanya mengandalkan riwayat dengar sering gagal ketika konteks pengguna berubah (misalnya pengguna sedang ingin *fokus belajar*, tetapi sistem malah memutar lagu *pesta* karena kemarin ia sering memutar lagu pesta).
2. **Menjustifikasi bentuk "lintasan" (*arc*), bukan titik tunggal:** Aktivitas membuktikan bahwa emosi pendengar dalam satu sesi mendengarkan bersifat dinamis dan terarah dari satu titik emosi ke titik emosi lain.
3. **Menjawab pertanyaan penguji soal manfaat praktis:** Tanpa contoh aktivitas nyata, topik *Valence-Arousal trajectory* bisa terdengar terlalu abstrak. Dengan adanya contoh tidur, olahraga, dan belajar, dosen penguji langsung menangkap dampak praktisnya di industri streaming.

---

## ❓ Pertanyaan #2
> Memangnya algoritma yang saya ajukan bisa menebak fase waktu (awal, tengah, akhir) aktivitas pengguna?

### 💡 Jawaban

**Tidak.** Algoritma yang Anda ajukan **tidak menebak** aktivitas pengguna ataupun fase waktunya secara otomatis (bukan *activity recognition* atau deteksi konteks *real-time*).

#### 1. Bagaimana Fase Awal, Tengah, dan Akhir Sebenarnya Bekerja di Algoritma Anda?
Berdasarkan [[Bab-3-Metodologi]] (Subbab 3.3.1), alurnya bersifat **terkendali dari input (*user-defined / query-driven*)**, bukan tebakan otomatis:
1. **Input Ditetapkan di Awal:** Titik emosi awal ($\mathbf{p}_{\text{start}}$), titik emosi target akhir ($\mathbf{p}_{\text{target}}$), dan jumlah lagu ($M$) diberikan sebagai parameter masukan (misalnya pada pengujian rute dari Q3 ke Q1 atau Q1 ke Q4).
2. **Pembagian Fase via Interpolasi Linier (Persamaan 3.3):** Sistem membagi garis lurus antara $\mathbf{p}_{\text{start}}$ dan $\mathbf{p}_{\text{target}}$ menjadi $M$ titik acuan (*waypoints*):
   $$\mathbf{w}_j = \mathbf{p}_{\text{start}} + \frac{j-1}{M-1} \cdot (\mathbf{p}_{\text{target}} - \mathbf{p}_{\text{start}}), \quad \forall j \in \{1, 2, \dots, M\}$$
   - **Awal** = $\mathbf{w}_1 = \mathbf{p}_{\text{start}}$
   - **Tengah** = $\mathbf{w}_j$ di antara keduanya
   - **Akhir** = $\mathbf{w}_M = \mathbf{p}_{\text{target}}$
3. **Peran KNN & Reranker:**
   - **KNN (Tahap 1)** mengambil $K=20$ lagu terdekat di sekitar masing-masing $\mathbf{w}_j$.
   - **Trajectory Alignment Reranker (Tahap 2)** memilih lagu yang arah perubahan emosi internalnya ($\vec{\mathbf{t}}_k$) searah dengan vektor perpindahan antar-waypoint ($\vec{\mathbf{u}}_j = \mathbf{w}_j - \mathbf{w}_{j-1}$) dan memiliki sambungan *outro-to-intro* paling halus ($\mathcal{BJC}$ minimal).

#### 2. Cara Menjawab Jika Ditanya Dosen Penguji di Sempro
Jika penguji bertanya *"Apakah sistemmu bisa mendeteksi otomatis user sedang olahraga atau mau tidur?"*, jawab secara jujur dan tegas:
> *"Tidak, Pak/Bu. Deteksi aktivitas pengguna di luar batasan penelitian kami (sebagaimana tercantum di Batasan Penelitian bahwa sistem tidak membahas skenario real-time atau pengembangan aplikasi). Konteks aktivitas di Bab 1 berfungsi sebagai skenario kebutuhan nyata yang melatarbelakangi mengapa pengguna menginginkan playlist berbentuk lintasan dari satu titik emosi ke titik emosi lain. Algoritma kami bekerja setelah titik awal ($\mathbf{p}_{\text{start}}$) dan titik akhir ($\mathbf{p}_{\text{target}}$) ditentukan, untuk memastikan transisi antartrek di sepanjang lintasan tersebut berjalan mulus tanpa boundary jump."*

---

---

## ❓ Pertanyaan #3
> Sebenarnya nanti *generated playlist* itu output playlist yang seperti apa?

### 💡 Jawaban

Karena Tugas Akhir Anda **tidak membangun aplikasi pemutar musik** atau sistem *real-time* (sesuai Batasan Penelitian pada `chapter-1.tex`), output *generated playlist* bukan berupa antarmuka aplikasi seperti Spotify, melainkan **dua bentuk keluaran konkret**:

#### 1. Output Data Terstruktur (untuk Evaluasi Komputasional 540 Batch Run)
Secara inti, output dari algoritma Anda adalah **daftar urutan terurut berisi $M$ buah ID lagu DEAM** (dengan variasi panjang $M \in \{5, 10, 15\}$ lagu pada `Bab-3-Metodologi.md`) beserta rekam jejak koordinat dan metriknya, misalnya dalam struktur list/JSON/CSV:
- **Urutan Lagu:** `[Track_1, Track_2, Track_3, ..., Track_M]` (contoh: 5 lagu berurutan dari rute Q3 ke Q1).
- **Atribut per Trek:** `song_id`, koordinat *intro* $\mathbf{p}_{\text{intro}}$, koordinat *outro* $\mathbf{p}_{\text{outro}}$, vektor trajektori $\vec{\mathbf{t}}_k$, dan jarak *Boundary Jump Cost* ($\mathcal{BJC}$) terhadap lagu sebelumnya.
- **Skor Evaluasi Playlist:** *Smoothness Index* ($\mathcal{S}$), *Evenness Index* ($\mathcal{E}$), dan *Cumulative Boundary Jump Cost* ($\mathcal{CBJC}$).

Pada eksperimen benchmark, sistem menghasilkan **540 sekuens playlist** seperti itu untuk membandingkan Model Usulan, Baseline Gaur, dan Random.

#### 2. Output Audio Sambungan (untuk Uji Dengar Manusia / Blind A/B Listening Test)
Karena dataset DEAM memiliki berkas audio MP3 asli, daftar urutan lagu tersebut juga bisa dirender menjadi berkas audio untuk didengarkan:
- Untuk **pengujian persepsi manusia** pada `chapter-1.tex` (minimal 30 responden), pasangan lagu berturutan $(L_i, L_{i+1})$ dari *generated playlist* dipotong dan disambung menjadi **klip transisi berdurasi 30 detik**: **15 detik *outro* lagu ke-$i$ disambung langsung dengan 15 detik *intro* lagu ke-$(i+1)$**.
- Tujuannya agar responden bisa menilai langsung secara audio (*perceived smoothness*, *acoustic continuity*, *emotional naturalness*) tanpa harus mendengarkan seluruh playlist 15 lagu penuh yang melelahkan telinga.

---

### 📚 Referensi
- [[01-Gaur2023-Mood-Dynamic]] — Motivasi *mood regulation* (terapi musik, pengantar tidur dari gelisah ke rileks, dan musik olahraga dari pemanasan ke intensitas tinggi).
- [[06-Bontempelli2022-Flow-Moods-Deezer]] — Contoh kegagalan personalisasi historis saat konteks aktivitas pengguna berubah (*belajar* vs. *pesta*).
- [[03-Russell1980-Circumplex-Model]] — Pemetaan emosi dasar (senang, marah, sedih, tenang) ke koordinat kontinu *Valence-Arousal*.
- `proposal-penelitian-andryano-123140205/chapters/chapter-1.tex` (Latar Belakang, baris 7–9).

### 🔗 Catatan Terkait
- [[00-Index-Catatan]]
- [[Model-Emosi-Sirkumpleks-Russell-1980]]
- [[QA-Algoritma-Rekomendasi-Platform-Streaming]]
