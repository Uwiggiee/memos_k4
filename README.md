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
















Memos is a lightweight, self-hosted alternative to cloud-based note-taking services. Built with privacy and performance in mind, it offers a comprehensive platform for personal knowledge management without compromising data ownership or security.

## Key Features

### Privacy & Security

- **Complete Data Ownership** — All data stored locally in your chosen database
- **Self-Hosted Architecture** — Full control over infrastructure and access policies
- **No External Dependencies** — Zero third-party services or cloud connections required

### Content Creation

- **Instant Save** — Streamlined plain text input with automatic persistence
- **Rich Markdown Support** — Full Markdown rendering with syntax highlighting
- **Media Integration** — Native support for images, links, and embedded content

### Performance & Technology

- **High-Performance Backend** — Built with Go for optimal resource utilization
- **Modern React Frontend** — Responsive, intuitive user interface
- **Lightweight Deployment** — Minimal system requirements, maximum efficiency
- **Cross-Platform** — Linux, macOS, Windows, and containerized environments

### Customization

- **Configurable Interface** — Custom branding, themes, and UI elements
- **API-First Design** — RESTful API for seamless third-party integrations
- **Multi-Database Support** — SQLite, PostgreSQL, and MySQL compatibility

### Cost-Effective

- **Open Source (MIT)** — Full source code availability with permissive licensing
- **Zero Subscription Fees** — No usage limits, premium tiers, or hidden costs
- **Community-Driven** — Transparent development with active community support

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

**Pro Tip**: The data directory stores all your notes, uploads, and settings. Include it in your backup strategy!

## Sponsors

Memos is made possible by the generous support of our sponsors. Their contributions help ensure the project's continued development, maintenance, and growth.

<a href="https://github.com/yourselfhosted" target="_blank"><img src="https://avatars.githubusercontent.com/u/140182318?v=4" alt="yourselfhosted" height="60" /></a>
<a href="https://github.com/fixermark" target="_blank"><img src="https://avatars.githubusercontent.com/u/169982?v=4" alt="fixermark" height="60" /></a>
<a href="https://github.com/alik-agaev" target="_blank"><img src="https://avatars.githubusercontent.com/u/2662697?v=4" alt="alik-agaev" height="60" /></a>

<p><strong>Every contribution, no matter the size, makes a difference!</strong></p>

<a href="https://github.com/sponsors/usememos" target="_blank">
  <img src="https://img.shields.io/badge/Sponsor-❤️-red?style=for-the-badge" alt="Sponsor Memos">
</a>

## Contributing

Memos welcomes contributions from developers, designers, and users worldwide. We value quality, innovation, and community feedback.

**Ways to Contribute:**

- Code contributions (bug fixes, features, performance improvements)
- Documentation and user guides
- Testing and bug reporting
- Localization and translation
- Community support

**Get Started**: [Contributing Guide](https://github.com/usememos/memos/blob/main/CONTRIBUTING.md) • [Code of Conduct](https://github.com/usememos/memos/blob/main/CODE_OF_CONDUCT.md)

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=usememos/memos&type=Date)](https://star-history.com/#usememos/memos&Date)
