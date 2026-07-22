# Setup Guide

This guide covers first-time setup for the plane_radar firmware on an ESP32 + ILI9341 + XPT2046 board.

## 1. Prerequisites

- VS Code with PlatformIO extension
- USB data cable
- Python and PlatformIO toolchain installed by PlatformIO extension

## 2. Hardware Profile

Configured target in this repo:

- Board env: esp32dev
- Display: ILI9341 (landscape UI)
- Touch: XPT2046 on HSPI

## 3. Build Firmware

From repository root:

```bash
pio run
```

Expected result: SUCCESS for environment esp32dev.

## 4. Flash Firmware

Connect board over USB, then run:

```bash
pio run -t upload
```

If upload fails due to busy serial port, close any active monitor first.

## 5. Upload Web Files (LittleFS)

Required for web setup UI and static assets:

```bash
pio run -t uploadfs
```

## 6. Open Serial Monitor (optional)

```bash
pio device monitor -b 115200
```

Use this for boot logs, Wi-Fi state, and poller diagnostics.

## 7. First Boot Wi-Fi Setup

- If no Wi-Fi is saved, the device starts setup AP automatically.
- If Wi-Fi exists, hold touch during boot for about 2 seconds to open setup.
- Connect to AP named SkyGauge-XXXX.
- Complete captive portal setup.

## 8. Runtime Access

After Wi-Fi joins:

- Open device web UI via hostname (example):
  - http://esp-gauge.local
- If mDNS does not resolve, use the IP shown on device status screen.

## 9. Common Commands

Build only:

```bash
pio run
```

Flash firmware:

```bash
pio run -t upload
```

Flash filesystem:

```bash
pio run -t uploadfs
```

## 10. Troubleshooting

- Upload fails with serial lock:
  - Close monitor/other serial apps and retry upload.
- Blank or clipped display edge:
  - Verify rotation and panel offsets in src/board_config.h.
- Touch seems off:
  - Recheck touch mapping constants in src/main.cpp.
- Web UI missing files:
  - Run pio run -t uploadfs.
- API errors or stale data:
  - Check Wi-Fi quality and rate-limit responses from upstream APIs.
