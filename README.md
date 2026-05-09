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

## Benchmarks

### VecnoHash

| GPU | Hashrate |
|-----|----------|
| RTX 3070 | ~39 MH/s |

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
./nekominer -a vecnohash -o ninjaraider.com:44700 -u wallet.worker
./nekominer -a exfer -o ssl://ninjaraider.com:44913 -u %ADDRESS%.%WORKER%
./nekominer -a exfer -o ssl://exfer.luckypool.io:3336 -u %ADDRESS%.%WORKER%

./nekominer --help
```

### Supported Exfer pools

| Pool | Connection |
|------|------------|
| ninjaraider.com | `ssl://ninjaraider.com:44913` or `ninjaraider.com:44912` |
| luckypool.io | `ssl://exfer.luckypool.io:3336` or `exfer.luckypool.io:3335` |

## HiveOS

Create a **Custom Miner** flight sheet.

**Installation URL:**
```
https://github.com/shatll-s/nekominer-release/releases/download/v0.9.23/nekominer-hiveos-0.9.23.tar.gz
```

**Extra config arguments:** `-a blake3`, `-a vecnohash`, or `-a exfer`

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
      "install_url": "https://github.com/shatll-s/nekominer-release/releases/download/v0.9.23/nekominer-hiveos-0.9.23.tar.gz",
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
      "install_url": "https://github.com/shatll-s/nekominer-release/releases/download/v0.9.23/nekominer-hiveos-0.9.23.tar.gz",
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
      "install_url": "https://github.com/shatll-s/nekominer-release/releases/download/v0.9.23/nekominer-hiveos-0.9.23.tar.gz",
      "user_config": "-a exfer"
    }
  }]
}
```
</details>

## os.dog

Select **custom** miner in profile settings.

**Installation URL:**
```
https://github.com/shatll-s/nekominer-release/releases/download/v0.9.23/nekominer-osdog-0.9.23.tar.gz
```

Set algo in extra arguments: `-a blake3`, `-a vecnohash`, or `-a exfer`

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
  "custom_url": "https://github.com/shatll-s/nekominer-release/releases/download/v0.9.23/nekominer-osdog-0.9.23.tar.gz"
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
  "custom_url": "https://github.com/shatll-s/nekominer-release/releases/download/v0.9.23/nekominer-osdog-0.9.23.tar.gz"
}
```
</details>

## Requirements

- NVIDIA GPU (Compute Capability 6.0+: Tesla P100 and newer)
- Linux x86_64
- NVIDIA Driver 525+

## Downloads

See [Releases](../../releases).
