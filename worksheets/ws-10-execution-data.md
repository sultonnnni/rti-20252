# WS-10: Experiment Execution & Data Collection

## Pertemuan 10 — Eksekusi Eksperimen & Pengumpulan Data

**Nama:** Ahmad Sultoni
**NIM:** 240202850
**Mata Kuliah:** Research & Teknologi Informasi (RTI)

---

# Latihan 1 — Execution Plan

Tujuan eksperimen adalah membandingkan performa arsitektur e-learning pada empat skenario berbeda menggunakan metrik Response Time dan Throughput.

| Run # | Skenario            | Seed | Parameter Kunci    | Status  |
| ----- | ------------------- | ---- | ------------------ | ------- |
| 1     | Baseline            | 42   | 200 User, 10 Menit | Planned |
| 2     | Baseline            | 123  | 200 User, 10 Menit | Planned |
| 3     | Baseline            | 456  | 200 User, 10 Menit | Planned |
| 4     | Baseline            | 789  | 200 User, 10 Menit | Planned |
| 5     | Baseline            | 999  | 200 User, 10 Menit | Planned |
| 6     | Cache Only          | 42   | 200 User, 10 Menit | Planned |
| 7     | Cache Only          | 123  | 200 User, 10 Menit | Planned |
| 8     | Cache Only          | 456  | 200 User, 10 Menit | Planned |
| 9     | Cache Only          | 789  | 200 User, 10 Menit | Planned |
| 10    | Cache Only          | 999  | 200 User, 10 Menit | Planned |
| 11    | Load Balancing Only | 42   | 200 User, 10 Menit | Planned |
| 12    | Load Balancing Only | 123  | 200 User, 10 Menit | Planned |
| 13    | Load Balancing Only | 456  | 200 User, 10 Menit | Planned |
| 14    | Load Balancing Only | 789  | 200 User, 10 Menit | Planned |
| 15    | Load Balancing Only | 999  | 200 User, 10 Menit | Planned |
| 16    | Hybrid              | 42   | 200 User, 10 Menit | Planned |
| 17    | Hybrid              | 123  | 200 User, 10 Menit | Planned |
| 18    | Hybrid              | 456  | 200 User, 10 Menit | Planned |
| 19    | Hybrid              | 789  | 200 User, 10 Menit | Planned |
| 20    | Hybrid              | 999  | 200 User, 10 Menit | Planned |

### Ringkasan Eksekusi

* Total skenario : 4
* Run per skenario : 5
* Total run keseluruhan : 20

### Parameter yang Dikunci

* Jumlah Concurrent Users : 200
* Durasi Pengujian : 10 Menit
* Database : MySQL 8.0
* Dataset : 10.000 Record
* Hardware : Sama untuk seluruh pengujian
* Tool Load Testing : Apache JMeter 5.6
* Monitoring : Prometheus & Grafana

---

# Latihan 2 — Data Log Terstruktur

## Identitas

| Field     | Contoh              |
| --------- | ------------------- |
| Run ID    | run-001             |
| Timestamp | 2026-06-23T10:30:00 |
| Scenario  | Hybrid              |
| Tester    | Ahmad Sultoni       |
| Hostname  | Local-Research-Node |

## Konfigurasi

| Field                  | Contoh        |
| ---------------------- | ------------- |
| Seed                   | 42            |
| Code Version           | commit-a1b2c3 |
| Docker Compose Version | 2.29          |
| Nginx Version          | 1.28          |
| Redis Version          | 8.0           |
| MySQL Version          | 8.0           |
| Concurrent Users       | 200           |
| Duration               | 10 Minutes    |

## Hasil

| Metrik            | Tipe Data | Range Valid |
| ----------------- | --------- | ----------- |
| Response Time Avg | Float     | > 0 ms      |
| Response Time P95 | Float     | > 0 ms      |
| Response Time P99 | Float     | > 0 ms      |
| Throughput        | Float     | > 0 req/sec |
| Error Rate        | Float     | 0–100 %     |
| CPU Usage         | Float     | 0–100 %     |
| Memory Usage      | Float     | 0–100 %     |

## Metadata Tambahan

| Field              | Keterangan            |
| ------------------ | --------------------- |
| Warning Log        | Peringatan selama run |
| Error Log          | Error yang muncul     |
| Resource Usage     | CPU & RAM             |
| Execution Duration | Lama eksekusi aktual  |

### Format Output

* [x] CSV
* [x] JSON
* [ ] Database
* [ ] Lainnya

File yang dihasilkan:

```text
logs/
├── run_001.csv
├── run_001.json
├── run_002.csv
├── run_002.json
└── summary.csv
```

---

# Latihan 3 — Anomaly Protocol

| Jenis Anomali                 | Contoh                                               | Tindakan                                                                       |
| ----------------------------- | ---------------------------------------------------- | ------------------------------------------------------------------------------ |
| Run gagal (Crash)             | Docker container berhenti mendadak                   | Dokumentasikan error, perbaiki konfigurasi, lakukan re-run dan simpan log lama |
| Hasil ekstrem                 | Response time tiba-tiba 5× lebih besar dari run lain | Investigasi CPU, RAM, dan log sistem sebelum memutuskan re-run                 |
| Waktu eksekusi anomali        | Pengujian selesai lebih cepat dari durasi seharusnya | Verifikasi konfigurasi JMeter dan validasi log                                 |
| Inkonsistensi dengan run lain | Throughput turun drastis hanya pada satu run         | Bandingkan resource usage dan log, jangan langsung menghapus data              |

### Prinsip Penanganan Anomali

Detect → Investigate → Document → Decide

Langkah yang digunakan:

1. Mendeteksi anomali melalui monitoring Grafana.
2. Menginvestigasi log Nginx, Redis, dan Docker.
3. Mendokumentasikan seluruh kejadian.
4. Menentukan apakah data tetap digunakan atau perlu re-run.

Catatan:

Run anomali tidak boleh langsung dihapus karena dapat menjadi temuan penelitian yang menunjukkan batas kemampuan sistem.

---

# Refleksi

### Pengalaman Sebelumnya

Pada beberapa tugas praktikum sebelumnya, pengujian sering dilakukan hanya satu kali dan hasilnya langsung digunakan sebagai kesimpulan. Pendekatan tersebut berisiko menghasilkan kesimpulan yang bias karena hasil dapat dipengaruhi kondisi sesaat seperti beban CPU, penggunaan memori, atau faktor acak lainnya.

### Yang Akan Dilakukan Berbeda

Pada penelitian ini setiap skenario akan dijalankan sebanyak lima kali dengan seed yang telah ditentukan sebelumnya. Hasil seluruh run akan dicatat dalam log terstruktur dan dianalisis menggunakan nilai rata-rata, variasi hasil, serta distribusi metrik performa. Dengan demikian tingkat kepercayaan terhadap kesimpulan penelitian menjadi lebih tinggi dan lebih sesuai dengan prinsip penelitian ilmiah yang dapat diuji ulang.

### Kesimpulan

Multiple run memberikan gambaran performa yang lebih representatif dibandingkan single run. Dengan pengulangan eksperimen dan dokumentasi yang lengkap, hasil penelitian menjadi lebih valid, repeatable, dan dapat dipertanggungjawabkan secara ilmiah.
