# Changelog

## [0.9.19] — 2026-05-03

- SMEM bank conflict swizzle for Exfer — **~814 H/s** on RTX 3070 Ti Laptop (+13% over 0.9.15).
- Fixed VRAM out-of-memory on multi-GPU rigs.

## [0.9.15] — 2026-05-02

- Added **luckypool.io** compatibility for Exfer algorithm (auto-detects pool protocol).
- Keryx (KHeavyHash) algorithm support.

## [0.9.13] — 2026-04-25

- Fixed high CPU load average on multi-GPU rigs (now correctly sleeps while waiting for GPU on all devices, not just the first).

## [0.9.12] — 2026-04-25

- Added **Exfer** algorithm — Argon2id memory-hard PoW (~580 H/s on RTX 3070 Ti Laptop).

## [0.7.x] — 2026-03-27 → 2026-04-03

- Autotune progress logs and 15-second tuning window.
- Various performance and stability improvements.

## [0.6.0] — 2026-03-26

- Added **VecnoHash** algorithm (Vecno blockchain).

## [0.5.x] — 2026-03-25

- DUTAHash performance improvements (~38 KH/s on RTX 3070).

## [0.4.x] — 2026-03-23

- SSL/TLS support and dev fee.
- DUTAHash algorithm.
- HiveOS/os.dog packaging.

## [0.3.x] — 2026-03-19

- BLAKE3 performance: 1.9 → 3.6 GH/s on RTX 3070.

## [0.2.x] — 2026-03-19

- Multi-GPU support, colored output, stats table.

## [0.1.0] — 2026-03-19

- Initial release: BLAKE3 (Qado) CUDA GPU miner.
