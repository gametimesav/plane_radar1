# plane_radar

Plane radar project for an ESP32 smart display board.

## Hardware

- Board: ESP32 Development Board 2.8 inch 240 x 320 Smart Display TFT Module Touch Screen LVGL
- MCU: ESP32 (WROOM class module)
- Display: 240 x 320 TFT
- Touch: integrated touch panel

## Development Baseline

- Framework: Arduino (ESP32 core)
- UI library: LVGL
- Typical display/touch drivers: board-dependent TFT + touch controller libraries

## Notes

- Pin mapping, display controller model, and touch controller model can vary by vendor revision of this board.
- Confirm your exact board revision before finalizing wiring constants and driver config.
