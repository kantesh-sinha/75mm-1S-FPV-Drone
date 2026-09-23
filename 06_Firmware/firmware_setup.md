# Betaflight Setup

## Version policy
The FC manufacturer identifies a board-specific Betaflight target. Record the firmware currently installed on the physical FC before changing it.

BETAFPV documentation for the F4 1S 5A Serial ELRS board identifies the BETAFPVF411 family and notes BMI270 compatibility requirements for older firmware generations.

Current Betaflight documentation also notes that DShot300 is suitable for F411/BMI270 combinations.

## Setup sequence
1. Connect FC by USB with propellers removed.
2. Record board target and firmware version.
3. Save a configuration backup.
4. Confirm gyro/accelerometer detection.
5. Confirm board orientation.
6. Configure receiver.
7. Configure motor protocol.
8. Verify motor order and direction with props removed.
9. Configure OSD.
10. Configure VTX control if supported.
11. Configure and test failsafe.
12. Save final configuration.

Do not copy a CLI dump from another board revision without checking its target and hardware mapping.
