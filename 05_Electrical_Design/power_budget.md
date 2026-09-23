# Power Budget

This is a planning document, not a measured electrical budget.

## Power domains
| Domain | Source | Status |
|---|---|---|
| Battery/VBAT | 1S HV LiPo | Defined |
| FC/ESC | AIO board | Defined |
| Camera rail | FC peripheral rail | Verify on final board |
| VTX rail | FC peripheral rail | Verify on final board |
| Receiver | Integrated | Defined |

## Measurement plan
Measure during bring-up:
- battery voltage at rest
- battery voltage under load if instrumentation is available
- FC reported voltage
- total current where a suitable inline/current method exists
- post-flight motor/FC/VTX temperature observations

Do not derive flight-time or current claims from nominal component specifications alone.
