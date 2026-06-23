# WS-13: Data Preprocessing

## Pertemuan 13 — Preprocessing & Persiapan Data untuk Analisis

**Nama:** Ahmad Sultoni
**NIM:** 240202850
**Mata Kuliah:** Research & Teknologi Informasi (RTI)

---

# PREPROCESSING LOG

### Dataset

Dataset hasil pengujian performa sistem e-learning menggunakan empat skenario:

1. Baseline
2. Cache Only
3. Load Balancing Only
4. Hybrid (Load Balancing + Redis Cache)

### Jumlah Data Awal

20 records (4 skenario × 5 run)

---

# Latihan 1 — Cleaning Plan

## Hasil Pemeriksaan Data

| Masalah                | Jumlah Kasus | Penanganan                    | Justifikasi                        |
| ---------------------- | ------------ | ----------------------------- | ---------------------------------- |
| Missing Value          | 0            | Tidak ada tindakan            | Seluruh log berhasil terekam       |
| Duplikat Data          | 0            | Tidak ada tindakan            | Setiap Run ID unik                 |
| Error Format Timestamp | 1            | Standardisasi format ISO-8601 | Menjaga konsistensi pencatatan     |
| Error Penulisan Satuan | 1            | Diseragamkan menjadi ms       | Menghindari kesalahan interpretasi |

---

## Ringkasan Cleaning

Jumlah data sebelum cleaning:

```text
20 records
```

Jumlah data setelah cleaning:

```text
20 records
```

Persentase data yang hilang/berubah:

```text
0%
```

Tidak ada record yang dihapus karena seluruh data masih valid dan dapat digunakan untuk analisis.

---

# Latihan 2 — Normalisasi Decision

## Evaluasi Variabel

| Variabel      | Range Asli      | Distribusi     | Outlier?            | Metode Normalisasi | Alasan                                                             |
| ------------- | --------------- | -------------- | ------------------- | ------------------ | ------------------------------------------------------------------ |
| Response Time | 118–245 ms      | Relatif Normal | Ada sedikit outlier | Tidak perlu        | Analisis dilakukan pada nilai aktual agar interpretasi tetap mudah |
| Throughput    | 420–850 req/sec | Relatif Normal | Tidak               | Tidak perlu        | Perbandingan antar skenario lebih mudah menggunakan nilai asli     |
| Error Rate    | 0–100 %         | Sangat kecil   | Tidak               | Tidak perlu        | Sudah dalam satuan yang jelas                                      |
| CPU Usage     | 0–100 %         | Normal         | Tidak               | Tidak perlu        | Tidak digunakan sebagai metrik utama                               |
| Memory Usage  | 0–100 %         | Normal         | Tidak               | Tidak perlu        | Hanya sebagai metadata                                             |

---

## Keputusan Normalisasi

☑ Tidak

### Justifikasi

Penelitian ini bertujuan membandingkan performa sistem menggunakan metrik yang memiliki satuan fisik yang jelas (milisecond dan request per second). Oleh karena itu penggunaan nilai asli lebih mudah diinterpretasikan dibandingkan hasil transformasi atau normalisasi.

Selain itu, analisis yang dilakukan berupa perbandingan rata-rata, standar deviasi, dan uji statistik antar-skenario sehingga tidak membutuhkan metode berbasis distance yang umumnya memerlukan normalisasi.

---

## Leakage Check

* [x] Tidak ada parameter normalisasi yang dihitung dari seluruh dataset
* [x] Tidak ada informasi hasil pengujian yang bocor ke proses preprocessing
* [x] Seluruh preprocessing dilakukan sebelum analisis statistik

---

# Latihan 3 — Preprocessing Report

## PREPROCESSING SUMMARY

### 1. Dataset

Hasil eksperimen performa sistem e-learning dengan empat skenario arsitektur.

---

### 2. Data Awal

```text
20 records
8 features
```

Fitur yang digunakan:

* Run ID
* Timestamp
* Scenario
* Seed
* Response Time
* Throughput
* CPU Usage
* Memory Usage

---

### 3. Cleaning

#### Missing Values

```text
0 kasus
```

Metode:

```text
Tidak diperlukan
```

---

#### Duplikat

```text
0 kasus
```

Tindakan:

```text
Tidak diperlukan
```

---

#### Error Format

```text
2 kasus
```

Tindakan:

* Standardisasi format timestamp
* Penyamaan satuan waktu ke milisecond

---

### 4. Transformation

Transformasi yang dilakukan:

```text
Standarisasi format timestamp
Standarisasi satuan metrik performa
```

Alasan:

```text
Menjaga konsistensi data antar-run
```

---

### 5. Normalisasi

```text
Tidak dilakukan
```

Alasan:

```text
Nilai asli lebih representatif dan mudah diinterpretasikan untuk penelitian performa sistem.
```

---

### 6. Data Akhir

```text
20 records
8 features
```

Tidak ada data yang dihapus selama proses preprocessing.

---

### 7. Leakage Check

☑ Lulus

Hasil pemeriksaan menunjukkan tidak terdapat data leakage karena:

* Tidak ada proses normalisasi berbasis seluruh dataset.
* Tidak ada pencampuran data antar-skenario.
* Tidak ada modifikasi nilai metrik utama.

---

# Refleksi

Dalam praktik sebelumnya, normalisasi sering dianggap sebagai langkah wajib karena umum digunakan pada penelitian machine learning. Namun setelah mempelajari preprocessing lebih mendalam, normalisasi seharusnya dilakukan hanya ketika memang diperlukan oleh metode analisis yang digunakan.

Risiko over-preprocessing adalah hilangnya karakteristik asli data sehingga hasil analisis menjadi kurang representatif. Selain itu, transformasi yang tidak diperlukan dapat menyulitkan interpretasi hasil dan berpotensi menghasilkan kesimpulan yang berbeda dari kondisi nyata sistem yang diteliti.

Oleh karena itu setiap langkah preprocessing harus memiliki alasan yang jelas, terdokumentasi, dan dapat direproduksi oleh peneliti lain.

---

# Kesimpulan

Proses preprocessing menunjukkan bahwa dataset penelitian memiliki kualitas yang baik dengan tingkat kelengkapan 100%, tanpa missing value maupun duplikasi data. Hanya dilakukan standardisasi format untuk menjaga konsistensi pencatatan. Karena metrik utama berupa Response Time dan Throughput masih mudah diinterpretasikan dalam bentuk aslinya, normalisasi tidak dilakukan. Dataset hasil preprocessing dinyatakan siap digunakan pada tahap analisis statistik dan pengujian hipotesis.
