# Memos

<img align="right" height="96px" src="https://www.usememos.com/logo-rounded.png" alt="Memos" />

Memos adalah sebuah layanan pencatat yang ringan, open-source, dan mengutamakan privasi (privacy-first). Aplikasi ini dirancang untuk menjadi tempat bagi Anda mencatat ide dan pemikiran secara cepat dan efisien. Konsepnya mirip seperti memiliki Twitter atau media sosial pribadi, di mana setiap catatan ("memo") ditampilkan dalam sebuah alur waktu (timeline).

![Memos Application Screenshot](https://www.usememos.com/demo.png)


# INSTALASI

## System Requirements
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

# Konfigurasi

Konfigurasi lanjutan dapat diakses melalui menu **Settings** di antarmuka web Memos.

* **Batas Upload File**: Jika Anda menggunakan *reverse proxy* seperti Nginx, Anda mungkin perlu mengatur `client_max_body_size` di konfigurasi Nginx untuk mengizinkan unggahan file yang lebih besar.
* **Login dengan Pihak Ketiga (SSO)**:
    1.  Buka **Settings > SSO**.
    2.  Pilih provider (misalnya, Google atau GitHub).
    3.  Dapatkan **Client ID** dan **Client Secret** dari provider tersebut.
    4.  Masukkan kredensial ke Memos untuk mengaktifkannya.
* **Editor Markdown**: Sudah menjadi fitur inti dan tidak memerlukan plugin tambahan.


# Cara Pemakaian

## Tampilan Aplikasi & Fungsi Utama
Antarmuka Memos sangat minimalis, berfokus pada kotak input dan timeline.
- Membuat Memo: Ketik di kotak input. Gunakan sintaks Markdown untuk format.
- Menggunakan Tags: Tambahkan tag seperti #proyek atau #ide untuk mengkategorikan.
- Membuat Checklist: Gunakan sintaks - [ ] untuk item tugas yang belum selesai dan - [x] untuk yang sudah.
- Mengatur Visibilitas: Setiap memo bisa diatur sebagai Public, Protected, atau Private.


# Pembahasan
## Kelebihan 👍

- Kontrol Penuh Atas Data: Privasi terjamin karena self-hosted.
- Cepat dan Ringan: Antarmuka responsif dan tidak membebani server.
- Sederhana dan Fokus: Minimalis, bebas dari distraksi fitur yang tidak perlu.
- Fleksibel berkat API: Membuka peluang untuk integrasi dan otomatisasi.
- Instalasi Sangat Mudah: Dengan Docker, proses instalasi menjadi sangat cepat dan tidak rumit.

## Kekurangan 👎
- Memerlukan Pengetahuan Teknis: Proses instalasi dan maintenance menjadi penghalang bagi pengguna non-teknis.
- Tidak Ada Aplikasi Mobile Native: Akses di ponsel harus melalui browser (PWA), yang pengalamannya tidak sebaik aplikasi native.
- Fitur Kolaborasi Terbatas: Lebih dirancang untuk penggunaan personal daripada kerja tim.


# Perbandingan dengan Apple Notes
Jika dibandingkan dengan aplikasi sejenis yang populer seperti Apple Notes (Notes di iPhone), Memos menunjukkan perbedaan filosofi yang mendasar.
Perbedaan paling fundamental terletak pada platform dan kepemilikan data. Memos adalah aplikasi self-hosted yang berjalan di server pribadi Anda, memberikan kontrol penuh dan privasi 100% atas data. Sebaliknya, Apple Notes terintegrasi erat dengan ekosistem Apple dan menyimpan data pengguna di server iCloud. Dari segi biaya, perangkat lunak Memos gratis namun memerlukan biaya untuk server, sementara Apple Notes gratis sebagai bagian dari pembelian perangkat Apple.

Dari segi pengalaman penggunaan dan organisasi, keduanya juga berbeda. Memos menggunakan sistem tag (#tag) yang fleksibel dan penulisan berbasis Markdown, yang sangat efisien untuk pencatatan cepat dan teknis. Sementara itu, Apple Notes mengandalkan sistem folder yang lebih tradisional seperti file manager dan editor Rich Text (WYSIWYG), yang terasa lebih familiar bagi pengguna umum.

Untuk fitur tambahan, Apple Notes unggul dalam hal kreativitas dan integrasi ekosistem, dengan kemampuan untuk menggambar, memindai dokumen, dan kolaborasi yang solid dengan pengguna Apple lainnya. Keunggulan unik Memos justru terletak pada API-nya, yang membuka pintu bagi otomatisasi dan integrasi dengan alur kerja lain, sesuatu yang tidak dimiliki Apple Notes.

Kesimpulan Perbandingan
Memos adalah pilihan ideal bagi pengguna teknis yang memprioritaskan kepemilikan data, privasi, dan kesederhanaan. Ini adalah alat yang sempurna untuk power user yang ingin membuat "bank ide" pribadi yang bisa diakses dari mana saja.
Apple Notes lebih cocok untuk pengguna umum dalam ekosistem Apple yang membutuhkan aplikasi pencatat yang serbaguna, mudah digunakan, dan terintegrasi penuh dengan perangkat mereka.


