# 03 — Component Selection

| Subsystem | V1 selection | Reason |
|---|---|---|
| FC | BETAFPV F4 1S 5A AIO-class | FC + 1S ESC + Serial ELRS in one board |
| Receiver | Integrated Serial ELRS | Less wiring and fewer parts |
| Motors | 0802 ~22,000 KV ×4 | 75 mm 1S propulsion class |
| Props | 40 mm 3-blade | Matches target architecture |
| Battery | 1S ~450 mAh BT2.0 | 1S ecosystem / manageable mass |
| Camera | Caddx Ant Nano | Compact analog FPV |
| VTX | Separate analog VTX, AKK Nano3-class reference | Keeps video subsystem independently visible/testable; exact V1 part TBD pending EU sourcing |
| Frame | Commercial 75 mm class | Keeps V1 focused on electronics |

## Design trade-off
A newer integrated video/5-in-1 platform could reduce wiring and mass. V1 intentionally retains a separate analog VTX so the video subsystem remains independently visible and testable.

Exact revisions and final Germany/EU sources will be frozen in the BOM after verification. AKK Nano3 is a reference class, not a locked procurement part.
