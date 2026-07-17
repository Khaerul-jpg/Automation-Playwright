# Automation Testing - Playwright

Proyek ini berisi *script* otomatisasi pengujian (automation testing) menggunakan **Playwright** dan **Pytest**. Proyek ini dirancang untuk memudahkan pengujian fungsionalitas aplikasi dan sudah dikonfigurasi agar dapat dijalankan secara terisolasi menggunakan **Docker**.

## 📁 Struktur Direktori

- `backend-node/` & `frontend-react/` : Direktori pendukung aplikasi.
- `config/` : Berisi file konfigurasi untuk berbagai *environment* pengujian (misal: dev, staging, prod).
- `pages/` : Implementasi *Page Object Model* (POM) untuk memisahkan logika antarmuka dan *script* pengujian.
- `test-data/` : Kumpulan data yang digunakan untuk pengujian (mock data, kredensial, dll).
- `tests/` : Kumpulan *script* pengujian utama.
- `utils/` : Berisi fungsi-fungsi *helper* atau utilitas yang dapat digunakan ulang di berbagai *script* pengujian.

## 🛠️ Persiapan Awal (Instalasi)

Sebelum menjalankan pengujian, pastikan Anda sudah melakukan instalasi berikut:

### 1. Download & Install Docker
Docker dibutuhkan untuk menjalankan *script* pengujian secara instan di dalam *container* yang terisolasi.
- Unduh Docker Desktop sesuai dengan sistem operasi Anda melalui situs resminya: [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- Lakukan instalasi dan pastikan aplikasi Docker sudah dalam keadaan berjalan (*running*) di komputer Anda.

### 2. Download & Install Playwright (Untuk Pengujian Lokal)
Jika Anda hanya ingin menggunakan Docker, Anda bisa melewati langkah ini. Namun, jika Anda ingin memodifikasi atau menjalankan *script* secara lokal, instal Playwright dengan perintah berikut di terminal Anda:
```bash
# Instal dependensi pytest dan playwright
pip install pytest-playwright

# Download browser pendukung (Chromium, Firefox, WebKit)
playwright install
