# Project review and next development steps

This page is the working release checklist. It separates documentation readiness from a physically demonstrated aircraft.

## Current baseline

- Functional V1 architecture: frozen.
- Hardware procurement: exact VTX and revision-sensitive peripherals remain open.
- Pad-level wiring: not released for build until checked against the exact purchased board revisions.
- Firmware: Betaflight configuration is planned; no configuration dump is treated as a verified baseline.
- Physical assembly, bench verification and flight validation: pending.

## Release gates

| Gate | Work | Evidence required | Exit condition |
|---|---|---|---|
| G0 — Parts freeze | Record exact manufacturer part numbers, revisions, EU sources and datasheets | BOM with links, revision and price/date | All electrically critical parts identified |
| G1 — Electrical release | Reconcile FC, camera and VTX pad maps, supply ranges and signal levels | Revision-specific wiring diagram and interface table | No unresolved power or signal compatibility |
| G2 — Bench bring-up | Inspect, check continuity, power FC, configure receiver and video | Photos, Betaflight dump, test records | All props-off checks pass |
| G3 — Flight readiness | Verify motor mapping, arming, disarming and failsafe | Completed safety checklist and test evidence | All required safety checks pass |
| G4 — Mission validation | Conduct controlled hover and mission tests | Blackbox logs, flight conditions and measured results | Mission criteria evaluated against recorded data |

## Improvements to make during implementation

1. Replace class-level BOM entries with exact part numbers and revision identifiers as parts are selected.
2. Create one revision-specific wiring drawing. Keep the Blueprint concept image clearly marked as preliminary.
3. Record the Betaflight target, firmware version, configuration dump and CLI diff after the actual FC is available.
4. Add test records with raw evidence rather than marking planned procedures as complete.
5. Record all-up weight, current, battery voltage sag, temperature and flight time only from measurements, including test conditions.
6. Keep each design change traceable to a problem, evidence, decision and retest.

## Definition of done

The project is not complete merely because the aircraft powers on. V1 completion requires an identified hardware baseline, reproducible assembly/configuration instructions, passed bench checks, documented first-flight safety checks and mission-validation results. Any untested item remains explicitly open.
