# SQueue-Care

![SQueue-Care](https://img.shields.io/badge/SQueue--Care-Healthcare%20Queue%20Management-blue)

**SQueue-Care** adalah sistem manajemen antrean rumah sakit pintar dan sistem pendukung keputusan klinis (Clinical Decision Support System - CDSS) terintegrasi. Proyek ini bertujuan untuk mengurangi waktu tunggu pasien, mengoptimalkan alokasi pelayanan kesehatan, dan mempermudah dokter dalam menegakkan diagnosis awal dengan bantuan AI.

---

## Tautan Repositori Proyek (SQueue-Care Ecosystem)

Sistem ini terbagi ke dalam beberapa repositori yang saling terintegrasi:
* **Frontend (FE):** [SQueue-Care Frontend (main)](https://github.com/SQueue-Care/frontend/tree/main) — Aplikasi antarmuka pasien (booking & tracking), admin (monitoring), dan dokter (CDSS panel) berbasis React.
* **Backend (BE):** [SQueue-Care Backend (main)](https://github.com/SQueue-Care/backend/tree/main) — Layanan API backend berbasis Node.js/Express, Prisma ORM, dan PostgreSQL.
* **Machine Learning (ML):** [SQueue-Care ML (main)](https://github.com/SQueue-Care/ml/tree/main) — Layanan prediksi waktu tunggu antrean dan diagnosis CDSS berbasis Python/FastAPI.
* **Data Science (DS):** [SQueue-Care Data Science](https://github.com/SQueue-Care/data_science) — Pembersihan data, analisis durasi pelayanan, EDA, dan visualisasi data kesehatan.

---

## Deskripsi Singkat Proyek

### Masalah
Proses pelayanan kesehatan di rumah sakit sering kali terkendala waktu tunggu yang lama, penumpukan pasien pada poliklinik tertentu (overload), serta kurangnya transparansi informasi antrean. Selain itu, dokter membutuhkan alat bantu penegakan diagnosis awal yang cepat untuk mempercepat proses pelayanan.

### Solusi & Tujuan
SQueue-Care menghadirkan solusi berupa:
1. **Smart Queue System**: Manajemen antrean dinamis secara real-time yang memprediksi estimasi waktu tunggu pasien menggunakan AI.
2. **Clinical Decision Support System (CDSS)**: Rekomendasi diagnosis awal berbasis gejala klinis pasien dengan visualisasi confidence score untuk membantu dokter mengambil keputusan klinis secara objektif.
3. **BPJS Integration Mock**: Simulasi integrasi jaminan kesehatan nasional untuk kemudahan pendaftaran pasien.

---

## Tautan Model ML (Machine Learning)

Model Machine Learning dikembangkan dan dipelihara pada repositori [SQueue-Care ML](https://github.com/SQueue-Care/ml/tree/main).

* **Tautan Unduh Model:**
  Model tereduksi/terlatih (misalnya model prediksi waktu tunggu dan model klasifikasi gejala CDSS) diserialisasikan ke format `.joblib` / `.pkl` dan dapat diunduh di direktori `/models` pada:
  👉 [SQueue-Care ML Models](https://github.com/SQueue-Care/ml/tree/main/models)
* **Memuat (Load) Model:**
  Pada server ML (Python/FastAPI), model dimuat menggunakan pustaka `joblib` sebagai berikut:
  ```python
  import joblib

  # Memuat model prediksi waktu tunggu
  wait_time_model = joblib.load("models/wait_time_estimator.joblib")

  # Memuat model sistem pendukung keputusan klinis (CDSS)
  cdss_model = joblib.load("models/cdss_classifier.joblib")
  ```

---

## Petunjuk Setup Environment

Silakan ikuti langkah-langkah di bawah ini untuk menyiapkan lingkungan kerja masing-masing komponen:

### 1. Frontend (FE)
* Pustaka wajib: Node.js v20 LTS dan `pnpm` (atau `npm`).
* Buat berkas `.env` dan masukkan API endpoint:
  ```env
  VITE_API_URL=http://localhost:3000/api/v1
  ```

### 2. Backend (BE)
* Pustaka wajib: Node.js v20 LTS, `pnpm`, dan PostgreSQL (misal Supabase).
* Salin berkas `.env.example` menjadi `.env` di repositori backend dan lengkapi variabel berikut:
  ```env
  DATABASE_URL="postgresql://user:pass@host:6543/db?schema=public"
  DIRECT_URL="postgresql://user:pass@host:5432/db?schema=public"
  JWT_ACCESS_SECRET="min-16-karakter-acak"
  JWT_REFRESH_SECRET="min-16-karakter-acak"
  ML_SERVICE_URL="http://localhost:8000" # Opsional (jika kosong menggunakan heuristik lokal)
  ```

### 3. Machine Learning (ML)
* Pustaka wajib: Python 3.10+ dan `pip`.
* Buat virtual environment dan install dependensi:
  ```bash
  python -m venv venv
  source venv/bin/activate  # Untuk Windows: venv\Scripts\activate
  pip install -r requirements.txt
  ```

---

## Cara Menjalankan Aplikasi

Jalankan masing-masing komponen di terminal terpisah sesuai urutan di bawah ini:

### 1. Jalankan Backend (BE)
Masuk ke folder repositori `backend`, lalu jalankan:
```bash
# 1. Install dependensi
pnpm install

# 2. Sinkronisasi database & seeding data awal (admin, dokter, pasien)
pnpm prisma:migrate
pnpm prisma:seed

# 3. Jalankan server lokal
pnpm dev
```
* Server default berjalan di: `http://localhost:3000`

### 2. Jalankan Machine Learning (ML) Service
Masuk ke folder repositori `ml` (aktifkan virtual environment terlebih dahulu), lalu jalankan:
```bash
# Jalankan FastAPI server dengan uvicorn
uvicorn app.main:app --host 0.0.0.0 --port 8000 --reload
```
* Server default berjalan di: `http://localhost:8000`

### 3. Jalankan Frontend (FE)
Masuk ke folder repositori `frontend`, lalu jalankan:
```bash
# Install dependensi frontend
pnpm install

# Jalankan dev server Vite
pnpm dev
```
* Buka peramban (browser) di alamat yang tertera (biasanya `http://localhost:5173`).

---

## Kontribusi

Masing-masing repositori memiliki panduan kontribusi yang dapat diakses di berkas `CONTRIBUTING.md` masing-masing proyek.

Built with ❤️ for the 2026 Coding Camp powered by DBS Foundation.
