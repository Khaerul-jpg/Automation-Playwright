# Automation Testing - Playwright

Proyek ini berisi *script* otomatisasi pengujian (automation testing) menggunakan **Playwright** dan **Pytest**. Proyek ini dirancang untuk memudahkan pengujian fungsionalitas aplikasi dan sudah dikonfigurasi agar dapat dijalankan secara terisolasi menggunakan **Docker**.

## 📁 Struktur Direktori

- `backend-node/` & `frontend-react/` : Direktori pendukung aplikasi.
- `config/` : Berisi file konfigurasi untuk berbagai *environment* pengujian (misal: dev, staging, prod).
- `pages/` : Implementasi *Page Object Model* (POM) untuk memisahkan logika antarmuka dan *script* pengujian.
- `test-data/` : Kumpulan data yang digunakan untuk pengujian (mock data, kredensial, dll).
- `tests/` : Kumpulan *script* pengujian utama.
- `utils/` : Berisi fungsi-fungsi *helper* atau utilitas yang dapat digunakan ulang di berbagai *script* pengujian.

## 🚀 Cara Menjalankan (menggunakan Docker)

Proyek ini telah dikemas ke dalam *image* Docker. Anda tidak perlu menginstal dependensi Python atau Playwright secara lokal untuk menjalankan pengujian.

Pastikan **Docker** sudah terinstal dan berjalan di mesin Anda. Untuk menjalankan *test suite* (contoh: `set_personal_info.py`), gunakan perintah berikut di terminal:

```bash
docker run --rm khaerulrafli/playwright-automation:v11 pytest -s --log-cli-level=INFO "Personal Information-Field/set_personal_info.py" --env=dev --username=<ISI_USERNAME_ANDA> --password=<ISI_PASSWORD_ANDA>
