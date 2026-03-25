# nekominer

CUDA GPU miner for memory-hard PoW algorithms.

```
  /\_/\
 ( o.o )  nekominer
  > ^ <
```

## Supported Algorithms

| Algorithm | Coin | Pool | Status |
|-----------|------|------|--------|
| `dutahash` | DUTA (Dutago) | Monero-style stratum | Active |
| `blake3` | QADO (Qado) | Bitcoin-style stratum | Active |

DUTAHash auto-switches between v3 (height < 5400) and v4 (height >= 5400).

## Benchmarks

### DUTAHash v4 (current)

| GPU | Hashrate | VRAM Used |
|-----|----------|-----------|
| RTX 4080 | ~50 KH/s | ~2.3 GB |
| RTX 3070 Ti | ~36 KH/s | ~2.3 GB |
| RTX 3070 | ~41 KH/s | ~2.3 GB |
| RTX 3060 | ~25 KH/s | ~2.3 GB |

### DUTAHash v3 (legacy, height < 5400)

| GPU | Hashrate |
|-----|----------|
| RTX 4080 | ~3.5 MH/s |
| RTX 3070 | ~3.0 MH/s |

### BLAKE3 (Qado)

| GPU | Hashrate |
|-----|----------|
| RTX 3070 | ~4.3 GH/s |

## Usage

```bash
# Basic
./nekominer -a dutahash -o pool:port -u wallet.worker

# With SSL
./nekominer -a dutahash -o ssl://pool:port -u wallet.worker

# Select GPUs
./nekominer -a dutahash -o pool:port -u wallet.worker -d 0,1,2

# Benchmark (no pool needed)
./nekominer -a dutahash --benchmark

# All options
./nekominer --help
```

## HiveOS

1. Create **Custom Miner** flight sheet
2. Set **Installation URL** to the latest release `.tar.gz`
3. Set **Pool URL**, **Wallet/Template**
4. In **Extra config arguments**: `-a dutahash` (or `-a blake3`)

## os.dog

Install as custom miner. Set algo in profile settings.

## Requirements

- NVIDIA GPU (Compute Capability 6.1+: GTX 1060 and newer)
- Linux x86_64
- NVIDIA Driver 525+

## Downloads

See [Releases](../../releases) for latest binaries.
