# Research Notes

## Manufacturer evidence

BETAFPV's current F4 1S 5A Serial ELRS documentation identifies STM32F411CEU6, BMI270, integrated Serial ELRS 2.4 GHz, 26 × 26 mm mounting, integrated 1S ESC, 5 A continuous / 6 A peak for 3 seconds, DShot300/DShot600, 8 MB blackbox and external analog VTX support.

Source:
https://betafpv.com/products/f4-1s-5a-aio-brushless-flight-controller-elrs-2-4g

BETAFPV's Meteor75 documentation provides a closely related reference architecture using 75 mm, 0802 motors, 40 mm props, BT2.0 450 mAh 1S and the F4 1S 5A Serial ELRS FC.

Source:
https://betafpv.com/products/meteor75-brushless-whoop-quadcopter-1s

## Betaflight evidence

Current Betaflight documentation identifies DShot300 as a suitable combination for F411/BMI270-class hardware and documents CLI, motor testing, arming safety, failsafe and Blackbox procedures.

Sources:
https://betaflight.com/docs/wiki/getting-started/setup-guide
https://betaflight.com/docs/wiki/app/configuration-tab
https://betaflight.com/docs/wiki/guides/current/Cli
https://betaflight.com/docs/wiki/guides/current/Safety
https://betaflight.com/docs/wiki/guides/current/Failsafe
https://betaflight.com/docs/wiki/guides/current/Black-Box-logging-and-usage

## ExpressLRS evidence

ExpressLRS documents CRSF as the serial receiver protocol and describes Serial RX configuration through the FC configuration interface.

Source:
https://www.expresslrs.org/quick-start/receivers/configuring-fc/

## Germany / EU procurement evidence

FPV24 currently lists a BetaFPV 0802 22000KV motor set and provides part-level specifications including 1S operation, 1.0 mm shaft and 1.88 g per motor.

Source:
https://www.fpv24.com/en/betafpv/betafpv-0802-22000kv-fpv-motor-freestyle-4-pieces

FPV24 currently lists Caddx Ant analog nano cameras with CVBS output, 14 × 14 mm dimensions and 3.7–18 V input for the listed revision.

Source:
https://www.fpv24.com/en/caddx/caddx-ant-1200tvl-wdr-43-ultra-light-nano-fpv-camera-black

FPV24 currently lists BetaFPV 450 mAh 1S BT2.0 batteries.

Source:
https://www.fpv24.com/en/betafpv/betafpv-lipo-bt2-0-450mah-1s-30c-4-stueck

Availability and price are time-dependent and are not frozen into the engineering design.

## Community evidence

Reddit tiny-whoop discussions show 0802 motors are commonly used on 75 mm / 40 mm builds, with users discussing trade-offs between 0802, larger motors, prop blade count and outdoor performance.

Examples:
https://www.reddit.com/r/TinyWhoop/comments/1l34k4z
https://www.reddit.com/r/TinyWhoop/comments/1cjsii0

Community discussion is practical experience, not a substitute for manufacturer specifications or measurements.


## VTX sourcing risk

AKK's current official site states that AKK stopped exporting VTX products on September 1, 2024 and warns about third-party clones. Therefore, the AKK Nano3 should be treated as an architecture/specification reference rather than a guaranteed V1 procurement part.

Source:
https://www.akktek.com/akk-race-vtx.html

This does not change the V1 requirement for a **separate analog VTX**. It means the exact V1 VTX must be selected from a currently available, revision-identified source before the BOM is frozen.
