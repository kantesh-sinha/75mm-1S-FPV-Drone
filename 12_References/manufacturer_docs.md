# 12 — References

## Primary manufacturer / technical sources

### Flight controller

- BETAFPV F4 1S 5A AIO Brushless Flight Controller, Serial ELRS 2.4G:
  https://betafpv.com/products/f4-1s-5a-aio-brushless-flight-controller-elrs-2-4g
- BETAFPV F4 1S 5A AIO support / firmware information:
  https://support.betafpv.com/hc/en-us/sections/4408016911129-Betaflight-FC
- BETAFPV CLI information for F4 1S 5A BMI270 / Bluejay:
  https://support.betafpv.com/hc/en-us/articles/7064243258777-CLI-for-F4-1S-5A-Flight-Controller-BMI270-BLUEJAY-ESC-2022

### Camera

- Caddx Ant Nano: use the exact datasheet/manual corresponding to the purchased revision.
- Current EU technical listing used for preliminary electrical specifications:
  https://www.rotorama.de/product/caddx-ant-nano

### VTX

- AKK Nano3 technical specification reference:
  https://ledge-team.com/en-gb/VTX/AKK-Nano3-VTX-25-50-100-200mw

## Verified design facts

The current BETAFPV documentation confirms:

- STM32F411CEU6 MCU
- BMI270 IMU
- integrated Serial ELRS 2.4 GHz receiver
- 26 × 26 mm mounting pattern
- integrated 1S ESC
- 5 A continuous / 6 A peak ESC specification
- DShot300 / DShot600 support
- built-in Betaflight OSD
- external analog VTX support
- analog-VTX interface using CAM, VTX, GND, +5V and SmartAudio

citeturn2view0turn3view0

## Source discipline

Manufacturer documentation is preferred for:

- pad labels
- voltage/current limits
- firmware target
- UART/resource mapping
- connector type
- mounting pattern

Community builds and marketplace listings are supporting evidence, not the sole source for critical electrical specifications.

**Important:** the exact purchased hardware revision remains the authority for final wiring.
