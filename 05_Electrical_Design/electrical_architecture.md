# 05 — Electrical Architecture

<figure>
  <img src="images/system_architecture.svg" alt="Functional architecture of the 75 mm 1S FPV drone" />
  <figcaption><em>Figure 1 — Functional system context. See the preliminary Blueprint wiring image below for the concept-stage wiring view.</em></figcaption>
</figure>

![Preliminary system wiring concept](images/blueprint_wiring_v1.jpg)

*Figure 2 — Preliminary Blueprint wiring concept. Treat it as a design input, not a verified schematic. Confirm all connections against the purchased hardware revisions.*

## 1. Power path

```text
1S HV LiPo
   │
   │ BT2.0
   ▼
F4 1S 5A AIO FC
   ├── VBAT → integrated 4-in-1 ESC
   ├── onboard regulation → FC electronics
   ├── peripheral supply → camera / VTX, subject to ratings
   └── GND → common reference
```

BETAFPV documents the selected F4 1S 5A AIO family for 1S operation, with 5 A continuous and 6 A peak ESC current for 3 seconds and a BT2.0 power cable. Confirm the exact purchased revision and its peripheral power capabilities before connection. [Manufacturer documentation](https://betafpv.com/products/f4-1s-5a-aio-brushless-flight-controller-elrs-2-4g)

## 2. Propulsion interfaces

| Channel | Functional position | Electrical interface | Verification |
|---|---|---|---|
| M1 | Front left | 3-phase motor output from integrated ESC | Confirm mapping and direction |
| M2 | Front right | 3-phase motor output from integrated ESC | Confirm mapping and direction |
| M3 | Rear right | 3-phase motor output from integrated ESC | Confirm mapping and direction |
| M4 | Rear left | 3-phase motor output from integrated ESC | Confirm mapping and direction |

The FC sends digital motor commands to the integrated ESC. The ESC switches the motor phases. Confirm motor order and direction in Betaflight with propellers removed before any flight.

## 3. Analog video interfaces

```text
Camera
  │ CVBS
  ▼
FC CAM input
  │
  │ OSD insertion
  ▼
FC VTX output
  │
  ▼
Analog VTX
  │ 5.8 GHz RF
  ▼
FPV goggles / receiver
```

| Interface | Function | Design status |
|---|---|---|
| Camera supply | Power for camera | Exact camera revision and voltage to verify |
| CVBS | Camera video into FC | Functional path designed; pads to verify |
| OSD/video output | FC video output to VTX | Confirm board revision and video configuration |
| VTX supply | Power for VTX | Exact VTX and FC supply compatibility TBD |
| SmartAudio | VTX configuration, if supported | Confirm both endpoint revisions |

The BETAFPV documentation shows an external analog VTX interface. The Caddx Ant Nano-class camera and AKK Nano3-class VTX remain revision-sensitive selections. Do not infer power compatibility from product-family names alone.

## 4. Radio-control interface

```text
Pilot transmitter
      │ 2.4 GHz RF
      ▼
Integrated Serial ELRS receiver
      │ CRSF (internal FC interface)
      ▼
STM32F411 / Betaflight
```

The selected architecture uses the FC's integrated Serial ELRS receiver. Do not add external receiver wiring unless the actual hardware differs from the selected variant.

## 5. Functional interface summary

| Interface | Direction | Purpose | Verification method |
|---|---|---|---|
| BT2.0 / VBAT | Battery → FC | Power | Polarity and continuity inspection |
| DShot | FC → ESC | Motor command | Props-off motor test |
| 3-phase motor outputs | ESC → motors | Motor drive | Order and direction check |
| CRSF | Receiver → FC | Pilot control | Receiver tab and failsafe test |
| CVBS | Camera → FC | Analog video | Live video |
| Analog video | FC → VTX | Video with OSD | Video and OSD check |
| SmartAudio | FC → VTX | VTX configuration | Verify exact pads and configuration |

## 6. Design status and release checks

| Item | Status | Required evidence |
|---|---|---|
| Functional power architecture | DESIGNED | Exact board revision inspection |
| Motor channel mapping | DESIGNED | Props-off mapping test |
| Camera/video signal path | DESIGNED | Video and OSD test |
| Peripheral power compatibility | TBD | Manufacturer ratings for exact revisions |
| VTX selection | Reference class only | Current source and exact part/revision |
| Pad-level wiring | TBD | Physical board labels and revision-specific documentation |

> **Wiring rule:** this document defines functional intent. It is not a substitute for the pad labels and specifications of the actual hardware.
