# WS-01: Distorsi & Paradigma

> **Bab 1 — Research Mindset in IT**

---

## Ringkasan Materi

### Research Trust Model

Pengetahuan ilmiah tidak muncul langsung dari kenyataan. Ia melewati **6 tahap transformasi** yang masing-masing rawan distorsi:

```
Reality → Data → Processing → Analysis → Inference → Knowledge
```

Etika mencegah distorsi yang disengaja (fabrikasi, cherry-picking). Validitas mendeteksi distorsi yang tidak disengaja (confounding variable, sampling bias).

### Tiga Jenis Validitas

| Jenis | Pertanyaan | Contoh Ancaman |
|-------|-----------|----------------|
| **Internal Validity** | Apakah hubungan kausal benar ada? | Confounding variable |
| **External Validity** | Apakah bisa digeneralisasi? | Dataset terlalu homogen |
| **Construct Validity** | Apakah mengukur hal yang benar? | Metrik tidak sesuai klaim |

### Paradigma Riset

Mata kuliah ini menggunakan pendekatan **Positivist** (fenomena TI bisa diukur objektif melalui eksperimen terkontrol) diperkuat **Design Science Research** (artefak dibuat sebagai instrumen pengujian hipotesis, bukan tujuan akhir).

### Mode Berpikir Peneliti

**Curious** (mempertanyakan fenomena) → **Critical** (mengevaluasi klaim berdasarkan bukti) → **Systematic** (merancang investigasi terstruktur dan reproducible).

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan | Membuat sistem yang bekerja | Menghasilkan pengetahuan yang valid |
| Pertanyaan khas | "Bagaimana membuatnya jalan?" | "Apakah klaim ini benar?" |
| Ukuran sukses | Sistem berfungsi, client puas | Hipotesis terjawab, temuan tervalidasi |
| Kegagalan | Harus dihindari | Harus dilaporkan (negative result = kontribusi) |

### Istilah Penting

- **Research Mindset** — Pola pikir yang menuntut bukti dan mempertanyakan asumsi
- **Research Ethics** — Prinsip perilaku: kejujuran, objektivitas, keterbukaan, akuntabilitas
- **HARKing** — Hypothesizing After Results are Known — merumuskan hipotesis setelah melihat data
- **Falsifiability** — Hipotesis harus bisa dibuktikan salah

---

## Template A.1 — Research Mindset Self-Assessment

```
Nama Peneliti    : ____________________
Tanggal          : ____________________

1. Ketika membaca klaim "metode X 95% akurat":
   - Pertanyaan pertama saya: ____________________
   - Data yang dibutuhkan untuk verifikasi: ____________________

2. Posisi paradigma:
   - Pendekatan: [ ] Positivis  [ ] Interpretivis  [ ] Design Science  [ ] Mixed
   - Alasan: ____________________

3. Identifikasi distorsi:
   - Asumsi tersembunyi: ____________________
   - Sumber bias potensial: ____________________
   - Langkah mitigasi: ____________________

4. Komitmen etika:
   - Data yang tidak akan dimanipulasi: ____________________
   - Batasan yang diakui sejak awal: ____________________
```

---

## Latihan 1 — Identifikasi Distorsi

Pilih satu paper riset di bidang TI yang mengklaim "metode X meningkatkan performa." Telusuri setiap tahap Research Trust Model.

**Paper yang dipilih:**
> Judul: _______________________________________________
> Penulis (Tahun): ______________________________________

| Tahap | Apa yang Dilakukan | Potensi Distorsi |
|-------|-------------------|-----------------|
| Reality → Data | *Contoh: Kumpulkan log server 30 hari* | *Contoh: Hanya ambil jam sibuk* |
| Data → Processing | | |
| Processing → Analysis | | |
| Analysis → Inference | | |
| Inference → Knowledge | | |

**Distorsi paling besar di tahap:** ________________________

**Dua distorsi spesifik yang teridentifikasi:**
1. ___________________________________________________
2. ___________________________________________________

---

## Latihan 2 — Analisis Kasus Etika

Skenario: Seorang peneliti menemukan bahwa jika 3 data point outlier dihapus, hasil eksperimennya menjadi signifikan. Dengan outlier, hasilnya tidak signifikan.

| Perspektif | Analisis |
|------------|---------|
| Kejujuran ilmiah | *Contoh: Laporkan kedua versi (dengan dan tanpa outlier)* |
| Transparansi | |
| Peer review | |

**Keputusan akhir dan justifikasi:**
> ___________________________________________________

---

## Latihan 3 — Posisi Paradigma

**Topik riset:** ________________________________________

| Kriteria | Positivis | Interpretivis | Design Science |
|----------|-----------|---------------|----------------|
| Kesesuaian dengan topik (1–5) | *Contoh: 4* | *Contoh: 2* | *Contoh: 5* |
| Jenis data yang dikumpulkan | | | |
| Limitasi paradigma | | | |

**Paradigma yang dipilih:** _____________________________
**Alasan:** ____________________________________________

---

## Refleksi

> Sebelum membaca materi ini, apakah pernah mempertanyakan klaim "95% akurat"? Setelah memahami rantai distorsi, pertanyaan apa yang sekarang akan diajukan saat membaca paper?

**Jawaban:**
> ___________________________________________________
> ___________________________________________________


# WS-01: Distorsi & Paradigma

## Bab 1 — Research Mindset in IT

**Nama** : Ahmad Sultoni
**NIM** : 240202850
**Mata Kuliah** : Research & Teknologi Informasi (RTI)
**Tanggal** : 12 April 2026

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


