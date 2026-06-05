# SQueue-Care

![SQueue-Care](https://img.shields.io/badge/SQueue--Care-Healthcare%20Queue%20Management-blue)

**SQueue-Care** adalah sistem manajemen antrean rumah sakit pintar dan sistem pendukung keputusan klinis (Clinical Decision Support System - CDSS) terintegrasi. Proyek ini bertujuan untuk mengurangi waktu tunggu pasien, mengoptimalkan alokasi pelayanan kesehatan, dan mempermudah dokter dalam menegakkan diagnosis awal dengan bantuan AI.

---

## Tautan Repositori Proyek (SQueue-Care Ecosystem)

Sistem ini terbagi ke dalam beberapa repositori yang saling terintegrasi:
* **Frontend (FE):** [SQueue-Care Frontend](https://github.com/SQueue-Care/frontend/tree/main) — Aplikasi antarmuka pasien (booking & tracking), admin (monitoring), dan dokter (CDSS panel) berbasis React.
* **Backend (BE):** [SQueue-Care Backend](https://github.com/SQueue-Care/backend/tree/main) — Layanan API backend berbasis Node.js/Express, Prisma ORM, dan PostgreSQL.
* **Machine Learning (ML):** [SQueue-Care ML](https://github.com/SQueue-Care/ml/tree/main) — Layanan prediksi waktu tunggu antrean dan diagnosis CDSS berbasis Python/FastAPI.
* **Data Science (DS):** [SQueue-Care Data Science](https://github.com/SQueue-Care/data_science) — Pembersihan data, analisis durasi pelayanan, EDA, dan visualisasi data kesehatan.

---

## Tautan Demo & Aplikasi (Live Deployment)

Aplikasi **SQueue-Care** telah di-deploy secara publik dan dapat diakses melalui tautan berikut:
- **Aplikasi Web (Frontend):** [SQueue-Care Live Preview](https://squeue-care.netlify.app/) (Netlify)
- **API Layanan Utama (Backend):** [SQueue-Care Backend API](https://api-squeue.peix.my.id)
- **Dokumentasi API Layanan Prediksi (ML Service):** [SmartQueue ML Swagger API Docs](https://prediksi-waktu-tunggu-epdta4f5bjheajf5.southeastasia-01.azurewebsites.net/docs) (Azure App Services)
- **Dashboard Analisis Data (Streamlit):** [SQueue-Care Analytics Dashboard](https://squeuecare-analytics.streamlit.app/)

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

* **Tautan Unduh Model (Google Drive):**
  Model-model hasil pelatihan yang sudah diserialisasikan ke format `.joblib` / `.pkl` dapat diunduh langsung melalui folder Google Drive berikut:
  👉 [SQueue-Care ML Models (Google Drive)](https://drive.google.com/drive/folders/1N48kWDc9rZ1_6FGKqeHNw5USVE4DrLY5?usp=sharing)
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

Untuk mempermudah persiapan lingkungan kerja (environment setup), silakan ikuti petunjuk detail yang terdapat di setiap repositori masing-masing komponen:

1. **Frontend (FE):** Ikuti panduan setup pada [README.md Frontend](https://github.com/SQueue-Care/frontend/tree/main#readme).
2. **Backend (BE):** Ikuti panduan setup pada [README.md Backend](https://github.com/SQueue-Care/backend/tree/main#readme).
3. **Machine Learning (ML):** Ikuti panduan setup pada [README.md ML Service](https://github.com/SQueue-Care/ml/tree/main#readme).
4. **Data Science (DS):** Ikuti panduan setup pada [README.md Data Science](https://github.com/SQueue-Care/data_science#readme).

---

## Kontribusi

Masing-masing repositori memiliki panduan kontribusi yang dapat diakses di berkas `CONTRIBUTING.md` masing-masing proyek.

Built with ❤️ for the 2026 Coding Camp powered by DBS Foundation.
