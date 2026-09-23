# System Interfaces

| Interface | Source | Destination | Type | Verification |
|---|---|---|---|---|
| PWR-01 | 1S LiPo | AIO FC | VBAT/GND | Polarity + voltage |
| MOT-01..04 | AIO ESC | Motors | 3-phase | Individual motor test |
| CAM-01 | Camera | FC CAM | CVBS | Video test |
| VTX-01 | FC VTX | Analog VTX | CVBS | Video test |
| VTX-02 | FC SA | Analog VTX | SmartAudio | Control test if supported |
| RX-01 | Integrated ELRS | Betaflight | CRSF | Channel/failsafe test |
| CFG-01 | USB | FC | Configuration/MSP | USB connection |
| DBG-01 | FC blackbox | Onboard flash | Flight data | Log extraction |

Functional signal names are documented here. Exact GPIO numbers and pad names are not invented until the physical FC revision is identified.
