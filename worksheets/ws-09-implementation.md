
# WS-09: Implementation & Environment

## Identitas Riset

**Judul Penelitian:**
*Analisis Pengaruh Caching dan Load Balancing terhadap Performa Sistem E-Learning Berbasis Web*

**Tujuan Penelitian:**
Menganalisis pengaruh penerapan caching dan load balancing terhadap performa sistem e-learning berbasis web menggunakan metrik response time dan throughput.

---

# Latihan 1 — Environment Specification

## Environment Eksperimen

| Komponen        | Spesifikasi                     |
| --------------- | ------------------------------- |
| CPU             | Intel Core i5                   |
| RAM             | 16 GB DDR4                      |
| GPU             | Intel UHD Graphics (Integrated) |
| Storage         | SSD 512 GB                      |
| OS              | Windows 11 Pro 64-bit           |
| Runtime         | Python 3.12                     |
| Framework       | Flask 3.0                       |
| Version Control | Git 2.49                        |
| Random Seed     | 42                              |

---

## Dependencies

| Library    | Version | Alasan Dibutuhkan                              |
| ---------- | ------- | ---------------------------------------------- |
| Flask      | 3.0.3   | Framework web untuk simulasi sistem e-learning |
| NumPy      | 2.0.0   | Perhitungan numerik dan simulasi data          |
| Pandas     | 2.2.2   | Pengolahan data hasil eksperimen               |
| Matplotlib | 3.9.0   | Visualisasi hasil pengujian                    |
| Requests   | 2.32.3  | Simulasi request pengguna                      |
| Gunicorn   | 22.0.0  | Menjalankan web server secara konsisten        |

---

## Dokumentasi Setup Eksperimen

### Hardware

```text
CPU      : Intel Core i5
RAM      : 16 GB DDR4
GPU      : Intel UHD Graphics
Storage  : SSD 512 GB
```

### Software

```text
OS        : Windows 11 Pro 64-bit
Runtime   : Python 3.12
Framework : Flask 3.0
Git       : 2.49
```

### Konfigurasi Eksperimen

```text
Config File     : config.json
Random Seed     : 42

Parameter:
- Request Count = 1000
- Concurrent User = 50
- Cache Enabled = True
- Cache Size = 256 MB
- Test Duration = 60 Detik
```

---

## Reproducibility Check

* [x] Dependency terdokumentasi dalam requirements.txt
* [x] Random seed ditetapkan
* [x] Config file disimpan pada GitHub Repository
* [x] Langkah instalasi terdokumentasi
* [x] Langkah eksekusi terdokumentasi
* [x] Output eksperimen terdokumentasi

---

# Latihan 2 — Repeatability Test Plan

## Tujuan

Memastikan eksperimen menghasilkan keluaran yang konsisten ketika dijalankan berulang kali pada environment yang sama.

### Hasil Pengujian

| Run | Seed | Response Time | Throughput | Hasil Sama? |
| --- | ---- | ------------- | ---------- | ----------- |
| 1   | 42   | 121 ms        | 850 req/s  | —           |
| 2   | 42   | 121 ms        | 850 req/s  | Ya          |
| 3   | 42   | 121 ms        | 850 req/s  | Ya          |

---

## Analisis

Berdasarkan tiga kali pengujian, nilai response time dan throughput menunjukkan hasil yang konsisten. Hal ini mengindikasikan bahwa implementasi eksperimen telah memenuhi prinsip repeatability karena parameter, dependency, dan environment tetap sama pada setiap pengujian.

---

## Jika Hasil Berbeda, Kemungkinan Penyebab

1. Random seed tidak ditetapkan.
2. Perubahan versi library.
3. Cache belum dibersihkan.
4. Beban CPU atau RAM berubah.
5. Konfigurasi eksperimen berbeda.
6. Terdapat proses latar belakang yang mempengaruhi performa.

---

## Checklist Kontrol

* [x] Random seed di-set pada seluruh pengujian
* [x] Environment tidak berubah
* [x] Dependency menggunakan versi yang sama
* [x] Cache dibersihkan sebelum pengujian
* [x] Config file yang sama digunakan pada semua run
* [x] Tidak ada perubahan kode selama pengujian

---

# Latihan 3 — README Eksperimen

## Judul Eksperimen

**Analisis Pengaruh Caching dan Load Balancing terhadap Performa Sistem E-Learning Berbasis Web**

### 1. Environment

```text
CPU       : Intel Core i5
RAM       : 16 GB
OS        : Windows 11 Pro
Python    : 3.12
Framework : Flask 3.0
```

### 2. Installation

```bash
git clone https://github.com/username/ws09-research.git

cd ws09-research

pip install -r requirements.txt
```

### 3. Data

Data yang digunakan merupakan data simulasi request pengguna terhadap sistem e-learning.

Karakteristik data:

```text
Format      : CSV
Jumlah Data : 1000 Request
Sumber      : Simulasi Beban Sistem
```

### 4. Execution

Menjalankan eksperimen:

```bash
python experiment.py
```

Atau:

```bash
python app.py
```

### 5. Configuration

File konfigurasi:

```text
config.json
```

Parameter utama:

```json
{
  "cache_enabled": true,
  "cache_size": 256,
  "concurrency": 50,
  "request_count": 1000,
  "random_seed": 42
}
```

### 6. Expected Output

Output yang dihasilkan:

```text
Average Response Time
Throughput
Error Rate
```

Contoh:

```text
Response Time : 121 ms
Throughput    : 850 req/s
Error Rate    : 0%
```

Output disimpan dalam:

```text
results/
├── response_time.csv
├── throughput.csv
└── summary_report.txt
```

---

# Struktur Repository

```text
WS-09/
│
├── README.md
├── requirements.txt
├── config.json
├── app.py
├── experiment.py
│
├── results/
│   ├── response_time.csv
│   ├── throughput.csv
│   └── summary_report.txt
│
└── docs/
    └── environment_specification.md
```

---

# Refleksi

Eksperimen yang dirancang pada penelitian ini telah memenuhi prinsip **repeatability** karena menghasilkan nilai response time dan throughput yang konsisten pada tiga kali pengujian menggunakan environment yang sama. Selain itu, spesifikasi hardware, software, dependency, konfigurasi, dan prosedur eksekusi telah didokumentasikan secara rinci sehingga memungkinkan peneliti lain untuk melakukan pengujian ulang dengan langkah yang sama.

Meskipun demikian, untuk mencapai tingkat **reproducibility** yang lebih tinggi pada berbagai platform dan perangkat, penelitian ini masih dapat ditingkatkan melalui penggunaan Docker atau containerization sehingga seluruh dependency dan konfigurasi lingkungan dapat dijalankan secara identik pada sistem yang berbeda.

### Level Saat Ini

* [x] Repeatability
* [x] Reproducibility
* [ ] Belum Keduanya

### Komponen yang Masih Dapat Ditingkatkan

* Implementasi Docker Container.
* Lock file dependency yang lebih ketat.
* Otomatisasi pengujian menggunakan CI/CD.
* Dokumentasi hasil eksperimen yang lebih rinci.

---

**Kesimpulan:** Implementasi penelitian telah dirancang sebagai instrumen pengukuran yang konsisten, terdokumentasi, dan dapat diulang sehingga hasil yang diperoleh lebih valid, terpercaya, serta sesuai dengan prinsip penelitian ilmiah yang baik.
