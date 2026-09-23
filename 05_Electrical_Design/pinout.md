# FC Pin / Pad Mapping

## Scope

This is the **functional pin map** for the V1 design. It deliberately does not invent STM32 GPIO numbers where the manufacturer documentation does not expose them.

The selected BETAFPV F4 1S 5A AIO Serial ELRS board provides the interfaces required for the project: integrated Serial ELRS, four integrated ESC channels, analog VTX support, OSD and BT2.0 power input. citeturn2view0turn3view0

## Functional mapping

| FC interface / pad function | Connected subsystem | Signal |
|---|---|---|
| VBAT / BAT+ | 1S LiPo | Battery positive |
| GND | Battery + all peripherals | Common ground |
| ESC/M1 | Motor 1 | DShot / ESC control |
| ESC/M2 | Motor 2 | DShot / ESC control |
| ESC/M3 | Motor 3 | DShot / ESC control |
| ESC/M4 | Motor 4 | DShot / ESC control |
| 5V | Caddx Ant Nano | Camera supply |
| GND | Caddx Ant Nano | Camera ground |
| CAM | Caddx Ant Nano | CVBS video into FC |
| VTX | AKK Nano3 | Analog video out |
| 5V | AKK Nano3 | VTX supply |
| GND | AKK Nano3 | VTX ground |
| SA / SmartAudio | AKK Nano3 | VTX control |
| Integrated Serial ELRS | Radio receiver | CRSF |

BETAFPV's published analog-VTX diagram labels the external analog-VTX interface as CAM, VTX, GND, +5V and SA, and shows the camera in the same video chain. citeturn3view0

## UART assignment

For the published F4 1S 5A AIO wiring example, **UART2 is used for the VTX SmartAudio peripheral**. The documentation also distinguishes UART configuration depending on receiver architecture. citeturn3view0

For this project:

- **UART2 / VTX peripheral:** intended for SmartAudio, subject to exact FC revision verification.
- **Integrated Serial ELRS:** receiver interface is internal to the selected board and uses CRSF.
- **UART1:** do not assign additional peripherals until the exact purchased FC revision and Betaflight target are confirmed.

## What is intentionally not specified

The following are **TBD until the physical FC is inspected**:

- STM32F411 GPIO number for each external pad
- exact TX/RX pad labels on the purchased board
- exact camera/VTX pad location
- exact UART resource mapping in the installed Betaflight target
- exact firmware target/version

This avoids turning a documentation diagram from a different FC revision into a false pinout.

## Bring-up check

Before applying battery power:

1. Identify the exact FC revision.
2. Photograph the top and bottom of the FC.
3. Record every pad label.
4. Compare the physical board against the manufacturer diagram.
5. Update this table with the verified pad names.
6. Check continuity between intended grounds.
7. Power the FC without motors/camera/VTX first.
