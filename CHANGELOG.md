# Changelog

All notable changes to nekominer.

## [0.9.7] — 2026-04-25

### Fixed
- Exfer stratum: extranonce1/extranonce2 byte ordering now matches pool
  (verbatim hex bytes, LE byte hex in submit). Shares now accepted on
  BTC-style Exfer pools.

## [0.9.6] — 2026-04-25

### Changed
- Exfer nonce layout: extranonce2 in LOW bytes (offset 84..84+ext2_size),
  extranonce1 in HIGH bytes per BTC stratum convention

## [0.9.5] — 2026-04-25

### Fixed
- Stats table: pool URL now shown in periodic status header
- Stats table: Total row column alignment (was off by 2 chars)

## [0.9.4] — 2026-04-25

### Added
- Exfer: split share_target (set_difficulty) and network_target (notify)
  so miners on share-difficulty pools no longer wait for full blocks

## [0.9.3] — 2026-04-25

### Added
- Exfer: 5-parameter mining.submit (worker, job_id, ext2, ntime, nonce)
  for compatibility with strict BTC-style stratum pools

## [0.9.2] — 2026-04-25

### Fixed
- Docker build (missing libargon2 dep — production uses bundled implementation)

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
