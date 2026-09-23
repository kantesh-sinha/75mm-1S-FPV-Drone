# 75 mm 1S Analog FPV Drone

<img width="1024" height="1024" alt="image" src="https://github.com/user-attachments/assets/24a9a99e-3ddb-4a22-b2e2-525d79fcd1f4" />


Engineering design, integration and validation of a 75 mm 1S analog FPV micro quadcopter.

> **Project status:** V1 architecture frozen · Electronics documentation in progress · Physical build not yet validated

## Project goal

Build a small, reproducible FPV quadcopter as an engineering demonstrator, with the emphasis on:

- embedded electronics
- system architecture
- hardware/software integration
- firmware configuration
- electrical interfaces
- verification and validation
- clear build documentation

Mechanical design is intentionally kept simple. The project is not primarily a custom-frame or 3D-printing exercise.

## Engineering workflow

**01 Requirements → 02 Architecture → 03 Component Selection → 04 BOM → 05 Electrical Design → 06 Firmware → 07 Integration → 08 Verification → 09 Validation → 10 Iterations**

The intended development model is a V-model:

```text
SYSTEM REQUIREMENTS
        │
        ▼
SYSTEM ARCHITECTURE
        │
        ▼
SUBSYSTEM / ELECTRICAL DESIGN
        │
        ├──────────────┐
        ▼              ▼
   HARDWARE         FIRMWARE
        │              │
        └──────┬───────┘
               ▼
           INTEGRATION
               │
               ▼
          VERIFICATION
               │
               ▼
           VALIDATION
               │
               ▼
        FLIGHT / SYSTEM TEST
               │
               ▼
       LESSONS LEARNED
               │
               ▼
           ITERATION
```

## V1 system at a glance

| Subsystem | V1 target |
|---|---|
| Platform | 75 mm micro quad |
| Power | 1S LiPo HV, ~450 mAh |
| Connector | BT2.0 |
| Flight controller | BETAFPV F4 1S 5A AIO-class |
| MCU | STM32F411 |
| IMU | BMI270 |
| Receiver | Integrated Serial ELRS 2.4 GHz |
| ESC | Integrated 1S 4-in-1 ESC |
| Motors | 4 × 0802, ~22,000 KV |
| Propellers | 40 mm, 3-blade |
| Camera | Caddx Ant Nano |
| Video | Analog FPV |
| VTX | Separate AKK Nano3-class |
| Firmware | Betaflight |

## Repository map

| Folder | Purpose |
|---|---|
| [01_Requirements](01_Requirements/) | Mission, constraints and requirements |
| [02_System_Architecture](02_System_Architecture/) | System and subsystem architecture |
| [03_Component_Selection](03_Component_Selection/) | Hardware choices and trade-offs |
| [04_BOM](04_BOM/) | Reproducible parts list and sourcing |
| [05_Electrical_Design](05_Electrical_Design/) | Power, wiring and interfaces |
| [06_Firmware](06_Firmware/) | Betaflight and ELRS configuration |
| [07_Integration](07_Integration/) | Assembly, wiring and bring-up |
| [08_Verification](08_Verification/) | Requirements verification and bench tests |
| [09_Validation](09_Validation/) | Flight/system validation |
| [10_Iterations](10_Iterations/) | Design evolution and lessons learned |
| [11_Mechanical](11_Mechanical/) | Supporting frame/CAD information |
| [12_References](12_References/) | Datasheets, manufacturer documentation and research |

## Status convention

- **DESIGNED** — selected or specified as part of the V1 design
- **VERIFIED** — confirmed against documentation, hardware inspection or configuration
- **MEASURED** — experimentally measured on the physical system

A design value is not presented as a measured result.

## Build path

1. Read the requirements.
2. Understand the system architecture.
3. Review component selection.
4. Build the BOM.
5. Follow the electrical documentation.
6. Configure firmware.
7. Perform staged bring-up.
8. Run verification tests.
9. Perform flight validation.
10. Record measured results and update the iteration log.

## Current limitations

The documentation is being built from the preliminary Blueprint design package and manufacturer documentation. Exact FC revision, firmware target, pin mapping, VTX revision and final sourced part numbers must be verified before physical assembly.

## Design origin

Blueprint.io was used to generate the initial concept, preliminary BOM, wiring concept and build sequence. This repository separates that generated starting point from subsequent engineering verification and measured results.
