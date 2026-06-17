# nekominer

CUDA GPU miner.

```
  /\_/\
 ( o.o )  nekominer
  > ^ <
```

## Supported Algorithms

| Algorithm | Coin | Dev Fee |
|-----------|------|---------|
| `blake3` | QADO (Qado) | 10% |
| `vecnohash` | VE (Vecno) | 1% |
| `exfer` | EXFER (Exfer) | 10% |
| `equihash` | YEC (Ycash) | 2% |
| `btx` | BTX | 10% (ninja) · 0% (minebtx / aria) |

## Benchmarks

### VecnoHash

| GPU | Hashrate |
|-----|----------|
| RTX 3070 | ~39 MH/s |

### Equihash (192,7)

| GPU | Hashrate |
|-----|----------|
| RTX 3070 | ~46.5 Sol/s |

### BLAKE3

| GPU | Hashrate |
|-----|----------|
| RTX 3070 | ~4.3 GH/s |

### Exfer (Argon2id m=64 MiB t=2 p=1)

Memory-bound algorithm — hashrate scales with L2 cache size and memory bandwidth.

| GPU | Hashrate |
|-----|----------|
| RTX 3070 Ti Laptop | ~827 H/s |

## Usage

```bash
./nekominer -a blake3 -o ssl://ninjaraider.com:44811 -u wallet.worker
./nekominer -a vecnohash -o ssl://ninjaraider.com:44701 -u wallet.worker
./nekominer -a exfer -o ssl://ninjaraider.com:44913 -u %ADDRESS%.%WORKER%
./nekominer -a exfer -o ssl://exfer.luckypool.io:3336 -u %ADDRESS%.%WORKER%
./nekominer -a equihash -o ssl://ninjaraider.com:44561 -u %ADDRESS%.%WORKER%
./nekominer -a btx -o ssl://ninjaraider.com:44921 -u %ADDRESS%.%WORKER%

./nekominer --help
```

### Supported Exfer pools

| Pool | Connection |
|------|------------|
| ninjaraider.com | `ssl://ninjaraider.com:44913` or `ninjaraider.com:44912` |
| luckypool.io | `ssl://exfer.luckypool.io:3336` or `exfer.luckypool.io:3335` |

### Supported BTX pools

| Pool | Connection | `--pool-proto` |
|------|------------|----------------|
| ninjaraider.com | `ssl://ninjaraider.com:44921` | `ninja` (default) |
| minebtx.com | `minebtx.com:3333` | `minebtx` |
| bitminerpool.xyz | `bitminerpool.xyz:3333` | `minebtx` |
| AriaBrain | `stratum.ariabrain.com:3940` | `aria` |

> On `--pool-proto ninja` (ninjaraider) the worker is part of the address (`address.worker`); `minebtx` and `aria` take the bare address plus `--worker <name>`.

## HiveOS

Create a **Custom Miner** flight sheet.

**Installation URL:**
```
https://github.com/shatll-s/nekominer-release/releases/download/v0.11.22/nekominer-hiveos-0.11.22.tar.gz
```

**Extra config arguments:** `-a blake3`, `-a vecnohash`, `-a exfer`, `-a equihash`, or `-a btx`

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
      "install_url": "https://github.com/shatll-s/nekominer-release/releases/download/v0.11.22/nekominer-hiveos-0.11.22.tar.gz",
      "user_config": "-a blake3"
    }
  }]
}
```
</details>

<details>
<summary>EXFER flight sheet</summary>

```json
{
  "name": "EXFER nekominer",
  "items": [{
    "coin": "EXFER",
    "miner": "custom",
    "miner_config": {
      "url": "ssl://ninjaraider.com:44913",
      "miner": "nekominer-hiveos",
      "template": "%WAL%.%WORKER_NAME%",
      "install_url": "https://github.com/shatll-s/nekominer-release/releases/download/v0.11.22/nekominer-hiveos-0.11.22.tar.gz",
      "user_config": "-a exfer"
    }
  }]
}
```
</details>

<details>
<summary>EXFER flight sheet (luckypool.io)</summary>

```json
{
  "name": "EXFER nekominer (luckypool)",
  "items": [{
    "coin": "EXFER",
    "miner": "custom",
    "miner_config": {
      "url": "ssl://exfer.luckypool.io:3336",
      "miner": "nekominer-hiveos",
      "template": "%WAL%.%WORKER_NAME%",
      "install_url": "https://github.com/shatll-s/nekominer-release/releases/download/v0.11.22/nekominer-hiveos-0.11.22.tar.gz",
      "user_config": "-a exfer"
    }
  }]
}
```
</details>

<details>
<summary>Equihash flight sheet</summary>

```json
{
  "name": "Equihash nekominer",
  "items": [{
    "coin": "YEC",
    "miner": "custom",
    "miner_config": {
      "url": "ssl://ninjaraider.com:44561",
      "miner": "nekominer-hiveos",
      "template": "%WAL%.%WORKER_NAME%",
      "install_url": "https://github.com/shatll-s/nekominer-release/releases/download/v0.11.22/nekominer-hiveos-0.11.22.tar.gz",
      "user_config": "-a equihash"
    }
  }]
}
```
</details>

<details>
<summary>BTX flight sheet</summary>

```json
{
  "name": "BTX nekominer",
  "items": [{
    "coin": "BTX",
    "miner": "custom",
    "miner_config": {
      "url": "ssl://ninjaraider.com:44921",
      "miner": "nekominer-hiveos",
      "template": "%WAL%.%WORKER_NAME%",
      "install_url": "https://github.com/shatll-s/nekominer-release/releases/download/v0.11.22/nekominer-hiveos-0.11.22.tar.gz",
      "user_config": "-a btx"
    }
  }]
}
```
</details>

## os.dog

Select **custom** miner in profile settings.

**Installation URL:**
```
https://github.com/shatll-s/nekominer-release/releases/download/v0.11.22/nekominer-osdog-0.11.22.tar.gz
```

Set algo in extra arguments: `-a blake3`, `-a vecnohash`, `-a exfer`, `-a equihash`, or `-a btx`

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
  "custom_url": "https://github.com/shatll-s/nekominer-release/releases/download/v0.11.22/nekominer-osdog-0.11.22.tar.gz"
}
```
</details>

<details>
<summary>EXFER profile</summary>

```json
{
  "name": "EXFER nekominer",
  "coin": "custom",
  "customCoin": "EXFER",
  "wallet": "<your_address>",
  "template": "$ADDRESS.$WORKER",
  "pool": "ssl://ninjaraider.com:44913",
  "miner": "custom",
  "addition": "-a exfer",
  "fork": "latest",
  "custom_url": "https://github.com/shatll-s/nekominer-release/releases/download/v0.11.22/nekominer-osdog-0.11.22.tar.gz"
}
```
</details>

<details>
<summary>Equihash profile</summary>

```json
{
  "name": "Equihash nekominer",
  "coin": "custom",
  "customCoin": "YEC",
  "wallet": "<your_address>",
  "template": "$ADDRESS.$WORKER",
  "pool": "ssl://ninjaraider.com:44561",
  "miner": "custom",
  "addition": "-a equihash",
  "fork": "latest",
  "custom_url": "https://github.com/shatll-s/nekominer-release/releases/download/v0.11.22/nekominer-osdog-0.11.22.tar.gz"
}
```
</details>

<details>
<summary>BTX profile</summary>

```json
{
  "name": "BTX nekominer",
  "coin": "custom",
  "customCoin": "BTX",
  "wallet": "<your_address>",
  "template": "$ADDRESS.$WORKER",
  "pool": "ssl://ninjaraider.com:44921",
  "miner": "custom",
  "addition": "-a btx",
  "fork": "latest",
  "custom_url": "https://github.com/shatll-s/nekominer-release/releases/download/v0.11.22/nekominer-osdog-0.11.22.tar.gz"
}
```
</details>

## Requirements

- NVIDIA GPU (Compute Capability 6.0+: Tesla P100 and newer)
- Linux x86_64
- NVIDIA Driver 525+

## Downloads

See [Releases](../../releases).
