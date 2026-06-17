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
| `vecnohash` | VE (Vecno) | 1% |
| `equihash` | YEC (Ycash) | 2% |
| `exfer` | EXFER (Exfer) | 10% |
| `btx` | BTX | 10% |
| `blake3` |  | 10% |

## Usage

```bash
./nekominer -a <algo> -o <pool-url> -u <wallet>.<worker>
./nekominer --help
```

Choose `-a` from the table above. Per-algorithm pool URLs, connection examples, and
HiveOS flight sheets are in the sections below; pools shown with `ssl://` need the prefix.

**HiveOS:** create a **Custom Miner** flight sheet with installation URL
`https://github.com/shatll-s/nekominer-release/releases/download/v0.11.23/nekominer-hiveos-0.11.23.tar.gz`
and pick the algorithm in *Extra config arguments*. Ready-made per-pool flight sheets are below.

## Requirements

- NVIDIA GPU (Compute Capability 6.0+: Tesla P100 and newer)
- Linux x86_64
- NVIDIA Driver 525+

---

## VecnoHash — VE (Vecno)

| GPU | Hashrate |
|-----|----------|
| RTX 3070 | ~39 MH/s |

```bash
./nekominer -a vecnohash -o ssl://ninjaraider.com:44701 -u %ADDRESS%.%WORKER%
```

<details>
<summary>VECNO ninjaraider nekominer</summary>

```json
{
  "name": "VECNO ninjaraider nekominer",
  "items": [{
    "coin": "VECNO",
    "miner": "custom",
    "miner_config": {
      "url": "ssl://ninjaraider.com:44701",
      "miner": "nekominer-hiveos",
      "template": "%WAL%.%WORKER_NAME%",
      "install_url": "https://github.com/shatll-s/nekominer-release/releases/download/v0.11.23/nekominer-hiveos-0.11.23.tar.gz",
      "user_config": "-a vecnohash"
    }
  }]
}
```
</details>

## Equihash — YEC (Ycash)

| GPU | Hashrate |
|-----|----------|
| RTX 3070 | ~46.5 Sol/s |

```bash
./nekominer -a equihash -o ssl://ninjaraider.com:44561 -u %ADDRESS%.%WORKER%
```

<details>
<summary>YEC ninjaraider nekominer</summary>

```json
{
  "name": "YEC ninjaraider nekominer",
  "items": [{
    "coin": "YEC",
    "miner": "custom",
    "miner_config": {
      "url": "ssl://ninjaraider.com:44561",
      "miner": "nekominer-hiveos",
      "template": "%WAL%.%WORKER_NAME%",
      "install_url": "https://github.com/shatll-s/nekominer-release/releases/download/v0.11.23/nekominer-hiveos-0.11.23.tar.gz",
      "user_config": "-a equihash"
    }
  }]
}
```
</details>

## Exfer — EXFER

Memory-bound (Argon2id m=64 MiB t=2 p=1) — hashrate scales with L2 cache size and memory bandwidth.

| GPU | Hashrate |
|-----|----------|
| RTX 3070 Ti Laptop | ~827 H/s |

```bash
./nekominer -a exfer -o ssl://ninjaraider.com:44913 -u %ADDRESS%.%WORKER%
./nekominer -a exfer -o ssl://exfer.luckypool.io:3336 -u %ADDRESS%.%WORKER%
```

| Pool | Connection |
|------|------------|
| ninjaraider.com | `ssl://ninjaraider.com:44913` or `ninjaraider.com:44912` |
| luckypool.io | `ssl://exfer.luckypool.io:3336` or `exfer.luckypool.io:3335` |

<details>
<summary>EXFER ninjaraider nekominer</summary>

```json
{
  "name": "EXFER ninjaraider nekominer",
  "items": [{
    "coin": "EXFER",
    "miner": "custom",
    "miner_config": {
      "url": "ssl://ninjaraider.com:44913",
      "miner": "nekominer-hiveos",
      "template": "%WAL%.%WORKER_NAME%",
      "install_url": "https://github.com/shatll-s/nekominer-release/releases/download/v0.11.23/nekominer-hiveos-0.11.23.tar.gz",
      "user_config": "-a exfer"
    }
  }]
}
```
</details>

<details>
<summary>EXFER luckypool nekominer</summary>

```json
{
  "name": "EXFER luckypool nekominer",
  "items": [{
    "coin": "EXFER",
    "miner": "custom",
    "miner_config": {
      "url": "ssl://exfer.luckypool.io:3336",
      "miner": "nekominer-hiveos",
      "template": "%WAL%.%WORKER_NAME%",
      "install_url": "https://github.com/shatll-s/nekominer-release/releases/download/v0.11.23/nekominer-hiveos-0.11.23.tar.gz",
      "user_config": "-a exfer"
    }
  }]
}
```
</details>

## BTX

| GPU | Hashrate |
|-----|----------|
| RTX 3070 | _TBD_ |

`--pool-proto ninja` (ninjaraider, default) puts the worker in the address (`address.worker`); `minebtx` and `aria` take a bare address plus `--worker <name>`.

```bash
# ninjaraider.com — primary pool (ninja proto, default; worker goes in the address)
./nekominer -a btx -o ssl://ninjaraider.com:44921 -u <BTX_ADDRESS>.rig

# minebtx.com
./nekominer -a btx -o minebtx.com:3333 -u <BTX_ADDRESS> --worker rig --pool-proto minebtx

# bitminerpool.xyz (same minebtx protocol)
./nekominer -a btx -o bitminerpool.xyz:3333 -u <BTX_ADDRESS> --worker rig --pool-proto minebtx

# AriaBrain — mine on stratum.ariabrain.com:3940 (NOT pool.ariabrain.com)
./nekominer -a btx -o stratum.ariabrain.com:3940 -u <BTX_ADDRESS> --worker rig --pool-proto aria
```

| Pool | Connection | `--pool-proto` |
|------|------------|----------------|
| ninjaraider.com | `ssl://ninjaraider.com:44921` | `ninja` (default) |
| minebtx.com | `minebtx.com:3333` | `minebtx` |
| bitminerpool.xyz | `bitminerpool.xyz:3333` | `minebtx` |
| AriaBrain | `stratum.ariabrain.com:3940` | `aria` |

<details>
<summary>BTX ninjaraider nekominer</summary>

```json
{
  "name": "BTX ninjaraider nekominer",
  "items": [{
    "coin": "BTX",
    "miner": "custom",
    "miner_config": {
      "url": "ssl://ninjaraider.com:44921",
      "miner": "nekominer-hiveos",
      "template": "%WAL%.%WORKER_NAME%",
      "install_url": "https://github.com/shatll-s/nekominer-release/releases/download/v0.11.23/nekominer-hiveos-0.11.23.tar.gz",
      "user_config": "-a btx"
    }
  }]
}
```
</details>

<details>
<summary>BTX minebtx nekominer</summary>

```json
{
  "name": "BTX minebtx nekominer",
  "items": [{
    "coin": "BTX",
    "miner": "custom",
    "miner_config": {
      "url": "minebtx.com:3333",
      "miner": "nekominer-hiveos",
      "template": "%WAL%.%WORKER_NAME%",
      "install_url": "https://github.com/shatll-s/nekominer-release/releases/download/v0.11.23/nekominer-hiveos-0.11.23.tar.gz",
      "user_config": "-a btx --pool-proto minebtx"
    }
  }]
}
```
</details>

<details>
<summary>BTX bitminerpool nekominer</summary>

```json
{
  "name": "BTX bitminerpool nekominer",
  "items": [{
    "coin": "BTX",
    "miner": "custom",
    "miner_config": {
      "url": "bitminerpool.xyz:3333",
      "miner": "nekominer-hiveos",
      "template": "%WAL%.%WORKER_NAME%",
      "install_url": "https://github.com/shatll-s/nekominer-release/releases/download/v0.11.23/nekominer-hiveos-0.11.23.tar.gz",
      "user_config": "-a btx --pool-proto minebtx"
    }
  }]
}
```
</details>

<details>
<summary>BTX ariapool nekominer</summary>

```json
{
  "name": "BTX ariapool nekominer",
  "items": [{
    "coin": "BTX",
    "miner": "custom",
    "miner_config": {
      "url": "stratum.ariabrain.com:3940",
      "miner": "nekominer-hiveos",
      "template": "%WAL%",
      "install_url": "https://github.com/shatll-s/nekominer-release/releases/download/v0.11.23/nekominer-hiveos-0.11.23.tar.gz",
      "user_config": "-a btx --pool-proto aria --worker %WORKER%"
    }
  }]
}
```
</details>

## Downloads

See [Releases](../../releases).
