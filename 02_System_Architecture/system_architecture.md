# 02 — System Architecture

<figure>
  <img src="../images/system_architecture.svg" alt="Functional architecture of the 75 mm 1S FPV drone" />
  <figcaption><em>Figure 1 — Functional V1 architecture. This is not a pad-level wiring schematic.</em></figcaption>
</figure>

## System boundary

The V1 system comprises the battery, flight controller and integrated ESC, four motors and propellers, integrated radio receiver, camera, separate analog VTX, and the pilot's external radio/video equipment.

## Subsystems

| Subsystem | Main elements | Responsibility |
|---|---|---|
| Power | 1S HV LiPo, BT2.0, FC power circuitry | Supply electrical energy |
| Flight control | STM32F411, BMI270, Betaflight | Estimate motion and calculate motor corrections |
| Propulsion | Integrated 4-in-1 ESC, four 0802 motors, props | Convert motor commands into thrust |
| Radio control | Integrated 2.4 GHz Serial ELRS | Deliver pilot commands to Betaflight |
| Video | Caddx Ant Nano-class camera, OSD path, separate analog VTX | Deliver analog FPV video to goggles |
| Configuration/logging | USB, Betaflight Configurator, Blackbox | Configure, diagnose and record system behavior |

## Primary interfaces

| Source | Interface / signal | Destination | Purpose | Verification |
|---|---|---|---|---|
| Battery | BT2.0 / VBAT / GND | FC | Power input | Polarity and continuity inspection |
| FC | DShot motor outputs | Integrated ESC | Motor commands | Props-off motor test |
| ESC | Three-phase outputs | M1–M4 | Motor drive | Motor order and direction check |
| ELRS receiver | Internal CRSF interface | Betaflight | Pilot commands and telemetry | Receiver tab and failsafe test |
| Camera | CVBS | FC CAM input | Analog video input | Live video check |
| FC OSD path | Analog video output | VTX | Video with OSD insertion | Video and OSD check |
| FC | SmartAudio, where supported | VTX | VTX configuration | Confirm against exact board/VTX revisions |

## Design constraints and assumptions

- The architecture is frozen at the functional level; exact purchased revisions and pad-level wiring remain subject to inspection.
- The selected FC family combines the STM32F411, BMI270, Serial ELRS and 1S 4-in-1 ESC.
- The camera's exact supply range and the VTX's exact part/revision must be verified before final wiring.
- Motor numbering and rotation direction must be confirmed in the configured firmware.
- The diagram communicates functional relationships; use the electrical-design documents and manufacturer documentation for wiring.

## Status

| Item | Status | Evidence required to close |
|---|---|---|
| Functional subsystem architecture | DESIGNED | Review against procured hardware |
| Battery and propulsion interfaces | DESIGNED | Inspect board and verify wiring |
| Receiver interface | DOCUMENTED | Bind and verify channel/failsafe behavior |
| Analog video path | DESIGNED | Verify video and OSD on assembled hardware |
| Physical system integration | NOT YET VERIFIED | Completed bring-up record |
