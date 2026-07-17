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
```

## 🐳 Manajemen Docker (Bila Ada Perubahan Kode)

Jika ada pembaruan pada *script* atau kode di dalam repository ini, Anda perlu membuat ulang (*rebuild*) image Docker agar perubahan tersebut tersimpan.

```bash
# 1. Build image baru (contoh menggunakan tag v11)
docker build -t khaerulrafli/playwright-automation:v11 .

# 2. Push image ke Docker Hub
docker push khaerulrafli/playwright-automation:v11
```

## 🚀 Cara Menjalankan (menggunakan Docker)

Proyek ini telah dikemas ke dalam *image* Docker. Anda tidak perlu menginstal dependensi Python atau Playwright secara lokal untuk menjalankan pengujian.

Pastikan **Docker** sudah terinstal dan berjalan di mesin Anda. Untuk menjalankan *test suite* (contoh: `set_personal_info.py`), gunakan perintah berikut di terminal:

```bash
docker run --rm khaerulrafli/playwright-automation:v11 pytest -s --log-cli-level=INFO "Personal Information-Field/set_personal_info.py" --env=dev --username=<ISI_USERNAME_ANDA> --password=<ISI_PASSWORD_ANDA>
```

**Penjelasan Perintah:**
- `--rm` : Menghapus *container* secara otomatis setelah pengujian selesai berjalan.
- `khaerulrafli/playwright-automation:v11` : *Image* dan tag Docker yang digunakan.
- `--log-cli-level=INFO` : Menampilkan log eksekusi pengujian secara detail di terminal.
- `--env`, `--username`, `--password` : Argumen khusus yang dikirimkan ke Pytest untuk kebutuhan *login* dan pemilihan *environment*.
