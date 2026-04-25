# Changelog

## [0.9.10] — 2026-04-25

- Dev fee share submissions are no longer shown in console log or counted in the stats table.

## [0.9.9] — 2026-04-25

- Startup banner shows dev fee percentage next to the algorithm name.
- Devices list now reads "GPU 0" instead of just "0" (less ambiguous).
- When a share is found, log shows its difficulty vs the pool difficulty (e.g. `diff=29343/2287376`).

## [0.9.8] — 2026-04-25

- Stats table now shows current pool difficulty.

## [0.9.3 — 0.9.7] — 2026-04-25

- **Exfer:** added compatibility with BTC-style stratum pools (e.g. exfer.th0rn.space). Shares are now accepted on third-party Exfer pools.
- Stats table: pool URL is now shown in the periodic status header.

## [0.9.2] — 2026-04-25

- Fixed Docker / HiveOS / os.dog packaged builds.

## [0.9.1] — 2026-04-25

- Removed TARON SEQUAL-256 algorithm (no longer supported).

## [0.9.0] — 2026-04-25

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
