# 05 — Electrical Architecture

![Preliminary system wiring concept](images/blueprint_wiring_v1.jpg)

*Figure — Preliminary wiring concept generated during the concept-design phase. Exact FC pads and video routing remain verification items.*

## Power
```text
1S LiPo → BT2.0 → VBAT/GND → F4 1S AIO
                         ├─ MCU / internal regulation
                         ├─ IMU
                         ├─ ELRS
                         ├─ ESC outputs
                         ├─ camera supply
                         └─ VTX supply
```

Internal regulator topology is not assumed and must be verified against the final FC documentation.

## Propulsion
- M1 — Front Left
- M2 — Front Right
- M3 — Rear Right
- M4 — Rear Left

Each motor has three phase connections to its integrated ESC channel. Motor mapping and direction are verified during bring-up with propellers removed.

## Video
```text
Caddx Ant Nano
      │ analog video
      ▼
FC video input / OSD path
      │
      ▼
FC video output
      │
      ▼
AKK Nano3-class VTX
      │
    5.8 GHz
      ▼
FPV receiver
```

Exact FC video pad names/routing remain a verification item.

## Radio
```text
ELRS transmitter → 2.4 GHz RF → integrated ELRS receiver
                                      │
                                     CRSF
                                      ▼
                                  Betaflight
```
