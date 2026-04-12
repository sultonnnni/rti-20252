# WS-01: Distorsi & Paradigma

## Bab 1 — Research Mindset in IT

**Nama** : Ahmad Sultoni
**NIM** : 240202850
**Mata Kuliah** : Research & Teknologi Informasi (RTI)
**Tanggal** : 8 April 2026

---

# Template A.1 — Research Mindset Self-Assessment

## 1. Ketika membaca klaim "metode X 95% akurat"

**Pertanyaan pertama saya:**
Saya akan mempertanyakan bagaimana metode tersebut diuji dan apakah dataset yang digunakan cukup mewakili kondisi nyata.

**Data yang dibutuhkan untuk verifikasi:**
Saya membutuhkan informasi mengenai dataset yang digunakan, jumlah data, metode pengujian, serta metrik evaluasi yang digunakan dalam penelitian tersebut.

---

## 2. Posisi paradigma

Pendekatan:

* [x] Positivis
* [ ] Interpretivis
* [x] Design Science
* [ ] Mixed

**Alasan:**
Penelitian di bidang teknologi informasi umumnya menggunakan eksperimen yang dapat diukur secara objektif. Selain itu, sering juga dibuat sistem atau model untuk menguji hipotesis, sehingga pendekatan positivis dan design science lebih sesuai.

---

## 3. Identifikasi distorsi

**Asumsi tersembunyi:**
Data yang digunakan dianggap sudah mewakili kondisi sebenarnya.

**Sumber bias potensial:**
Dataset yang digunakan terlalu terbatas atau hanya berasal dari satu sumber.

**Langkah mitigasi:**
Menggunakan dataset yang lebih beragam serta melakukan pengujian ulang pada data yang berbeda.

---

## 4. Komitmen etika

**Data yang tidak akan dimanipulasi:**
Hasil eksperimen dan nilai akurasi sistem.

**Batasan yang diakui sejak awal:**
Dataset yang digunakan terbatas dan waktu penelitian yang tidak terlalu panjang.

---

# Latihan 1 — Identifikasi Distorsi

**Paper yang dipilih**

**Judul:**
Machine Learning Based Network Intrusion Detection System

**Penulis (Tahun):**
Ahmad et al. (2022)

| Tahap                 | Apa yang Dilakukan                                 | Potensi Distorsi                     |
| --------------------- | -------------------------------------------------- | ------------------------------------ |
| Reality → Data        | Mengambil dataset jaringan dari sumber publik      | Dataset tidak mewakili kondisi nyata |
| Data → Processing     | Membersihkan data dan menghapus data tidak lengkap | Penghapusan data mempengaruhi hasil  |
| Processing → Analysis | Menggunakan algoritma machine learning             | Parameter model tidak dijelaskan     |
| Analysis → Inference  | Menghasilkan akurasi tinggi                        | Kemungkinan overfitting              |
| Inference → Knowledge | Menyimpulkan metode terbaik                        | Tidak diuji pada dataset lain        |

**Distorsi paling besar di tahap:**
Data → Processing

**Dua distorsi spesifik yang teridentifikasi:**

1. Penghapusan data tanpa penjelasan jelas
2. Dataset tidak cukup beragam

---

# Latihan 2 — Analisis Kasus Etika

Skenario:
Seorang peneliti menemukan bahwa jika 3 data point outlier dihapus, hasil eksperimennya menjadi signifikan.

| Perspektif       | Analisis                                                     |
| ---------------- | ------------------------------------------------------------ |
| Kejujuran ilmiah | Peneliti sebaiknya melaporkan hasil dengan dan tanpa outlier |
| Transparansi     | Peneliti perlu menjelaskan alasan menghapus outlier          |
| Peer review      | Reviewer kemungkinan meminta analisis tambahan               |

**Keputusan akhir dan justifikasi:**

Peneliti sebaiknya tidak langsung menghapus data outlier. Hasil dengan dan tanpa outlier perlu dilaporkan agar penelitian tetap transparan dan dapat dipertanggungjawabkan secara ilmiah.

---

# Latihan 3 — Posisi Paradigma

**Topik riset:**
Analisis Akurasi Algoritma Machine Learning untuk Deteksi Spam Email

| Kriteria                      | Positivis                      | Interpretivis     | Design Science               |
| ----------------------------- | ------------------------------ | ----------------- | ---------------------------- |
| Kesesuaian dengan topik (1–5) | 5                              | 2                 | 4                            |
| Jenis data yang dikumpulkan   | Data numerik                   | Pendapat pengguna | Dataset email                |
| Limitasi paradigma            | Kurang melihat faktor pengguna | Subjektif         | Membutuhkan waktu lebih lama |

**Paradigma yang dipilih:**
Positivis dan Design Science

**Alasan:**
Penelitian membutuhkan eksperimen dan pengujian sistem agar hasil dapat diukur secara objektif.

---

# Refleksi

Sebelum membaca materi ini, saya biasanya langsung percaya jika melihat klaim seperti "95% akurat". Saya jarang mempertanyakan bagaimana hasil tersebut diperoleh.

Setelah memahami materi tentang distorsi dalam penelitian, saya menjadi lebih kritis. Sekarang saya akan mempertanyakan ukuran dataset, metode pengujian, serta apakah hasil tersebut dapat diterapkan pada kondisi yang berbeda.


