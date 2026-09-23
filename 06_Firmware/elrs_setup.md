# ExpressLRS Setup

## Signal path
Integrated ELRS 2.4 GHz receiver → CRSF → Betaflight.

ExpressLRS documentation specifies CRSF as the serial receiver protocol for UART-based ELRS receivers.

## Bench procedure
1. Power the FC safely.
2. Confirm the receiver is detected.
3. Bind the transmitter and receiver.
4. Open the Receiver tab.
5. Confirm roll, pitch, yaw and throttle channels move correctly.
6. Confirm channel endpoints.
7. Configure an arm switch.
8. Configure a failsafe procedure.
9. Test loss-of-signal behavior without propellers installed.

The exact integrated receiver implementation depends on the FC revision and should be recorded with the hardware revision.
