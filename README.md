[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](LICENSE)
[![Doctrine v11 LOCKED](https://img.shields.io/badge/Doctrine-v11_LOCKED-d4a444.svg)](https://github.com/szl-holdings/lutar-lean)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.19944926.svg)](https://doi.org/10.5281/zenodo.19944926)
[![CI](https://github.com/szl-holdings/khipu-constellation/actions/workflows/ci.yml/badge.svg)](https://github.com/szl-holdings/khipu-constellation/actions)
[![Security Policy](https://img.shields.io/badge/Security-Policy-red.svg)](SECURITY.md)

---
title: Khipu Constellation
emoji: 🌌
colorFrom: indigo
colorTo: green
sdk: static
app_file: index.html
pinned: false
license: apache-2.0
---

# Khipu Constellation

A frontier 3D star field where **every Khipu receipt across the six SZL flagships is a star**.

- **Position** = `hash(receiptId)` mapped to a deterministic 3D spherical shell (reproducible across reloads).
- **Color** = flagship (a11oy / amaru / sentra / rosie / vessels / killinchu, Kanchay palette).
- **Brightness + size** = Yuyay score of the receipt.
- **Arcs** connect chained receipts (`prev → cur`) — the cords of the receipt DAG.
- **Live data**: polls the real `/v1/ledger` endpoint of each flagship every **5 s**
  (`https://szlholdings-<flagship>.hf.space/api/<flagship>/v1/ledger`).
- **Honest fallback**: if an endpoint is unreachable the star field runs in clearly-labelled
  **DEMO MODE** with deterministic synthetic receipts, and auto-promotes to **LIVE** the moment any
  real endpoint answers (`LIVE · n/6`).
- **Filters**: flagship toggles, Yuyay-score floor, time window.

**Tech**: React Three Fiber stack / Three.js **r171**, **WebGPURenderer** baseline with **WebGL2 fallback**
(badge in the HUD shows the active backend), GPU `InstancedMesh` for up to 20k stars, Kanchay design tokens.

Embeddable anywhere via `<iframe src="https://szlholdings-khipu-constellation.hf.space"></iframe>`.

— Yachay (CTO), SZL Holdings
