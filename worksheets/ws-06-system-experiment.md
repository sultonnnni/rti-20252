# WS-06: System-Experiment Mapping & Architecture

> Bab 6 — System Design sebagai Experimental Artifact

**Nama** : Ahmad Sultoni  
**NIM** : 240202850  
**Mata Kuliah** : Research & Teknologi Informasi (RTI)  

---

## 🎯 Tujuan Sistem

Arsitektur sistem ini dirancang sebagai *experimental artifact* untuk menguji perbandingan performa antara metode caching dan load balancing pada sistem e-learning berbasis web dalam kondisi beban pengguna tinggi.

---

## 🧱 Arsitektur Sistem
            +----------------------+
            |   Load Generator     |
            | (JMeter / Locust)    |
            +----------+-----------+
                       |
                       v
            +----------------------+
            |     Web Server       |
            |       (Nginx)        |
            +----------+-----------+
                       |
    +------------------+------------------+
    |                                     |
    v                                     v
    +------------------+ +------------------+
| App Server A | | App Server B |
| (Backend API) | | (Backend API) |
+--------+---------+ +--------+---------+
| |
+------------------+-----------------+
|
v
+----------------------+
| Optimization Layer |
|----------------------|
| 1. Caching (Redis) |
| 2. Load Balancer |
+----------+-----------+
|
v
+----------------------+
| Database |
| (MySQL) |
+----------+-----------+
|
v
+----------------------+
| Monitoring & Logging |
| (Grafana / Logs) |
+----------------------+

---

## 🔍 Penjelasan Komponen

### 1. Load Generator
Digunakan untuk mensimulasikan banyak pengguna secara bersamaan menggunakan tools seperti JMeter atau Locust.

### 2. Web Server
Menerima request dari pengguna dan meneruskannya ke application server.

### 3. Application Server
Menjalankan logika sistem e-learning seperti login, akses materi, dan pengumpulan tugas.

### 4. Optimization Layer (Fokus Penelitian)
- **Caching (Redis):** Menyimpan data yang sering diakses untuk mempercepat respon  
- **Load Balancing:** Mendistribusikan request ke beberapa server  

⚠️ Kedua metode diuji secara terpisah untuk menjaga keadilan eksperimen.

### 5. Database
Menyimpan seluruh data sistem e-learning.

### 6. Monitoring & Logging
Mengukur response time, throughput, dan performa sistem lainnya.

---

## 🔗 SYSTEM-EXPERIMENT MAPPING

**Research Question**  
Apakah metode caching menghasilkan response time yang lebih rendah dibandingkan load balancing pada sistem e-learning dengan jumlah pengguna tinggi?

---

### Variable → Component Mapping

| Variabel | Tipe | Komponen Sistem | Cara Manipulasi / Pengukuran |
|----------|------|-----------------|------------------------------|
| Metode optimasi | IV | Optimization Layer | Mengaktifkan caching atau load balancing melalui konfigurasi |
| Response time | DV | Monitoring & Logging | Mengukur waktu respon dari request |
| Throughput | DV | Monitoring & Logging | Menghitung request per detik |
| Jumlah user | CV | Load Generator | Mengatur jumlah user |
| Spesifikasi server | CV | Server Configuration | Dijaga tetap sama |
| Skenario request | CV | Load Script | Digunakan sama untuk semua pengujian |

---

## ✅ 4 Prinsip Desain

| Prinsip | Status | Penjelasan |
|---------|--------|-----------|
| Traceability | ✅ | Setiap variabel terhubung ke komponen sistem |
| Modularity | ✅ | Metode optimasi dapat diganti tanpa mengubah sistem lain |
| Controllability | ✅ | Parameter diatur melalui konfigurasi |
| Measurability | ✅ | Sistem otomatis mencatat metrik performa |

---

## ⚙️ Experimental Setup

**Input Data**  
Simulasi request pengguna (login, akses materi, dll)

**Parameter**
- Jumlah user: 50, 100, 200  
- Metode: caching / load balancing  

**Output**
- Response time (ms)  
- Throughput (request/second)  
- Disimpan dalam format CSV  

---

## 🔬 Ablation Study (Perbandingan Metode)

| Kondisi | Caching | Load Balancing | Hasil yang Diharapkan |
|---------|--------|---------------|----------------------|
| Baseline | ❌ | ❌ | Performa dasar |
| Caching | ✅ | ❌ | Response time lebih cepat |
| Load Balancing | ❌ | ✅ | Throughput meningkat |

---

## 🧠 Justifikasi Desain

Arsitektur ini dirancang modular agar setiap variabel dapat diuji secara terpisah (variable isolation). Dengan pendekatan ini, perubahan pada metode optimasi tidak mempengaruhi komponen lain, sehingga hasil eksperimen lebih valid dan dapat direproduksi.

---

## 🔁 Reproducibility

- Semua parameter eksperimen dapat diatur melalui konfigurasi  
- Skenario pengujian dibuat konsisten  
- Output disimpan dalam format terstruktur  

---

## ✍️ Refleksi

Jika sistem dibangun seperti produk (monolitik), maka sulit untuk memisahkan pengaruh tiap variabel. Hal ini dapat menyebabkan hasil eksperimen menjadi bias.

Arsitektur modular memungkinkan setiap komponen diuji secara independen, sehingga hasil penelitian lebih akurat dan dapat dipertanggungjawabkan secara ilmiah.

---
