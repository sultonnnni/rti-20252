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

```mermaid
graph TD
A[Load Generator<br>(JMeter / Locust)] --> B[Web Server<br>(Nginx)]

B --> C[App Server A<br>(Backend API)]
B --> D[App Server B<br>(Backend API)]

C --> E[Optimization Layer]
D --> E

E --> F[Database<br>(MySQL)]
F --> G[Monitoring & Logging<br>(Grafana / Logs)]
 
---

## 🔍 Penjelasan

Arsitektur ini dirancang secara modular untuk mendukung eksperimen perbandingan metode optimasi sistem. Load generator digunakan untuk mensimulasikan beban pengguna, sedangkan web server dan application server menangani request utama.

Bagian utama penelitian terletak pada optimization layer, yang memungkinkan pengujian metode caching dan load balancing secara terpisah. Monitoring & logging digunakan untuk mengukur response time dan throughput sebagai variabel dependen.

Pendekatan ini memastikan isolasi variabel, sehingga hasil eksperimen lebih valid dan dapat direproduksi.



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
