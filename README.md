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

## Overview

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
