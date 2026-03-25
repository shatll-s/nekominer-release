# nekominer

CUDA GPU miner.

```
  /\_/\
 ( o.o )  nekominer
  > ^ <
```

## Supported Algorithms

| Algorithm | Coin | Status |
|-----------|------|--------|
| `dutahash` | DUTA (Dutago) | Active |
| `blake3` | QADO (Qado) | Active |

## Benchmarks

### DUTAHash

| GPU | v4 (current) | v3 (reference) |
|-----|-------------|----------------|
| RTX 5090 | ~416 KH/s | — |
| RTX 4080 Laptop | ~50 KH/s | ~3.5 MH/s |
| RTX 3070 Ti Laptop | ~36 KH/s | ~3.0 MH/s |
| RTX 3070 | ~41 KH/s | ~3.0 MH/s |

### BLAKE3

| GPU | Hashrate |
|-----|----------|
| RTX 3070 | ~4.3 GH/s |

## Usage

```bash
./nekominer -a dutahash -o ssl://pool:port -u wallet.worker
./nekominer -a blake3 -o pool:port -u wallet.worker
./nekominer -a dutahash --benchmark
./nekominer --help
```

## HiveOS

Create a **Custom Miner** flight sheet.

**Installation URL:**
```
https://github.com/shatll-s/nekominer-release/releases/download/v0.5.8/nekominer-hiveos-0.5.8.tar.gz
```

**Extra config arguments:** `-a dutahash` or `-a blake3`

<details>
<summary>DUTA flight sheet</summary>

```json
{
  "name": "DUTA nekominer",
  "items": [{
    "coin": "DUTA",
    "miner": "custom",
    "miner_config": {
      "url": "ssl://ninjaraider.com:44821",
      "miner": "nekominer-hiveos",
      "template": "%WAL%.%WORKER_NAME%",
      "install_url": "https://github.com/shatll-s/nekominer-release/releases/download/v0.5.8/nekominer-hiveos-0.5.8.tar.gz",
      "user_config": "-a dutahash"
    }
  }]
}
```
</details>

<details>
<summary>QADO flight sheet</summary>

```json
{
  "name": "QADO nekominer",
  "items": [{
    "coin": "QADO",
    "miner": "custom",
    "miner_config": {
      "url": "ssl://ninjaraider.com:44811",
      "miner": "nekominer-hiveos",
      "template": "%WAL%.%WORKER_NAME%",
      "install_url": "https://github.com/shatll-s/nekominer-release/releases/download/v0.5.8/nekominer-hiveos-0.5.8.tar.gz",
      "user_config": "-a blake3"
    }
  }]
}
```
</details>

## os.dog

Select **custom** miner in profile settings.

**Installation URL:**
```
https://github.com/shatll-s/nekominer-release/releases/download/v0.5.8/nekominer-osdog-0.5.8.tar.gz
```

Set algo in extra arguments: `-a dutahash` or `-a blake3`

<details>
<summary>DUTA profile</summary>

```json
{
  "name": "DUTA nekominer",
  "coin": "custom",
  "customCoin": "DUTA",
  "wallet": "<your_address>",
  "template": "$ADDRESS.$WORKER",
  "pool": "ssl://ninjaraider.com:44821",
  "miner": "custom",
  "addition": "-a dutahash",
  "fork": "latest",
  "custom_url": "https://github.com/shatll-s/nekominer-release/releases/download/v0.5.8/nekominer-osdog-0.5.8.tar.gz"
}
```
</details>

<details>
<summary>QADO profile</summary>

```json
{
  "name": "QADO nekominer",
  "coin": "custom",
  "customCoin": "QADO",
  "wallet": "<your_address>",
  "template": "$ADDRESS.$WORKER",
  "pool": "ssl://ninjaraider.com:44811",
  "miner": "custom",
  "addition": "-a blake3",
  "fork": "latest",
  "custom_url": "https://github.com/shatll-s/nekominer-release/releases/download/v0.5.8/nekominer-osdog-0.5.8.tar.gz"
}
```
</details>

## Requirements

- NVIDIA GPU (Compute Capability 6.1+: GTX 1060 and newer)
- Linux x86_64
- NVIDIA Driver 525+

## Downloads

See [Releases](../../releases).
