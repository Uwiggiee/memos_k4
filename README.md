# Memos

<img align="right" height="96px" src="https://www.usememos.com/logo-rounded.png" alt="Memos" />

Memos adalah sebuah layanan pencatat yang ringan, open-source, dan mengutamakan privasi (privacy-first). Aplikasi ini dirancang untuk menjadi tempat bagi Anda mencatat ide dan pemikiran secara cepat dan efisien. Konsepnya mirip seperti memiliki Twitter atau media sosial pribadi, di mana setiap catatan ("memo") ditampilkan dalam sebuah alur waktu (timeline).

![Memos Application Screenshot](https://www.usememos.com/demo.png)


## INSTALASI

# System Requirements
Minimum Requirements
- RAM: 512 MB
- Storage: 1 GB available space
- CPU: Any modern x86_64 or ARM64 processor

Supported Platforms
- Linux (x86_64, ARM64)
- macOS (Intel, Apple Silicon)
- Windows (x86_64)
- Docker (all platforms)

Database Support
- SQLite (default) - Perfect for single-user instances
- PostgreSQL - Recommended for multi-user production deployments
- MySQL/MariaDB - Alternative for existing MySQL infrastructure

Prasyarat

Pastikan perangkat lunak berikut sudah terinstal di VM:
1.  **Docker**: Platform untuk menjalankan aplikasi dalam kontainer.
2.  **Docker Compose**: Alat untuk mendefinisikan dan menjalankan aplikasi Docker.
3.  **Akses Terminal/CLI**: Akses ke antarmuka baris perintah di VM Anda.

# Langkah Instalasi

1.  **Buat Direktori Proyek**
    Buat folder untuk menyimpan file konfigurasi Memos, lalu masuk ke direktori tersebut.
    ```bash
    mkdir memos-app
    cd memos-app
    ```

2.  **Buat File `docker-compose.yml`**
    Buat file konfigurasi menggunakan editor teks seperti `nano`.
    ```bash
    nano docker-compose.yml
    ```
    Salin dan tempel konten berikut ke dalam file:
    ```yaml
    version: "3.0"
    services:
      memos:
        image: neosmemo/memos:latest
        container_name: memos
        volumes:
          - ~/.memos/:/var/opt/memos
        ports:
          - "5230:5230"
        restart: unless-stopped
    ```
    > **Penting:** Bagian `volumes` memetakan direktori `~/.memos/` di VM Anda ke dalam kontainer. Ini memastikan data Anda (database, gambar, dll.) tetap aman meskipun kontainer dihapus.

3.  **Jalankan Aplikasi**
    Simpan file, lalu jalankan Memos di latar belakang (`-d`).
    ```bash
    docker-compose up -d
    ```

4.  **Akses Aplikasi**
    Buka browser dan akses Memos melalui `http://<IP_ADDRESS_VM>:5230`. Anda akan diminta untuk membuat akun admin saat pertama kali masuk.

## Konfigurasi

Konfigurasi lanjutan dapat diakses melalui menu **Settings** di antarmuka web Memos.

* **Batas Upload File**: Jika Anda menggunakan *reverse proxy* seperti Nginx, Anda mungkin perlu mengatur `client_max_body_size` di konfigurasi Nginx untuk mengizinkan unggahan file yang lebih besar.
* **Login dengan Pihak Ketiga (SSO)**:
    1.  Buka **Settings > SSO**.
    2.  Pilih provider (misalnya, Google atau GitHub).
    3.  Dapatkan **Client ID** dan **Client Secret** dari provider tersebut.
    4.  Masukkan kredensial ke Memos untuk mengaktifkannya.
* **Editor Markdown**: Sudah menjadi fitur inti dan tidak memerlukan plugin tambahan.


## Cara Pemakaian

# Tampilan Aplikasi & Fungsi Utama
Antarmuka Memos sangat minimalis, berfokus pada kotak input dan timeline.
- Membuat Memo: Ketik di kotak input. Gunakan sintaks Markdown untuk format.
- Menggunakan Tags: Tambahkan tag seperti #proyek atau #ide untuk mengkategorikan.
- Membuat Checklist: Gunakan sintaks - [ ] untuk item tugas yang belum selesai dan - [x] untuk yang sudah.
- Mengatur Visibilitas: Setiap memo bisa diatur sebagai Public, Protected, atau Private.


















## Quick Start

Get Memos running in under 1 minutes with Docker:

```bash
docker run -d \
  --name memos \
  --restart unless-stopped \
  -p 5230:5230 \
  -v ~/.memos:/var/opt/memos \
  neosmemo/memos:stable
```

Access Memos at `http://localhost:5230` and complete the initial setup.

**Alternative methods**: For Docker Compose, binary installation, or building from source, see our [Installation Guide](https://www.usememos.com/docs/installation).



## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=usememos/memos&type=Date)](https://star-history.com/#usememos/memos&Date)
