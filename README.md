# plane_radar (Sky Gauge Base + Touch Setup)

This workspace now uses the `Krasnov777/esp32-sky-gauge` firmware structure and modules, adapted for your ESP32 2.8" ILI9341 + XPT2046 board.

## What Changed

- Sky Gauge modular firmware is now the base (`src/` and `data/` were replaced).
- Board/display driver is adapted to ESP32 Dev + ILI9341 (240x320).
- Touch setup path is added:
  - If no Wi-Fi is saved, setup portal starts automatically.
  - If Wi-Fi is saved, hold touch for ~2 seconds during boot to open setup.
- Setup credentials are saved into Sky Gauge settings storage (NVS).

## Hardware Target

- MCU: ESP32 Dev Module (`esp32dev`)
- Display: ILI9341, 240x320
- Touch: XPT2046 (HSPI: SCLK 25, MISO 39, MOSI 32, CS 33)

## Build And Flash

```bash
pio run -t upload
```

## Setup Flow

1. On first boot (or touch-hold at boot), connect to AP `SkyGauge-XXXX`.
2. Complete Wi-Fi setup in the captive portal.
3. Device saves credentials and continues into Sky Gauge runtime.

## Notes

- Partition layout is set to `huge_app.csv` so this Sky Gauge build fits on ESP32.
- LVGL memory and draw buffers were reduced for non-PSRAM ESP32 hardware.
