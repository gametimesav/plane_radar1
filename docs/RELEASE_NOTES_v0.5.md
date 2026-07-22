# v0.5 Release Notes

Release date: 2026-07-21

## Highlights

- Full Sky Gauge firmware base integrated for ESP32 + ILI9341 + XPT2046.
- Radar, Weather, Auto, and Home Integration modes active.
- Touch setup flow improved:
  - Auto setup portal when no Wi-Fi is saved.
  - Hold touch during boot to reopen setup.
- Radar UI improvements:
  - Smoother sweep and improved blip behavior.
  - Touch-select aircraft details panel.
  - Aircraft type shown in selected details.
  - In-range aircraft totals available in UI.
  - LIVE connectivity/fetch indicator in details panel (idle state).
  - Type-based silhouette visual in details panel.
- Network/data reliability updates:
  - Streaming JSON parsing to reduce memory pressure.
  - Better retry/status handling for radar and weather.
  - Continuous radar polling support outside direct radar view (throttled).
- Web UI and device services:
  - Web config UI served from LittleFS.
  - OTA update support kept in firmware.

## Hardware Target

- Board: ESP32 Dev Module (esp32dev)
- Display: ILI9341, 240x320
- Touch: XPT2046 (HSPI)

## Included in Tag

- Tag: v0.5
- Commit: fbce4b2

## Upgrade Notes

- If web assets appear missing or stale after firmware update, upload filesystem:
  - pio run -t uploadfs
- If display edge clipping appears on some panel variants, tune panel offsets in src/board_config.h.
