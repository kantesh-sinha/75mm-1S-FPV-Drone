# Test Procedures

## T02 — Power continuity
Condition: battery disconnected.
1. Inspect VBAT and GND paths.
2. Measure resistance/continuity with the available meter.
3. Investigate any unexpected low-resistance path before connecting the battery.

## T04 — FC USB
1. Connect USB.
2. Confirm the FC appears in Betaflight.
3. Record target and firmware.
4. Record sensor detection.

## T06 — ELRS binding
1. Follow the documented binding procedure.
2. Confirm successful bind.
3. Confirm receiver data in Betaflight.
4. Record channel values.

## T09–T12 — Motor outputs
Props removed. Test one motor at a time. Confirm physical motor identity, smooth operation and direction. Stop for abnormal noise, heat or stuttering.

## T14–T17 — Video
Confirm camera power, analog image, OSD insertion, VTX output and SmartAudio control where supported.

## T18 — Arming
Verify intended arming conditions and confirm the quad cannot arm under an active failsafe or other safety lockout.

## T20 — Flight time
Record battery start voltage, takeoff timestamp, landing/disarm timestamp, battery end voltage, battery identifier, flight style and environmental conditions.
