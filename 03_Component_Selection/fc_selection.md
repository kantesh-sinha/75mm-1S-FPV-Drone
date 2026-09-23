# Flight Controller Selection

## Selected architecture
BETAFPV F4 1S 5A AIO-class board with Serial ELRS.

BETAFPV currently documents an STM32F411CEU6, BMI270, integrated Serial ELRS 2.4 GHz receiver, 26 × 26 mm mounting pattern, integrated 1S ESC, 5 A continuous / 6 A peak ESC specification, and DShot300/600 support.

Source: https://betafpv.com/products/f4-1s-5a-aio-brushless-flight-controller-elrs-2-4g

## Why it fits V1
- Integrates flight controller and 1S 4-in-1 ESC.
- Removes the need for a separate receiver.
- Retains an analog-VTX interface.
- Uses an STM32F411 and BMI270.
- Avoids a custom PCB in V1.

## Revision-control rule
BETAFPV has multiple F4 1S 5A revisions and firmware targets. The purchased board revision and its manufacturer documentation are authoritative. Do not flash or wire from a generic internet pinout.
