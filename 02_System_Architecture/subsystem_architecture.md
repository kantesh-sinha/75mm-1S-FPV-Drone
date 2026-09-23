# Subsystem Architecture

## Flight-control subsystem
Inputs: BMI270 inertial measurements, Serial ELRS receiver data, and battery information where available.

Processing: STM32F411, Betaflight estimation/control loop, mixer and safety/failsafe logic.

Outputs: four ESC motor commands, analog-video OSD path, and VTX control where supported.

## Propulsion subsystem
Betaflight → DShot → integrated 4-in-1 ESC → M1..M4.

Each motor is an independent three-phase brushless load.

## Radio subsystem
2.4 GHz ELRS RF → integrated Serial ELRS receiver → CRSF → Betaflight.

## Video subsystem
Caddx Ant Nano → CVBS → FC CAM input → OSD → FC VTX output → analog VTX → 5.8 GHz.

## Power subsystem
1S LiPo → BT2.0 → AIO FC/ESC → regulated peripheral rails.

The exact regulator topology is not inferred; final pad-level connections are controlled by the purchased FC revision.
