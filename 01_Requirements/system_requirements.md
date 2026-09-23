# System Requirements

## Mission profile
The V1 vehicle is a 75 mm-class 1S analog FPV quad intended for indoor and light outdoor operation.

## Functional requirements
| ID | Requirement | Verification method |
|---|---|---|
| SYS-F-001 | Four independently controlled brushless motors | Motor test |
| SYS-F-002 | 1S LiPo power through BT2.0 | Inspection + voltage test |
| SYS-F-003 | Pilot control through integrated Serial ELRS | Receiver/channel test |
| SYS-F-004 | Analog FPV video | Camera/VTX test |
| SYS-F-005 | Betaflight stabilization | FC/flight test |
| SYS-F-006 | Configurable failsafe behavior | Controlled failsafe test |
| SYS-F-007 | Reproducible firmware/configuration records | Configuration archive |

## Performance requirements
Performance values are targets until measured.
- Flight time: measure rather than claim.
- Hover stability: demonstrate by controlled flight.
- Video usability: demonstrate with the selected receiver.
- Radio link: characterize in the intended test environment.
- Thermal behavior: inspect after repeated flights.

## Safety requirements
- Propellers removed during bench motor testing.
- No firmware flashing with propellers installed.
- Battery polarity checked before first power-up.
- Failsafe verified before flight.
- First flight performed in a controlled area.

Numerical performance limits will be added only when justified by measured data or a documented engineering requirement.
