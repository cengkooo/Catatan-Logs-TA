---
title: "Draf Naskah Bab 1: Pendahuluan (Skenario 2 - Dual Evaluation: Objektif & User Study)"
tags:
  - draft
  - skenario-2
  - bab1
  - pendahuluan
  - user-study
  - deam
  - unesco
status: "READY FOR COMPILATION"
date: 2026-11-24
---
	
# ✍️ Bab I Pendahuluan (Skenario 2: Dual Evaluation dengan User Listening Study)

*Pendekatan evaluasi ganda (*Dual Evaluation Framework*) yang memadukan metrik komputasional objektif di GPU dengan uji persepsi manusia (*Blind A/B Listening Test* pada klip transisi 30s, $N \ge 30$ responden).*

---

## 1.1 Latar Belakang

Perkembangan platform penyiaran musik digital (*music streaming services*) seperti Spotify, Apple Music, dan Deezer telah mengubah paradigma interaksi manusia dengan katalog audio berskala masif. Berdasarkan laporan industri dan studi sistem temu kembali informasi musik (*Music Information Retrieval* / MIR), lebih dari 60% waktu mendengarkan musik dihabiskan melalui kurasi daftar putar (*playlist*). Namun, mayoritas sistem rekomendasi konvensional masih mengandalkan pendekatan penyaringan kolaboratif (*collaborative filtering*) dan kemiripan fitur statis yang hanya mencocokkan preferensi historis pengguna secara independen per trek, tanpa mempertimbangkan kontinuitas alur emosional di sepanjang sesi mendengarkan.

Kebutuhan pendengar modern telah bergeser ke arah daftar putar berbasis konteks dan aktivitas (seperti belajar, berolahraga, meditasi, dan tidur), di mana perubahan suasana hati (*mood*) diharapkan mengikuti lintasan tertentu yang terkontrol (*mood arc*). Sebagai contoh, platform Deezer mengadopsi fitur *Flow Moods* (Bontempelli et al., 2022) untuk mengarahkan pendengar ke kondisi afektif tertentu. Penelitian Tomasi et al. (2023) menggunakan *reinforcement learning* serta studi empiris Schweiger et al. (2025) pada jutaan playlist kurasi manusia membuktikan bahwa koherensi sekuensial dan kehalusan transisi antartrek berturutan (*sequential transition coherence*) memiliki korelasi langsung terhadap retensi dan kenyamanan pendengar.

Gagasan perancangan playlist berbasis kurva emosi telah dirintis sejak prototipe MOODetector (Cardoso et al., 2011) dengan memetakan titik-titik lagu pada ruang afektif dua dimensi Valence-Arousal model sirkumpleks Russell (1980). Penelitian acuan terkini oleh Shaurya Gaur dan Donnelly (2020, 2024) mengusulkan algoritma pembangkitan mood-arc playlist dua tahap: tahap pertama menggunakan *K-Nearest Neighbors* (KNN) untuk menginterpolasi dan mengambil kandidat lagu di sekitar *waypoint* lintasan emosi, disusul tahap kedua berupa penyaringan berbasis kemiripan akustik. Model ini diuji pada dataset DMDD (Delbouys et al., 2018) dan menjadi acuan utama dalam evaluasi metrik kehalusan (*smoothness*) serta keseragaman (*evenness*) playlist.

Meskipun model Gaur dan Donnelly (2020) menunjukkan kinerja retrieval yang terarah, pendekatan tersebut menyimpan kelemahan struktural yang mendasar: **pencocokan titik statis (*static-point matching*)**. Pada dataset DMDD, setiap lagu direpresentasikan hanya oleh satu nilai rata-rata skalar Valence dan Arousal ($\bar{v}, \bar{a}$) untuk keseluruhan durasi audio. Representasi statis ini mengasumsikan secara keliru bahwa suasana hati lagu bersifat konstan dari awal hingga akhir. Faktanya, analisis empiris pada korpus benchmark DEAM (*Database for Emotion Analysis in Music*, Aljanaki et al., 2017) yang memuat anotasi dinamis 2 Hz pada 1.802 klip musik membuktikan bahwa **98,11% lagu mengalami pergeseran emosi internal yang signifikan** sepanjang durasinya.

Ketiadaan representasi dinamika internal ini melahirkan fenomena kegagalan perseptual yang kami definisikan sebagai **The Boundary Jump Problem**: suatu kondisi diskontinuitas emosi yang tajam ketika detik-detik akhir lagu $i$ (misalnya berkarakter tenang di kuadran IV) bersambung langsung dengan detik-detik awal lagu $i+1$ (yang berkarakter enerjik di kuadran I), meskipun kedua lagu tersebut memiliki nilai rata-rata statis yang identik. Akibatnya, playlist yang secara matematis tampak mulus pada level rata-rata trek, sebenarnya memicu sentakan emosi kasar (*boundary jump shock*) saat didengarkan secara berurutan.

Belum ada penelitian terdahulu yang menguji apakah mempertimbangkan trajektori dinamis mood internal lagu mampu menghasilkan transisi playlist mood-arc yang lebih koheren dan mulus dibandingkan pendekatan *static-point matching*, serta bagaimana dampak perbaikan matematis tersebut terhadap kenyamanan mendengar manusia secara langsung. Oleh karena itu, penelitian ini mengusulkan pengembangan pipeline pembangkitan mood-arc playlist dua tahap berbasis **Dynamic Mood Trajectory Alignment** pada korpus benchmark DEAM dengan kerangka evaluasi ganda: metrik komputasional objektif dan pengujian persepsi subjektif (*User Listening Study*).

---

## 1.2 Rumusan Masalah

Berdasarkan latar belakang di atas, rumusan masalah dalam penelitian ini adalah:
1. Bagaimana merancang dan mengimplementasikan pipeline pembangkitan *mood-arc playlist* dua tahap yang memadukan algoritma *K-Nearest Neighbors* (KNN) dengan mekanisme *Dynamic Mood Trajectory Alignment* pada dataset benchmark DEAM?
2. Bagaimana pengaruh integrasi vektor trajektori dinamis lagu terhadap peningkatan metrik kelancaran transisi (*Smoothness*) dan pemerataan lintasan (*Evenness*) playlist jika dibandingkan secara *head-to-head* dengan model acuan *static-point matching* Gaur dan Donnelly (2020)?
3. Seberapa besar magnitudo pergeseran emosi internal (*intra-song mood dynamics*) pada dataset DEAM, dan bagaimana kontribusinya dalam mereduksi penalti lompatan batas emosi (*Boundary Jump Cost*) antartrek berturutan?
4. Bagaimana korelasi antara metrik komputasional objektif dengan tingkat penerimaan perseptual pendengar (*perceived transition smoothness* dan *acoustic continuity*) yang diukur melalui pengujian kuesioner pengguna (*user listening study*) pada segmen transisi antarlagu?

---

## 1.3 Tujuan Penelitian

Tujuan yang hendak dicapai dalam penelitian ini adalah:
1. Merancang dan mengimplementasikan arsitektur pipeline dua tahap berbasis KNN candidate generator dan trajectory alignment reranker pada korpus DEAM (indikator keberhasilan: pipeline modular berbasis PyTorch yang dapat mengeksekusi batch query playlist di GPU).
2. Mengevaluasi dan membandingkan performa playlist yang dihasilkan terhadap model baseline Gaur dan Donnelly (2020) menggunakan metrik kuantitatif terstandarisasi *Smoothness Index* ($\mathcal{S}$) dan *Evenness Index* ($\mathcal{E}$) (indikator keberhasilan: reduksi nilai Smoothness Index $\ge 15\%$ tanpa mendegradasi Evenness secara signifikan).
3. Mengukur magnitudo pergeseran vektor Valence-Arousal internal lagu pada 1.802 trek DEAM serta menguji efektivitas penalti *Boundary Jump Cost* dalam mengeliminasi diskontinuitas transisi antarlagu berturutan.
4. Mengukur dan memvalidasi penerimaan perseptual pengguna melalui *user listening study* berskala laboratorium ($N \ge 30$) dengan metode *blind A/B testing* dan skala Likert 5 poin (indikator keberhasilan: skor Mean Opinion Score (MOS) kelancaran transisi model usulan lebih tinggi secara signifikan dibanding baseline dengan nilai $p < 0.05$ pada uji Wilcoxon Signed-Rank).

---

## 1.4 Batasan Penelitian

Ruang lingkup dan batasan dalam penelitian ini meliputi:
1. Dataset yang digunakan terbatas pada korpus benchmark audio terbuka DEAM (*Database for Emotion Analysis in Music*) yang terdiri atas 1.802 klip musik berdurasi 45 detik dengan anotasi emosi kontinu 2 Hz.
2. Sesuai protokol resmi DEAM, 15 detik pertama dari setiap klip audio diabaikan (*offset* 15.0 detik) karena merupakan segmen stabilisasi anotator manusia.
3. Model psikologi emosi yang digunakan merujuk pada representasi dua dimensi ortogonal kontinu Russell (1980), yaitu Valence dan Arousal dalam rentang dinormalisasi $[-1.0, +1.0]$.
4. Pengujian persepsi manusia (*user listening study*) dirancang sebagai validasi subjektif komparatif (*blind A/B testing*) pada skala laboratorium terbatas yang melibatkan minimal 30 responden pendengar aktif musik digital, dievaluasi menggunakan instrumen kuesioner skala Likert 5 poin pada klip sambungan transisi 30 detik dan diuji signifikansinya secara statistik.
5. Algoritma retrieval kandidat dibatasi pada *K-Nearest Neighbors* (KNN) deterministik guna menjamin transparansi analisis dan komparasi yang adil terhadap baseline Gaur dan Donnelly (2020).

---

## 1.5 Manfaat Penelitian

1. **Manfaat Teoretis (Keilmuan):** Memberikan kontribusi akademis pada ranah *Music Information Retrieval* (MIR) dan psikomusikologi mengenai pentingnya memodelkan konten audio sebagai trajektori dinamis kontinu, serta membuktikan keterkaitan empiris antara metrik kehalusan algoritmik dengan respon persepsi afektif manusia.
2. **Manfaat Praktis (Industri):** Menyediakan cetak biru arsitektur komputasional yang efisien dan tervalidasi secara perseptual untuk diadopsi oleh platform streaming musik digital guna menghasilkan kurasi playlist kontekstual yang mulus dan nyaman didengarkan.

---

## 1.6 Sistematika Penulisan

Sistematika penulisan laporan proposal Tugas Akhir ini disusun dalam lima bab utama: Bab I Pendahuluan, Bab II Tinjauan Pustaka, Bab III Metodologi (mencakup evaluasi komputasional dan protokol uji dengar manusia), Bab IV Hasil dan Pembahasan, dan Bab V Kesimpulan dan Saran.
