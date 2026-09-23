# 02 — System Architecture

```text
                         1S LiPo
                            │
                         BT2.0
                            │
                            ▼
                 ┌─────────────────────┐
                 │ F4 1S 5A AIO FC     │
                 │ STM32F411           │
                 │ BMI270 IMU          │
                 │ Serial ELRS         │
                 │ 1S 4-in-1 ESC       │
                 │ Betaflight / OSD    │
                 └──────┬─────┬────────┘
                        │     │
                  Propulsion  Video
                        │     │
                   M1 M2 M3 M4
                              │
                       Analog Camera
                              │
                       FC OSD path
                              │
                       Analog VTX
                              │
                       FPV receiver

Radio transmitter
       │
   2.4 GHz ELRS
       ▼
Integrated ELRS receiver
       │
      CRSF
       ▼
    Betaflight
```

## Subsystems
- **Flight control:** MCU, IMU, Betaflight, integrated receiver and 1S ESC.
- **Propulsion:** four independent ESC outputs driving four 0802 motors.
- **Radio:** integrated Serial ELRS receiver.
- **Video:** analog camera + separate analog VTX.
- **Configuration:** USB / Betaflight Configurator; blackbox/configuration artifacts retained where supported.

Every electrical interface will be documented as: **source → signal → destination → direction → purpose → verification method**.
