---tier: "Tier 1: Core Foundation & Baseline Acuan"

title: "Bedah Kritis: Mood-Dynamic Playlist Interpolating a Path of Emotions Using a KNN Algorithm"
author: "Shaurya Gaur & Patrick Donnelly"
year: 2023
citekey: "gaur2023mooddynamic"
venue: "Oregon State University Honors Baccalaureate Thesis / ISMIR Workshop"
quartile: "Undergraduate Honors Thesis (Foundational Baseline)"
dataset: "DMDD (Deezer Mood Detection Dataset) — 18.644 lagu"
metode: "Linear Waypoint Interpolation + Two-Stage KNN (Coordinate & Acoustic Distance)"
gap_utama: "Static-point matching mengabaikan dinamika internal emosi lagu, memicu The Boundary Jump Problem pada sambungan outro-intro trek."
tags:
  - literatur
  - paper-review
  - baseline-primer
  - mood-arc
  - knn
  - dmdd
status: "audited"
aliases:
  - Gaur2023-Mood-Dynamic
  - Mood-Dynamic Playlist Gaur
---
# 📖 Bedah Kritis: Mood-Dynamic Playlist (Gaur & Donnelly, 2023)
## *Interpolating a Path of Emotions Using a KNN Algorithm*

> **Objek Bedah:** Naskah skripsi komputasi Oregon State University (117 KB text)  
> **Kedudukan dalam TA:** **Baseline Primer / Titik Pijak Utama** Replikasi & Peningkatan Model

---

## 🧭 Step 0: Metadata dan Konteks
* **Penulis & Afiliasi:** Shaurya Gaur (Honors Scholar) di bawah supervisi Dr. Patrick Donnelly, Sound, Music, and Creative Computing Lab, Oregon State University.
* **Venue & Tahun:** Oregon State University Honors Baccalaureate Thesis, dipresentasikan 22 Mei 2023. Merupakan formalisasi dari model Gaur & Donnelly (2020) di ISMIR Late Breaking Demo.
* **Tujuan Membaca:** Membedah kelemahan inheren arsitektur *Two-Stage KNN*, mereplikasi pipeline interpolasi waypoint emosi, dan merumuskan celah transisi kasar (*boundary jump*) yang akan kita selesaikan dengan *Dynamic Trajectory Alignment*.

---

## 📑 Step 1: Abstrak (Bedah 5 Komponen)
1. **Konteks & Masalah:** Layanan streaming kurasi playlist umumnya monoton pada satu mood statis. Pengguna membutuhkan perjalanan transisi emosional (*mood-arc*) antarlagu dari titik emosi awal ke akhir.
2. **Gap yang Diklaim:** Riset terdahulu hanya berfokus pada perpindahan genre atau playlist emosi homogen; belum ada algoritma interpolasi mood non-linier bertahap yang fleksibel.
3. **Pendekatan:** Interpolasi linier Euclidean pada bidang koordinat 2D Valence-Arousal (VA), diikuti pencarian lagu terdekat via KNN 2-tahap (Tahap 1: jarak koordinat emosi statis; Tahap 2: reranking jarak fitur akustik timbre/MFCC).
4. **Hasil Kuantitatif Konkret:**
   * Metrik kelancaran (*Smoothness* $\mathcal{S}$): Nilai rata-rata transisi $\mathcal{S} = 0.082$ vs *Random Shuffle* $\mathcal{S} = 0.341$ (penurunan jarak lompatan $pprox 76\%$).
   * Metrik keteraturan (*Evenness* $\mathcal{E}$): Standard deviasi interval $\mathcal{E} = 0.041$ vs Random $\mathcal{E} = 0.187$.
5. **Implikasi:** Algoritma KNN mampu memproduksi playlist bertransisi secara efisien secara komputasi ($O(N \log N)$ dengan KD-Tree).

---

## 🎯 Step 2: Pendahuluan (Problem Framing)
* **Definisi Masalah:** Masalah didefinisikan sangat operasional: Diberikan titik awal $P_{start} = (v_1, a_1)$, titik akhir $P_{end} = (v_k, a_k)$, dan panjang playlist $K$, bangkitkan deret lagu $L_1, L_2, \dots, L_K$ yang meminimalkan fluktuasi emosi antartrek bertetangga.
* **Motivasi Riil:** Aplikasi *mood regulation* (terapi musik, pengantar tidur dari gelisah ke rileks, atau musik olahraga dari pemanasan ke intensitas tinggi).
* **Gap Statement Asli Penulis:** *"While previous studies explored genre transitions, interpolating a smooth path through continuous emotion space using nearest neighbor search has not been systematically formalized."*

---

## 🔬 Step 3: Related Work & Taksonomi
Penulis mengelompokkan literatur menjadi:
1. *Single-mood playlist generation* (Content-based filtering tradisional).
2. *Genre transition graph-based methods* (Markov Chain lintas kategori diskrit).
3. *Emotion-aware MIR* (Model regresi emosi audio).
* **Citation Gap:** Penulis **tidak memperhitungkan** riset emosi musik dinamis deret waktu (seperti dataset DEAM Aljanaki 2017) dan hanya mengandalkan dataset DMDD (statis rata-rata per lagu).

---

## ⚙️ Step 4: Metodologi & Formulasi Matematis
* **Representasi Emosi:** Menggunakan koordinat skalar tunggal statis $(ar{v}_i, ar{a}_i) \in [-1, 1]^2$ per trek lagu.
* **Algoritma Dua Tahap (Two-Stage KNN):**
  1. **Interpolasi Waypoint Target:**
     $$ec{w}_t = ec{w}_1 + rac{t-1}{K-1}(ec{w}_K - ec{w}_1), \quad t \in \{1, 2, \dots, K\}$$
  2. **Tahap 1 (Retrieval Kandidat):** Mengambil $M$ tetangga terdekat di sekitar $ec{w}_t$ menggunakan KD-Tree pada jarak Euclidean:
     $$d_{VA}(L_i, ec{w}_t) = \sqrt{(v_i - w_{v,t})^2 + (a_i - w_{a,t})^2}$$
  3. **Tahap 2 (Reranking Fitur Akustik):** Dari $M$ kandidat, pilih lagu $L_t^*$ yang meminimalkan jarak fitur akustik timbre/MFCC terhadap lagu sebelumnya $L_{t-1}^*$:
     $$L_t^* = rg\min_{L_i \in 	ext{Kandidat}} \|\mathbf{f}(L_i) - \mathbf{f}(L_{t-1}^*)\|_2$$

---

## 🧪 Step 5: Setup Eksperimen & Leakage Audit
* **Dataset:** DMDD (*Deezer Mood Detection Dataset*) berisi 18.644 lagu (cuplikan 30 detik).
* **Audit Kebocoran Data (Leakage Audit):** Karena sifatnya *retrieval-based unsupervised*, tidak ada train/test split regresi. Namun, terdapat kelemahan: dataset DMDD hanya menyediakan **satu anotasi rata-rata statis** untuk keseluruhan 30 detik lagu.
* **Kekuatan Baseline:** Pembanding yang digunakan hanyalah *Random Shuffle* dan *Direct Metric Sort* (baseline yang relatif lemah / *naive baseline*).

---

## 📊 Step 6: Hasil & Temuan Kuantitatif
* **Tabel Hasil Utama:**
  * Interpolasi KNN menghasilkan reduksi metrik Smoothness $\mathcal{S}$ sebesar 76% dibanding pengacakan acak.
  * Evenness $\mathcal{E}$ membuktikan interval lompatan antar lagu terjaga konsisten tanpa fluktuasi liar.
* **Ablation Study:** Penulis menguji pengaruh nilai $M$ kandidat (dari $M=1$ hingga $M=20$). Ditemukan bahwa $M \ge 5$ memberikan trade-off terbaik antara kepatuhan emosi dan kontinuitas akustik.

---

## ⚠️ Step 7: Limitasi Tersembunyi & Red Flags
> [!WARNING]
> **Limitasi Struktural yang Tidak Dipecahkan Gaur (2023):**
> 1. **The Boundary Jump Problem:** Lagu diperlakukan sebagai titik statis tunggal. Faktanya, sebuah lagu memiliki outro (penutup) dan intro (pembuka). Jika outro lagu $A$ berada di $(v=0.8, a=0.9)$ tetapi intro lagu $B$ berada di $(v=0.2, a=0.2)$, transisi antarlagu akan terasa **sangat menyentak dan kasar (*jarring jump*)**, meskipun nilai rata-rata kedua lagu tampak berdekatan!
> 2. **Tidak Menggunakan Sifat Dinamis Deret Waktu:** Informasi fluktuasi per detik (seperti sampling 2 Hz pada DEAM) terbuang percuma.

---

## 💡 Step 8 & 9: Sintesis Pencapaian 3 Kalimat
1. **Fakta Terbukti:** Algoritma Two-Stage KNN terbukti secara matematis mampu menyusun deret lagu yang mengikuti garis lintasan waypoint emosi pada bidang 2D Valence-Arousal dengan kompleksitas komputasi rendah.
2. **Lompatan SOTA:** Berhasil mengotomatisasi transisi mood kontinu tanpa perlu membangun graf Markov manual berbasis aturan diskrit.
3. **Kegunaan Praktis:** Sangat aplikatif untuk modul rekomendasi playlist transisi emosi pada platform streaming musik.

---

## 🎯 Step 10: Research Gap Tiga Lapis
1. **Lapis 1 (Gap Klaim Penulis):** Penulis mengakui bahwa interpolasi linier belum tentu mencerminkan preferensi manusia yang non-linier dan membutuhkan pengujian subjektif pendengar.
2. **Lapis 2 (Gap Temuan Audit Kita):** Model Gaur gagal mengantisipasi dinamika internal emosi antarlagu, memicu *boundary jump problem* karena tidak menyelaraskan trajektori outro ke intro.
3. **Lapis 3 (Gap Sintesis Multi-Paper):** Belum ada riset yang mengawinkan arsitektur Two-Stage KNN Gaur dengan dataset emosi dinamis kontinu (DEAM 2 Hz) dan merancang reranking berbasis **Dynamic Trajectory Alignment** untuk meminimalkan lompatan batas trek.

> **Template Gap Statement Bab I & II:**  
> *"Meskipun model Two-Stage KNN Gaur & Donnelly (2023) terbukti mampu menginterpolasi lintasan waypoint emosi pada bidang 2D Valence-Arousal, pendekatan tersebut masih mengandalkan representasi titik skalar statis tunggal per lagu, sehingga mengabaikan dinamika temporal internal dan memicu Boundary Jump Problem saat pergantian trek musik."*

---

## 🚩 Radar Red Flags Audit
- [x] Baseline pembanding hanya Random Shuffle (*naive baseline*).
- [x] Dataset DMDD hanya memiliki label emosi statis rata-rata.
- [ ] Single run tanpa pengujian variasi seed (karena algoritma deterministik KNN).
- [x] Tidak ada evaluasi pendengaran subjektif (*Zero User Listening Study*).

---

## 🔗 Relevansi dengan Tugas Akhir ITERA
* **Bab I:** Menjadi acuan perumusan latar belakang dan kritik model terdahulu.
* **Bab II:** Menjadi subbab khusus *Model Acuan (Baseline)*.
* **Bab III & Kode:** Direplikasi pada modul `06-Log-Training-Baseline-Gaur.md` dan ditingkatkan pada modul usulan `Dynamic Trajectory Alignment`.
