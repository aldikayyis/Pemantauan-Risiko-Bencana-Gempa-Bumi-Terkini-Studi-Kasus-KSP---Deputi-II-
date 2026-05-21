# 🌋 Pemantauan Risiko Bencana Gempa Bumi Terkini (Studi Kasus KSP - Deputi II)

![Status](https://img.shields.io/badge/Status-Completed-success)
![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Folium](https://img.shields.io/badge/Library-Folium-green.svg)
![Pandas](https://img.shields.io/badge/Library-Pandas-150458.svg)

> **Catatan Portofolio:** Proyek ini merupakan simulasi *Data Pipeline* dan Visualisasi Geospasial yang dirancang untuk mendukung pengambilan keputusan strategis di lingkungan **Kantor Staf Presiden (KSP), khususnya Deputi II (Bidang Pembangunan Manusia)** dalam konteks mitigasi dan tanggap darurat bencana.

---

## 📑 Latar Belakang

Indonesia, yang berada di kawasan *Ring of Fire*, memiliki kerentanan tinggi terhadap bencana alam, terutama gempa bumi. Bagi para pengambil kebijakan di tingkat pusat (KSP), kecepatan informasi dan akurasi titik lokasi adalah kunci untuk memobilisasi bantuan (Bansos, relawan, medis) secara tepat sasaran.

Proyek ini bertujuan untuk mengotomatisasi penarikan data gempabumi terkini (>5.0 SR) langsung dari sistem peringatan dini BMKG dan memvisualisasikannya dalam bentuk *dashboard* geospasial interaktif, menghilangkan kebutuhan pengecekan manual.

## 🎯 Tujuan Proyek

1. **Automated Data Extraction:** Membangun *script* Python untuk mengekstrak data JSON secara *real-time* dari Open API BMKG tanpa hambatan birokrasi (tanpa API Key).
2. **Data Cleaning & Engineering:** Membersihkan data spasial (memisahkan Lintang & Bujur) agar siap dianalisis.
3. **Geospatial Dashboarding:** Mengonversi data tabular menjadi peta interaktif menggunakan `Folium`.
4. **Risk Classification:** Mengklasifikasikan tingkat ancaman gempa berdasarkan indikator geologis (Kedalaman dan Magnitude) ke dalam palet warna yang intuitif.

## 🛠️ Tech Stack yang Digunakan

* **Bahasa Pemrograman:** Python
* **Data Wrangling:** `pandas` (untuk manipulasi DataFrame dan *cleaning*)
* **API Requests:** `requests` (untuk komunikasi dengan REST API BMKG)
* **Visualisasi Spasial:** `folium` (berbasis Leaflet.js untuk peta interaktif)

---

## 📈 Alur Kerja (Pipeline)

1. **Scraping (`fetch_bmkg_gempa.py`):** Script akan melakukan HTTP GET *request* ke *endpoint* BMKG, menangkap JSON, dan merapikannya menjadi `data_gempa_terkini_bmkg.csv`.
2. **Mapping (`peta_gempa_bmkg.py`):** Script membaca CSV, menjalankan *business logic* (penentuan warna merah/oranye/hijau berdasarkan kedalaman), dan me-*render* file `dashboard_peta_gempa.html`.

## 🎨 Logika Klasifikasi Visual (Business Rules)

Pada *dashboard* peta, setiap titik gempa dikategorikan untuk memudahkan pembacaan risiko oleh pimpinan:

* 🔴 **Merah (Dangkal, < 60 km):** Risiko kerusakan permukaan tinggi. Prioritas mitigasi infrastruktur.
* 🟠 **Oranye (Menengah, 60 - 300 km):** Risiko menengah.
* 🟢 **Hijau (Dalam, > 300 km):** Energi biasanya teredam sebelum mencapai permukaan.
* 📏 **Radius Titik:** Ukuran lingkaran merepresentasikan besaran Magnitude (SR). Semakin besar, semakin luas radius lingkarannya.

---

## 🚀 Cara Menjalankan Proyek Secara Lokal

Jika Anda ingin mencoba menjalankan sistem ini di komputer Anda sendiri, ikuti langkah-langkah berikut:

### 1. Prasyarat

Pastikan Python sudah terpasang, lalu *install library* yang dibutuhkan:

```bash
pip install pandas requests folium
```

2. Eksekusi Script
Jalankan script secara berurutan di terminal Anda:

```Bash
# Langkah 1: Tarik data terbaru dari BMKG
python fetch_bmkg_gempa.py

# Langkah 2: Buat peta interaktif
python peta_gempa_bmkg.py
3. Lihat Hasil
Buka file dashboard_peta_gempa.html yang baru saja terbuat menggunakan peramban web (Google Chrome, Firefox, dll) untuk berinteraksi dengan peta.
```
Dibuat oleh Aldi Smart Nur Irfansyah - Calon Tenaga Terampil Data KSP
