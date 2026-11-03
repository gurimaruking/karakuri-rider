# Karakuri Rider / からくりライダー

> An original karakuri (mechanical doll) rider on a toy tricycle that drives itself — DonkeyCar-style autonomous driving on a **D-Robotics RDK X5**, with on-device vision on the BPU.

[![Brain: RDK X5](https://img.shields.io/badge/Brain-RDK%20X5-0085CA.svg)](https://developer.d-robotics.cc/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

**D-Robotics Robotics Dream Keeper Challenge — Winter 2026**
Built at [Robostadion](https://robostadion.com), a robot maker space in Akihabara, Tokyo. DUG Tokyo.
Progress thread on the challenge Discord: <https://discord.com/channels/1300358874280230994/1567099448453111848>

| Stage | Window | Status |
|---|---|---|
| 1 — Ignite | Nov 1–10, 2026 | In progress |
| 2 — Build | Nov 11–26, 2026 | Not started |
| 3 — Launch | Nov 27–Dec 15, 2026 | Not started |

## What it is

- **Body:** a toy RC tricycle (front-wheel steering, rear-wheel drive), rebuilt so the RDK X5 drives it instead of the toy receiver.
- **Rider:** an original karakuri doll — white lacquer-style face, round red cheeks, a jaw that opens and closes, and LED eyes.
- **Brain:** RDK X5 in the cargo box. A wide-angle camera hidden in the headlight.
- **Goal:** drive a track on its own, as fast as the little tricycle can go, using a model trained from manual driving data.

## Stage 1 — Board bring-up

### Hardware

| Item | Notes |
|---|---|
| RDK X5 (8 GB) | |
| microSD 32 GB | RDK OS 3.5.0 (Desktop image) |
| USB-C power adapter, 5 V / 5 A | Required by the RDK X5 |
| USB-C data cable | For the QuickLink (Type-C direct) connection |
| Camera | TODO: model and interface (MIPI / USB) |

### 1. Flash the image

Image used: `rdk-x5-ubuntu22-preinstalled-desktop-3.5.0-arm64.img.xz`
Source: <https://archive.d-robotics.cc/downloads/os_images/rdk_x5/rdk_os_3.5.0-2026-4-9/>

Written with Raspberry Pi Imager ("Use custom", no OS customisation). On Windows, cancel the "format this drive" prompt that appears after writing.

### 2. Connect

- **USB-C (QuickLink):** RDK Studio → Add device → RDK Type-C direct. Board address `192.168.128.10`.
- **Ethernet (fallback):** set the PC to a static address on `192.168.127.0/24`; board address `192.168.127.10`.

### 3. SSH

```bash
ssh <user>@192.168.128.10
```

TODO: paste the exact commands you ran and their output into `docs/evidence/stage1/`.

### 4. Sensor and first AI task

TODO: camera check and one on-device AI task (YOLO via the official samples). Record the command, the model name and the FPS shown.

### Troubleshooting

| Symptom | Fix |
|---|---|
| Windows asks to format the card after writing | Click Cancel. The Linux partition is not readable by Windows. |
| No RDK network adapter appears | Use a USB-C cable that carries data, not a charge-only cable. Re-plug and refresh. |
| Board reboots under load | Check the power adapter is 5 V / 5 A. |

## Repository layout (planned)

```
karakuri-rider/
├── docs/           # proposal, architecture, evidence, BOM
├── src/            # driving stack and doll control
├── launch/         # ROS 2 launch files
├── models/         # model conversion notes (no large binaries)
├── config/
├── hardware/       # 3D-printed parts (doll face, mounts)
└── tests/
```

## Credits

- D-Robotics RDK X5, RDK Studio and RDK Model Zoo.
- DonkeyCar project for the driving-stack approach.

## License

MIT — see [LICENSE](LICENSE). Third-party models and assets keep their own licenses; each one is listed in `docs/licenses.md`.
