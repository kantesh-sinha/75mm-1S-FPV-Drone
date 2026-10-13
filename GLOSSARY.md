# FPV Drone Engineering Glossary

This glossary collects the core terms used in the 75 mm 1S FPV drone project. For the project-specific implementation, always defer to the exact purchased hardware revision and the relevant design documents.

## Core terms

Use this section as a reference while reading the repository.

### 5.1 Flight Controller (FC)

The **flight controller** is the computer that stabilizes the drone.

In this project it contains:

- STM32F411 microcontroller
- BMI270 inertial sensor
- Betaflight firmware
- integrated Serial ELRS receiver
- integrated 4-in-1 ESC
- analog OSD/video interface
- Blackbox memory

Think of the FC as the central embedded computer.

### 5.2 MCU

**MCU = Microcontroller Unit.**

It is the processor executing the flight-control firmware.

The selected FC uses an **STM32F411CEU6**. [BETAFPV F4 1S 5A AIO Serial ELRS documentation](https://betafpv.com/products/f4-1s-5a-aio-brushless-flight-controller-elrs-2-4g)

### 5.3 IMU

**IMU = Inertial Measurement Unit.**

It measures motion-related quantities such as acceleration and angular rate.

The FC uses this information to determine how the aircraft is moving.

The selected FC uses a **BMI270**. [BETAFPV F4 1S 5A AIO Serial ELRS documentation](https://betafpv.com/products/f4-1s-5a-aio-brushless-flight-controller-elrs-2-4g)

### 5.4 ESC

**ESC = Electronic Speed Controller.**

An ESC converts the flight controller's motor command into electrical switching signals that drive a brushless motor.

This project uses an **AIO FC**, meaning the flight controller and ESC electronics are integrated onto one board.

~~~
Betaflight
    │
    │ motor command
    ▼
ESC
    │
    │ 3-phase switching
    ▼
Brushless motor
    │
    ▼
Propeller
~~~

### 5.5 AIO

**AIO = All-In-One.**

Here it means the flight controller and 4-in-1 ESC are integrated on the same PCB.

It does **not** mean all drone electronics are on one PCB. The camera and analog VTX remain separate.

### 5.6 KV

Motor KV is approximately the motor's no-load rotational-speed constant, expressed in RPM per volt.

A **22,000 KV** motor therefore belongs to a very high-RPM micro-drone motor class.

KV does **not** directly mean motor power.

Actual performance depends on motor construction, voltage, propeller, battery, current capability, aircraft mass and aerodynamic load.

Therefore this repository does not claim flight performance from KV alone.

### 5.7 1S

**1S means one lithium-cell series configuration.**

A conventional 1S LiPo is approximately 3.7 V nominal and 4.2 V when fully charged.

This project uses a 1S architecture to keep the system small and simple.

### 5.8 mAh

**mAh = milliampere-hour.**

It describes battery capacity.

A 450 mAh battery can theoretically supply 450 mA for one hour under idealized conditions.

Real flight time is not calculated directly from mAh because current consumption changes continuously.

Therefore:

> **Flight time is a measured result in this repository, not a guessed specification.**

### 5.9 BT2.0

BT2.0 is the battery connector used by the selected architecture.

It provides the physical electrical connection between the battery and drone.

### 5.10 ELRS

**ExpressLRS (ELRS)** is the radio-control link used between the pilot's transmitter and aircraft.

This project uses an **integrated 2.4 GHz Serial ELRS receiver**.

~~~
Pilot transmitter
      │
      │ 2.4 GHz RF
      ▼
Integrated ELRS receiver
      │
      │ CRSF
      ▼
Flight controller
~~~

ExpressLRS documents CRSF as the serial protocol used between UART-based receivers and the flight controller. [ExpressLRS receiver/FC configuration documentation](https://www.expresslrs.org/quick-start/receivers/configuring-fc/)

### 5.11 CRSF

**CRSF = Crossfire Serial Protocol.**

It is the serial communication protocol used to transfer receiver/control information between an ELRS receiver and flight controller.

Do not confuse:

- **ELRS** → radio link technology
- **CRSF** → serial communication protocol between receiver and FC

### 5.12 Betaflight

**Betaflight** is the flight-controller firmware/configuration ecosystem used in this project.

It handles functions including:

- sensor processing
- stabilization
- motor mixing
- receiver input
- arming
- failsafe
- OSD
- motor output
- Blackbox logging
- configuration

The Betaflight setup guide recommends configuring and testing failsafe and performing bench checks without propellers before flight. [Betaflight Setup Guide](https://betaflight.com/docs/wiki/getting-started/setup-guide)

### 5.13 PID

**PID = Proportional, Integral, Derivative.**

A PID controller compares desired aircraft motion with measured motion and calculates a correction.

~~~
Desired attitude
      │
      ▼
    ERROR ◄──── Measured attitude
      │
      ▼
    PID
      │
      ▼
Motor corrections
~~~

You do not need to tune PID values to understand the first build.

For V1, the priority is:

**correct hardware → correct configuration → safe flight → measurements → tuning.**

### 5.14 DShot

**DShot** is a digital protocol used to communicate motor commands from the flight controller to compatible ESCs.

The selected FC supports DShot300 and DShot600. [BETAFPV F4 1S 5A AIO Serial ELRS documentation](https://betafpv.com/products/f4-1s-5a-aio-brushless-flight-controller-elrs-2-4g)

### 5.15 Analog FPV

Analog FPV sends the camera image as an analog video signal.

The V1 signal chain is:

~~~
Camera
  │
  │ CVBS
  ▼
FC CAM input
  │
  │ OSD insertion
  ▼
FC VTX output
  │
  ▼
Analog VTX
  │
  │ 5.8 GHz RF
  ▼
FPV goggles / receiver
~~~

**CVBS** is the analog composite video signal.

### 5.16 VTX

**VTX = Video Transmitter.**

It converts the camera/video signal into a radio-frequency transmission for the FPV receiver.

The project intentionally uses a **separate VTX**. This adds some wiring and weight, but makes the video subsystem visible and independently testable.

### 5.17 OSD

**OSD = On-Screen Display.**

The flight controller can insert information such as battery voltage, flight time and warnings into the analog video stream.

Therefore:

~~~
Camera → FC → OSD → VTX
~~~

### 5.18 Blackbox

**Blackbox** is flight-controller logging.

It records internal flight data for troubleshooting, control analysis, filtering analysis, vibration investigation, tuning and post-flight engineering review.

The selected BETAFPV FC is documented with 8 MB Blackbox memory. [BETAFPV F4 1S 5A AIO Serial ELRS documentation](https://betafpv.com/products/f4-1s-5a-aio-brushless-flight-controller-elrs-2-4g)

### 5.19 Failsafe

Failsafe defines what the aircraft does when radio control is lost.

It is not an optional feature to ignore until the end.

Betaflight documents multiple failsafe stages and explicitly requires failsafe testing before flight. [Betaflight Failsafe documentation](https://betaflight.com/docs/wiki/guides/current/Failsafe)

For this project:

> **No first flight until failsafe behavior has been configured and bench-tested.**

---

## Project-specific cautions

- KV is not a direct measure of motor power or flight performance.
- Battery capacity in mAh does not by itself determine flight time.
- ELRS is the radio link; CRSF is the serial protocol used between the receiver and flight controller.
- An AIO flight controller integrates the FC and ESC, not necessarily the camera or VTX.
- Treat pad maps, motor order, firmware target and voltage compatibility as revision-specific facts to verify, not assumptions.
