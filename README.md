# User-Owned Social

**User is owner — on your phone or your chosen cloud.**

An open-source Android photo/video social network being designed around user-controlled identity, portable data, local-first operation, and minimal shared infrastructure.

> **Status: planning / pre-implementation.** There is no Android application, APK, production service, or verified P2P implementation in this repository yet. Proposed capabilities below are goals, not shipped features. The name is temporary.

## Prinsip / Principles

- Pengguna mengendalikan identitas, akses, dan lokasi penyimpanan datanya.
- Media dapat berada di HP, perangkat pribadi lain, atau cloud pilihan pengguna.
- Cloud bersifat opsional; membuat akun aplikasi tidak otomatis menyediakan cloud gratis.
- Identitas tidak terikat pada satu penyedia penyimpanan atau relay.
- Ekspor, backup, pemulihan, dan migrasi merupakan fungsi inti.
- Salinan yang sudah diterima orang lain tidak dapat dijamin terhapus.

## Proposed architecture

Native Android: Kotlin and Jetpack Compose. Local database and media first; signed social metadata over replaceable relays; direct P2P where reachable; optional user-connected cloud storage.

Shared application servers handle bounded metadata, discovery, and signaling. They are not the mandatory media store. In device-only mode, media waits when no source is reachable. User-connected cloud may improve availability but has its own quotas and costs.

See [architecture](docs/ARCHITECTURE.md), [roadmap and test gates](docs/ROADMAP.md), and [component review](docs/COMPONENTS.md).

## Collaborate

Contributions in Bahasa Indonesia and English are welcome: design review, Android development, networking experiments, accessibility, documentation, translations, and testing on real devices.

Start with [CONTRIBUTING.md](CONTRIBUTING.md). Open an issue to discuss a substantial change, or send a small, focused pull request. Public contribution does not grant direct write access; maintainers review changes.

No build instructions are available yet because the Android project has not been created. The first milestone is a measured two-device transport experiment.

## License

Original repository content is available under the [MIT License](LICENSE). Imported components retain their licenses and notices. A proposed dependency is not an imported dependency; none of the external application code has been copied into this repository.
