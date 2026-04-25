# Changelog

All notable changes to nekominer.

## [0.9.1] — 2026-04-25

### Removed
- TARON SEQUAL-256 algorithm (no longer supported)

## [0.9.0] — 2026-04-25

### Added
- **Exfer algorithm** (Argon2id m=64 MiB, t=2, p=1) — CUDA GPU mining
- BTC-style stratum support (auto-detects simplified vs full notify format)

### Performance
- ~580 H/s on RTX 3070 Ti Laptop

## [0.6.0] — 2026-03-26

### Added
- **VecnoHash** algorithm — Blake3 memory-hard PoW for Vecno blockchain

## [0.4.5] — 2026-03-23

### Added
- SSL/TLS support
- rplant-compatible stratum
- GPU-side digest, VarDiff (v0.4.2)
- GPU-accelerated dataset build — 2.3s → 0.1s (v0.4.3)

## [0.3.3] — 2026-03-19

### Performance
- **BLAKE3**: 1.9 → 3.6 GH/s on RTX 3070
- Midstate optimization (v0.3.0), multi-nonce kernel (v0.3.1)
- Inline schedule, 48 regs (v0.3.2), half-compress + shared memory (v0.3.3)

## [0.2.1] — 2026-03-19

### Added
- Multi-GPU support, colored output, stats table (v0.2.0)
- Reusable stratum framework (v0.2.1)

## [0.1.0] — 2026-03-19

### Added
- Initial multi-algorithm CUDA GPU miner
- BLAKE3 (cpupowv3 / Qado)
