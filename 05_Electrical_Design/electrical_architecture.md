# 05 — Electrical Architecture

![Preliminary system wiring concept](images/blueprint_wiring_v1.jpg)

*Figure — Preliminary wiring concept generated during the concept-design phase. The functional architecture below is based on the selected V1 components and manufacturer documentation; exact pad-level wiring must still be checked against the purchased FC revision.*

## 1. Power architecture

```text
1S HV LiPo
   │
   │ BT2.0
   ▼
F4 1S 5A AIO FC
   │
   ├── VBAT → integrated 4-in-1 ESC
   ├── onboard regulation → FC electronics
   ├── 5V → camera / VTX interface
   └── GND common reference
```

The selected BETAFPV FC is designed for 1S operation and includes the ESC on the same PCB. BETAFPV specifies 5 A continuous and 6 A peak ESC current for 3 seconds. The board uses a BT2.0 power cable. [BETAFPV F4 1S 5A AIO documentation](https://betafpv.com/products/f4-1s-5a-aio-brushless-flight-controller-elrs-2-4g)

**Important:** the internal regulator topology is not assumed here. The final board revision must be checked before connecting external loads.

## 2. Propulsion architecture

```text
                 ┌── M1 Front Left
                 ├── M2 Front Right
FC / integrated  ├── M3 Rear Right
4-in-1 ESC ─────┤
                 └── M4 Rear Left
```

Each motor is a 3-phase brushless motor connected to one integrated ESC channel.

The FC supports DShot300 and DShot600 according to BETAFPV. [BETAFPV F4 1S 5A AIO documentation](https://betafpv.com/products/f4-1s-5a-aio-brushless-flight-controller-elrs-2-4g)

Motor numbering and rotation direction will be verified during bring-up with the propellers removed.

## 3. Analog video architecture

```text
Caddx Ant Nano
     │
     │ CVBS analog video
     ▼
FC CAM input
     │
     │ OSD insertion
     ▼
FC VTX output
     │
     ▼
AKK Nano3-class VTX
     │
     │ 5.8 GHz RF
     ▼
FPV goggles / receiver
```

The BETAFPV wiring documentation explicitly shows an external analog VTX interface with **CAM, VTX, GND, +5V and SmartAudio (SA)** connections. It also shows the camera connected through the analog-video path. [BETAFPV F4 1S 5A AIO wiring documentation](https://betafpv.com/products/f4-1s-5a-aio-brushless-flight-controller-elrs-2-4g)

The Caddx Ant Nano is an analog CVBS camera. The exact input-voltage range is revision-dependent, so the purchased camera revision must be checked before final wiring. The referenced EU listing identifies a compact 14 × 14 mm analog camera.

The AKK Nano3-class VTX is retained as a reference architecture. A reference listing specifies 3.2–5.5 V input, 25/200 mW output and SmartAudio. The exact V1 VTX is not frozen until a current Germany/EU source and exact revision are verified. [AKK Nano3 reference specification](https://ledge-team.com/en-gb/VTX/AKK-Nano3-VTX-25-50-100-200mw?limit=15)

## 4. Radio-control architecture

```text
ELRS transmitter
       │
       │ 2.4 GHz RF
       ▼
Integrated Serial ELRS receiver
       │
       │ CRSF
       ▼
STM32F411 / Betaflight
       │
       ▼
Flight-control loop
```

BETAFPV states that the Serial ELRS receiver communicates with the FC using the Crossfire Serial Protocol (CRSF). [BETAFPV F4 1S 5A AIO documentation](https://betafpv.com/products/f4-1s-5a-aio-brushless-flight-controller-elrs-2-4g)

## 5. Complete functional architecture

```text
                    ┌─────────────────────┐
                    │   1S LiPo / BT2.0   │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ F4 1S 5A AIO FC     │
                    │                     │
                    │ STM32F411           │
                    │ BMI270              │
                    │ Serial ELRS         │
                    │ Betaflight OSD      │
                    │ 4-in-1 ESC          │
                    └───┬─────┬─────┬─────┘
                        │     │     │
             DShot ─────┘     │     └──── CRSF
                              │
                        Analog Video
                              │
                 ┌────────────┴────────────┐
                 ▼                         ▼
          Caddx Ant Nano             AKK Nano3
             Camera                     VTX
                 │                         │
                 └──── CVBS / OSD ─────────┘

                    ESC outputs
                 ┌──┬──┬──┬──┐
                 ▼  ▼  ▼  ▼
                M1 M2 M3 M4
```

## 6. Design status

| Interface | Status | Next action |
|---|---|---|
| Battery → FC | DESIGNED | Verify purchased FC revision |
| FC → M1–M4 | DESIGNED | Verify motor numbering |
| Camera → CAM | DESIGNED | Verify exact pads |
| FC → VTX | DESIGNED | Verify VTX/SA pads |
| ELRS → Betaflight | DOCUMENTED | Configure and bench-test |
| DShot → ESC | DOCUMENTED | Verify Betaflight configuration |
| Ground reference | DESIGNED | Continuity check before power-up |

**Rule:** this document defines the intended electrical architecture. It is not a substitute for the pad labels on the physical FC.
