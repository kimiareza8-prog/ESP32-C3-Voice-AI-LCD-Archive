# ESP32-C3 Voice + LCD + AI Host — Project Archive

**Current firmware:** v21.1 compile fix (integrated microphone / LCD / host bridge).  
**Current host:** v21 LCD & AI (flat PHP directory).  
**Historical ESP32-S3:** partial sanitized references in `history/early-S3`.

## What is included

- `firmware/`: latest combined ESP32-C3 MAX4466 / ST7789 Arduino sketch.
- `host/public_html_3/`: latest PHP host, dashboards, AI voice, typed prompts and LCD rendering.
- `lcd/`: TFT_eSPI setup references and independent Direct SPI display demos.
- `hardware_and_previews/`: selected actual board pinout and LCD preview assets.
- `history/`: selected prior firmware versions and key S3 context.
- `docs/FILES_AVAILABLE_IN_SESSION.json`: inventory and SHA-256 of original conversation project files, **including large archives that must not be uploaded verbatim**.

## IMPORTANT: secrets are intentionally removed

Old sketches and archives have hardcoded Wi-Fi credentials / device tokens. This repository-ready copy replaces many known assignments with `CONFIGURE_LOCALLY`; some old material is intentionally not included. **Do not upload raw original ZIP archives to GitHub** without fully auditing nested files first. Restore your real settings locally before uploading firmware.

Do not commit real API keys, user Wi-Fi passwords, shared device tokens, audio recordings, or `host/public_html_3/data/` runtime files. The server's private configuration and encryption keys must remain exclusively on the server, not in Git.

## Installation outline

1. Arduino-ESP32 3.x, target `ESP32C3 Dev Module`.
2. LCD ST7789 1.69 inch 240x280 on MOSI GPIO7, SCLK GPIO6, RES GPIO4, DC GPIO5, CS GPIO10; MAX4466 OUT on GPIO0.
3. Copy `host/public_html_3/` **contents** to `public_html/3/` after backing up your production host. Never overwrite server `data` credentials.
4. Before compile, configure your own Wi-Fi fallback credentials and per-device shared token locally. Align server & device tokens.
5. Validate firmware and end-to-end flow on real hardware; previous patches were not all fully compiled or hardware-tested.

## Project behavior

Audio: ADC continuous → temporary segmented ADPCM flash journal → HTTPS verified upload → WAV server-side.  
AI: speech-to-text → selected language-model API → answer text.  
LCD: host-side rasterized 4-bit 280x240 landscape pages → C3 Direct SPI row streaming.  
Also includes typed question UI to generate an answer and push LCD display.

## Historical material

`docs/FILES_AVAILABLE_IN_SESSION.json` inventories the raw files available at preparation time. A separate **private/offline raw backup** contains the full original session material (including samples and credential-bearing archives). That raw archive is NOT GitHub-safe.