# WS-15: Scientific Writing

**Bab 15 — Penulisan Ilmiah**

**Nama** : Ahmad Sultoni
**NIM** : 240202850
**Mata Kuliah** : Research & Teknologi Informasi (RTI)

---

## PAPER STRUCTURE CHECKLIST

```text
Title   : Analisis Pengaruh Caching dan Load Balancing terhadap Performa Sistem E-Learning Berbasis Web
Target  : [X] Laporan / Tugas Akhir RTI

Section Check:
  [X] Abstract — masalah, metode, hasil utama, kontribusi (max 250 kata)
  [X] Introduction — konteks → gap → RQ → kontribusi → struktur paper
  [X] Related Work — concept-centric, gap positioning
  [X] Method — reproducible: desain, variabel, metrik, setup, prosedur
  [X] Results — tabel + grafik + observasi (tanpa interpretasi)
  [X] Discussion — interpretasi, perbandingan, implikasi, limitation
  [X] Conclusion — jawaban RQ, kontribusi, future work

Consistency Matrix:
  [X] RQ di Introduction = RQ di Method = RQ di Conclusion
  [X] Variabel di Method = variabel di Results
  [X] Klaim di Discussion didukung data di Results
  [X] Limitasi di Discussion di-address di Conclusion/Future Work

Writing Quality:
  [X] Clarity — mudah dipahami tanpa re-read
  [X] Precision — tidak ada istilah ambigu
  [X] Conciseness — tidak ada kalimat redundan

```

---

## Latihan 1 — Paper Outline

Outline paper untuk riset infrastruktur *e-learning* Universitas Putra Bangsa (UPB) Kebumen.

| Section | Konten Utama (2-3 kalimat) | Target Kata |
| --- | --- | --- |
| **Abstract** | Lonjakan beban trafik *e-learning* pada kondisi puncak menyebabkan penurunan performa sistem secara drastis. Studi ini mengevaluasi arsitektur *Hybrid* (Nginx *Load Balancing* dan Redis *Caching*) dengan metode eksperimen ablasi berbasis 20 *run* simulasi beban. Hasil uji ANOVA menunjukkan arsitektur *Hybrid* secara signifikan ($p < 0.001$) mereduksi *response time* sebesar 51% (menjadi $120 \pm 6\text{ ms}$) dan mendongkrak *throughput* sebesar 102% ($850 \pm 12\text{ req/sec}$) dibandingkan *baseline*. | 200-250 |
| **Introduction** | *Konteks*: Kebutuhan keandalan sistem *e-learning* kampus saat jam sibuk seperti presensi bersamaan. *Gap*: Banyak optimasi infrastruktur hanya berfokus pada salah satu layer komputasi (jaringan saja atau data saja) tanpa mengukur dampak interaksi simultan keduanya secara parsial (ablasi). *RQ*: Bagaimana pengaruh arsitektur *Hybrid* dibanding sistem tanpa optimasi terhadap reduksi *response time* dan peningkatan *throughput* *e-learning* saat beban puncak? | 500-700 |
| **Related Work** | Tinjauan pustaka mengenai penerapan *load balancing* berbasis Nginx untuk perluasan kapasitas CPU horizontal dan teknologi Redis *caching* untuk reduksi hambatan I/O *database*. Pemosisian riset dilakukan dengan membedah gap penelitian terdahulu yang jarang menyajikan data variabilitas performa terstruktur (*multiple runs*) pada simulasi arsitektur web lokal. | 700-1000 |
| **Method** | Spesifikasi eksperimen menggunakan instrumen virtualisasi lokal `docker-compose` di host Windows 11 dengan runtime Flask 3.0 dan database MySQL 8.0. Variabel bebas (IV) mencakup empat skenario (*Baseline*, *Cache Only*, *LB Only*, *Hybrid*) yang diuji konstan via injeksi *workload* JMeter sebesar 200 *concurrent users* selama 10 menit. Validasi integritas data dikunci menggunakan *random seed* tetap untuk memastikan keterulangan (*repeatability*). | 800-1200 |
| **Results** | Penyajian data numerik murni hasil 20 kali *run* eksperimen yang diekstraksi otomatis dari instrumen monitoring Prometheus dan Grafana. Data ditampilkan dalam bentuk tabel *Mean* $\pm$ *Std* dan grafik *Box Plot* distribusi performa tanpa interpretasi subjektif, termasuk dokumentasi temuan *outlier* latensi $135\text{ ms}$ pada Run 4 skenario *Hybrid*. | 500-800 |
| **Discussion** | Interpretasi atas keunggulan signifikan arsitektur *Hybrid* yang sukses memotong latensi hingga setengahnya dari *baseline*. Diskusi mendalam membedah temuan tak terduga (*unpredicted finding*) di mana skenario *LB Only* sedikit lebih unggul dibanding *Cache Only*, yang mengindikasikan bottleneck awal sistem berada pada kapasitas CPU server Flask, bukan I/O query MySQL. Pengakuan atas keterbatasan lingkungan lokal (*resource sharing host*) disampaikan secara terbuka. | 600-900 |
| **Conclusion** | Penegasan penolakan hipotesis nol ($H_0$) karena arsitektur *Hybrid* terbukti secara empiris meningkatkan performa sistem secara berkelanjutan. Rekomendasi pengembangan riset selanjutnya (*future work*) mencakup migrasi pengujian ke *cloud provider* untuk latensi publik nyata dan orkestrasi *auto-scaling* menggunakan Kubernetes. | 200-400 |

---

## Latihan 2 — Consistency Matrix

Consistency matrix untuk memverifikasi keselarasan argumen internal paper.

| Elemen | Intro | Method | Result | Discussion | Conclusion |
| --- | --- | --- | --- | --- | --- |
| **RQ1 (Pengaruh Performa Arsitektur)** | ✓ | ✓ | ✓ | ✓ | ✓ |
| **Metrik Utama (Response Time & Throughput)** | ✓ | ✓ | ✓ | ✓ | ✓ |
| **Variabel IV (Skenario Kontrol & Ablasi)** | ✓ | ✓ | ✓ | ✓ | ✓ |
| **Variabel DV (Skala ms & req/sec)** | ✓ | ✓ | ✓ | ✓ | ✓ |
| **Klaim / Kontribusi Efisiensi Hybrid** | ✓ | ✓ | ✓ | ✓ | ✓ |
| **Keterbatasan / Limitasi Riset Lokal** | ✗ | ✗ | ✓ | ✓ | ✓ |

**Isi setiap sel:** ✓ (ada & konsisten), ✗ (missing), ~ (ada tapi inkonsisten)

**Inkonsistensi yang ditemukan:**

> Elemen "Keterbatasan / Limitasi Riset Lokal" (seperti *resource sharing CPU spikes* komputer host) terdeteksi muncul secara tak terduga pada bab Result saat investigasi anomali dan dibahas di Discussion, namun secara struktural memang absen di Introduction dan Method.

**Tindakan perbaikan:**

> Hal ini merupakan alur normal dalam IMRAD, namun untuk menjaga konsistensi, ancaman validitas internal terkait *resource borrowing* komputer host ditambahkan penjelasannya pada bagian bab Method (sub-bab *Threat Mitigation*) sebagai mitigasi awal sebelum pencatatan log dijalankan.

---

## Latihan 3 — Writing Quality Check

**Paragraf asli:**

> Implementasi arsitektur Hybrid yang menggunakan kombinasi dari Nginx Load Balancing dan juga Redis Caching terbukti memiliki performa yang sangat bagus sekali dan lebih cepat. Sistem ini berhasil membuat response time dari e-learning menjadi lebih turun dan throughput dari sistemnya naik drastis sewaktu dilakukan pengujian beban puncak menggunakan tools JMeter dengan 200 user. Perubahan nilainya kelihatan beda banget kalau dibandingkan dengan baseline yang lambat.

| Kriteria | Evaluasi | Perbaikan |
| --- | --- | --- |
| **Clarity** | Frasa "performa yang sangat bagus sekali dan lebih cepat" serta "naik drastis" bersifat abstrak, subjektif, dan tidak terukur. | Mengubahnya menjadi pernyataan kuantitatif dengan menyertakan nilai persentase perubahan yang eksak ($51\%$ dan $102\%$). |
| **Precision** | Kata "lambat", "beda banget", dan "tools JMeter" tidak baku untuk penulisan ilmiah. Penggunaan istilah statistik belum presisi. | Menyertakan tingkat signifikansi statistik ($p < 0.001$), nilai rerata $\pm$ deviasi standar ($120 \pm 6\text{ ms}$ vs $245 \pm 11\text{ ms}$), serta menyebut JMeter sebagai instrumen uji beban kerja buatan. |
| **Conciseness** | Banyak kata pemborosan (*filler*) seperti "kombinasi dari", "dan juga", "sewaktu dilakukan", dan "kelihatan". | Menghapus kata mubazir dan memadatkan struktur kalimat agar fokus pada fakta data hasil eksperimen. |

**Paragraf setelah perbaikan:**

> Arsitektur *Hybrid* (Nginx *Load Balancing* dan Redis *Caching*) terbukti secara signifikan ($p < 0.001$) mengoptimalkan performa infrastruktur *e-learning* pada kondisi beban puncak. Injeksi beban kerja buatan sebesar 200 *concurrent users* menunjukkan arsitektur usulan mampu mereduksi *response time* sebesar 51% menjadi $120 \pm 6\text{ ms}$ dari nilai *baseline* awal ($245 \pm 11\text{ ms}$). Selain itu, kapasitas pemrosesan data (*throughput*) sistem melonjak sebesar 102%, naik dari $420 \pm 20\text{ req/sec}$ pada kondisi *baseline* menjadi $850 \pm 12\text{ req/sec}$.

---

## Refleksi

Menulis "tentang" riset cenderung bersifat naratif deskriptif yang sekadar melaporkan apa saja aktivitas kronologis yang dilakukan peneliti di laboratorium. Sebaliknya, menulis sebagai sebuah "argumen" riset berarti memosisikan seluruh isi paper sebagai struktur pembuktian logis yang kokoh; di mana setiap data yang disajikan dalam bab *Results* dan *Discussion* bertindak sebagai bukti empiris tak terbantahkan untuk menjawab *Research Question* serta menolak Hipotesis Nol ($H_0$) yang diajukan di bab *Introduction*.

Urutan penulisan terbalik (**Method & Results** $\rightarrow$ **Discussion** $\rightarrow$ **Introduction** $\rightarrow$ **Abstract**) secara radikal meningkatkan kualitas tulisan karena memaksa peneliti membangun bingkai narasi (*framing*) berdasarkan realitas data aktual yang sudah stabil. Hal ini secara efektif melindungikarya ilmiah dari bias kognitif *cherry-picking* (memanipulasi klaim pendahuluan agar terlihat cocok dengan hasil), menghemat waktu penyuntingan, serta memastikan jaminan konsistensi internal (*red thread*) terjaga utuh dari awal hingga akhir paragraf.
