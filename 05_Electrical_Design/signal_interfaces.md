# Signal Interfaces

This document defines the logical interfaces between the major electrical subsystems.

| Interface | Source | Destination | Signal | Electrical role | Status |
|---|---|---|---|---|---|
| Power | 1S LiPo | FC | VBAT, GND | DC power | DESIGNED |
| Motor 1 | FC ESC1 | 0802 motor | 3-phase | Motor drive | DESIGNED |
| Motor 2 | FC ESC2 | 0802 motor | 3-phase | Motor drive | DESIGNED |
| Motor 3 | FC ESC3 | 0802 motor | 3-phase | Motor drive | DESIGNED |
| Motor 4 | FC ESC4 | 0802 motor | 3-phase | Motor drive | DESIGNED |
| Camera power | FC | Caddx Ant Nano | 5V, GND | Camera supply | DESIGNED |
| Camera video | Caddx Ant Nano | FC | CVBS | Analog video | DESIGNED |
| VTX power | FC | AKK Nano3 | 5V, GND | VTX supply | DESIGNED |
| VTX video | FC | AKK Nano3 | Video | Analog video | DESIGNED |
| VTX control | FC | AKK Nano3 | SmartAudio | VTX configuration | DESIGNED |
| Radio | Integrated ELRS RX | Betaflight | CRSF | RC control data | DOCUMENTED |
| FC → ESC | STM32/FC | Integrated ESC | DShot | Motor command | DOCUMENTED |

## Interface notes

### Power

The FC is a 1S AIO design. Battery power enters the FC through the BT2.0 connection and feeds the integrated ESC and onboard electronics.

### Motors

Each motor is a 3-phase brushless motor. Individual phase-wire order does not need to be predetermined in the documentation; rotation direction is verified after Betaflight/ESC configuration.

### Analog video

The camera produces CVBS analog video. The FC inserts Betaflight OSD information and sends the resulting analog video signal to the VTX.

### SmartAudio

SmartAudio is a control interface used to configure VTX parameters such as channel and transmit power. It is separate from the analog video signal.

### CRSF

CRSF is the serial protocol used between the integrated Serial ELRS receiver and the flight controller.

## Verification rule

Pad names and UART assignment must be taken from the exact FC revision being assembled. Do not infer a physical pad from this logical interface table alone.
