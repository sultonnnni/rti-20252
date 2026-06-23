# WS-11: Data Validation & Integrity

## Pertemuan 11 — Validasi Data & Integritas

**Nama:** Ahmad Sultoni
**NIM:** 240202850
**Mata Kuliah:** Research & Teknologi Informasi (RTI)

---

# Latihan 1 — Completeness Check

Verifikasi dilakukan terhadap seluruh hasil eksperimen yang telah direncanakan pada WS-10.

| Skenario            | Run Direncanakan | Run Tercatat | Missing | Alasan |
| ------------------- | ---------------- | ------------ | ------- | ------ |
| Baseline            | 5                | 5            | 0       | —      |
| Cache Only          | 5                | 5            | 0       | —      |
| Load Balancing Only | 5                | 5            | 0       | —      |
| Hybrid (LB + Cache) | 5                | 5            | 0       | —      |

### Ringkasan

* Total expected : 20 run
* Total actual : 20 run
* Missing : 0 run

### Keputusan untuk Data Missing

Tidak terdapat data yang hilang. Seluruh run yang direncanakan berhasil dieksekusi dan menghasilkan file log yang lengkap. Oleh karena itu tidak diperlukan proses imputasi maupun pengulangan eksperimen.

---

# Latihan 2 — Anomaly Investigation

Pengujian dilakukan menggunakan metrik utama Average Response Time (ms) pada skenario Hybrid.

## Dataset Sampel

| Run | Response Time (ms) |
| --- | ------------------ |
| 1   | 118                |
| 2   | 121                |
| 3   | 119                |
| 4   | 135                |
| 5   | 120                |

### Perhitungan IQR

Data terurut:

```text
118, 119, 120, 121, 135
```

* Q1 = 119
* Q3 = 121
* IQR = 2

Batas bawah:

```text
Q1 − 1.5 × IQR
= 119 − 3
= 116
```

Batas atas:

```text
Q3 + 1.5 × IQR
= 121 + 3
= 124
```

### Hasil Deteksi

* Batas bawah = 116
* Batas atas = 124
* Outlier terdeteksi = 135 ms (Run 4)

---

## Investigasi Outlier

| Outlier | Nilai  | Kemungkinan Penyebab                                                                  | Keputusan                                                                   |
| ------- | ------ | ------------------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| Run 4   | 135 ms | Lonjakan penggunaan CPU host akibat proses latar belakang saat eksperimen berlangsung | Tetap disimpan dan didokumentasikan sebagai anomali, tidak langsung dihapus |

### Hasil Investigasi

Nilai 135 ms berada di luar rentang distribusi normal hasil eksperimen. Setelah dilakukan pemeriksaan log Docker dan monitoring Grafana, ditemukan adanya peningkatan penggunaan CPU pada host selama periode pengujian tersebut.

Karena penyebabnya dapat dijelaskan secara teknis dan data masih valid, run tersebut tidak dihapus. Data akan tetap dicantumkan pada analisis dengan dokumentasi anomali yang jelas.

---

# Latihan 3 — Validation Report

## 1. Completeness

100% data berhasil terkumpul.

```text
20 dari 20 run tersedia
```

---

## 2. Format

☑ Konsisten

Seluruh hasil eksperimen menggunakan format CSV dan JSON dengan struktur field yang sama:

```text
Run_ID
Timestamp
Scenario
Seed
Response_Time
Throughput
Error_Rate
CPU_Usage
Memory_Usage
```

---

## 3. Range Check

Pemeriksaan dilakukan terhadap seluruh metrik.

| Metrik        | Range Valid | Hasil |
| ------------- | ----------- | ----- |
| Response Time | > 0 ms      | Valid |
| Throughput    | > 0 req/sec | Valid |
| Error Rate    | 0–100%      | Valid |
| CPU Usage     | 0–100%      | Valid |
| Memory Usage  | 0–100%      | Valid |

### Anomali Ditemukan

* Satu outlier pada Response Time sebesar 135 ms.
* Tidak ditemukan nilai negatif atau nilai di luar batas logis.

---

## 4. Logic Check

☑ Parameter sesuai plan

Validasi dilakukan dengan membandingkan log eksekusi terhadap Execution Plan pada WS-10.

Hasil pemeriksaan:

* Jumlah concurrent users = 200
* Durasi pengujian = 10 menit
* Dataset = 10.000 record
* Konfigurasi Nginx dan Redis sesuai skenario
* Seed sesuai daftar yang telah ditentukan

Tidak ditemukan pencampuran parameter antara kelompok kontrol dan treatment.

---

# Data Validation Checklist

## Completeness

* [x] Semua skenario tercakup
* [x] Jumlah run sesuai rencana
* [x] Tidak ada file output hilang

Missing: 0 dari 20 data points

---

## Format Consistency

* [x] Semua file menggunakan format yang sama
* [x] Header konsisten
* [x] Tipe data konsisten

---

## Range & Logic

* [x] Nilai berada dalam rentang masuk akal
* [x] Tidak ada waktu negatif
* [x] Tidak ada metrik di luar range

Anomali ditemukan:

```text
Response Time = 135 ms pada Run 4
```

---

## Cross Validation

* [x] Run identik menghasilkan nilai yang mendekati
* [x] Trend performa sesuai teori

Urutan performa yang diperoleh:

```text
Hybrid
   ↓
Load Balancing + Cache

Load Balancing Only
   ↓

Cache Only
   ↓

Baseline
```

Hasil ini konsisten dengan hipotesis penelitian pada WS-05.

---

# Keputusan

☑ Data siap untuk analisis statistik

Tidak diperlukan cleaning tambahan maupun re-run eksperimen karena seluruh data telah memenuhi aspek:

* Accuracy
* Consistency
* Completeness
* Validity

---

# Refleksi

Data yang benar belum tentu merupakan data yang dipercaya. Data dapat terlihat benar secara kasat mata, tetapi masih mungkin mengandung kesalahan pencatatan, data hilang, inkonsistensi format, atau anomali yang belum terdeteksi.

Sebaliknya, data yang dipercaya adalah data yang telah melalui proses validasi formal sehingga kualitas, konsistensi, dan kesesuaiannya dengan desain eksperimen dapat dibuktikan.

Proses validasi tetap diperlukan meskipun data dikumpulkan secara otomatis karena sistem logging juga dapat mengalami kesalahan konfigurasi, bug perangkat lunak, atau kehilangan data selama proses pengumpulan. Dengan validasi formal, peneliti memiliki dasar yang kuat untuk menyatakan bahwa data layak digunakan dalam analisis dan penarikan kesimpulan ilmiah.

### Kesimpulan

Dataset penelitian telah memenuhi prinsip integritas data karena seluruh data lengkap, konsisten, berada dalam rentang logis, serta sesuai dengan desain eksperimen yang telah direncanakan. Oleh karena itu dataset dinyatakan siap digunakan pada tahap analisis statistik berikutnya.
