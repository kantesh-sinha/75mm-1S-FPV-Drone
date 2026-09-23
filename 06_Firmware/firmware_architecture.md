# 06 — Firmware

## Stack
```text
Hardware
   ↓
STM32F411
   ↓
Betaflight
   ├─ IMU
   ├─ Receiver / CRSF
   ├─ Mixer
   ├─ PID control
   ├─ Motor outputs
   ├─ OSD
   ├─ VTX control
   ├─ Failsafe
   └─ Blackbox
```

## Firmware separation
Track separately:
1. Flight-controller firmware/configuration
2. Integrated ELRS receiver firmware/configuration

## Bring-up
1. Identify exact FC revision.
2. Connect USB.
3. Record existing Betaflight target/version.
4. Back up configuration.
5. Verify gyro/IMU.
6. Flash only a verified target if required.
7. Configure receiver and bind ELRS.
8. Configure motor mapping/direction.
9. Configure OSD/VTX.
10. Configure failsafe.
11. Save final configuration backup.

No firmware version is claimed as tested until the physical FC is available.
