# MP-1 Electrical Bench Test — 2026-09-07

**Status:** In progress

## Objective

Verify the Meadowlark Platform 1 (MP-1) electrical power architecture and establish baseline measurements before permanent wiring and propulsion testing.

## Safety Configuration

- Propeller removed for all initial electrical testing.
- High-current battery power connections use proper RC connectors/harnesses, not exposed alligator clips.
- Alligator clips may be used for low-current measurement connections only.
- Power is removed before changing wiring unless a specific energized measurement requires otherwise.

## Test Configuration

- Flight battery: Spektrum SPMX54S50H5 Smart G2 LiPo, 5000 mAh, 4S, 14.8 V nominal, 50C, IC5
- Battery state: Fully charged before test
- Charger used: Spektrum S2100 SPMXC1010, OS 1.1.0.17
- Flight controller: Holybro Pixhawk 6C Mini
- Power module: Holybro PM02 V3
- ESC: Hobbywing Skywalker 50A V2
- Motor: T-Motor F90 2806.5 1300KV
- Servos: EMAX ES3059MD digital metal gear, three planned for installation
- Multimeter: TESMEN TM-510

## Bench Measurements

| Test | Expected / Reference | Measured | Result | Notes |
|---|---|---:|---|---|
| Battery voltage, unloaded | Approximately 16.8 V when fully charged | 16.63 V | PASS | Fully charged pack after resting; normal value |
| Battery polarity | Correct | Positive 16.63 V with red probe on + and black probe on − | PASS | Confirms expected terminal polarity |
| PM02 V3 input voltage | Near battery voltage | TBD | TBD | |
| PM02 V3 output voltage, unloaded | Near battery voltage | 15.84 V | PASS | Measured several days after initial full-charge battery reading; output is consistent with present pack voltage |
| Pixhawk supply voltage | 5 V-class regulated supply | 5.31 V | PASS | Measured at PM02 V3 6-pin Pixhawk power output with Pixhawk disconnected |
| Pixhawk power-on / boot indication | Stable powered state with processor activity | I/O: PWR solid green, B/E flashing orange, ACT flashing blue; FMU: PWR solid green, ACT flashing blue, B/E off | PASS | Power and processor activity observed |
| Mission Planner USB connection | Flight controller enumerates and establishes MAVLink connection | Connected successfully | PASS | Initial software-level communication with Pixhawk over USB |
| ArduPlane 4.6.3 boot, no microSD | Mission Planner connects and identifies fixed-wing vehicle | COM6 connected; FIXED WING | PASS | Pixhawk6C target, ArduPlane 4.6.3; microSD removed. I/O PWR green, B/E off, ACT flashing blue. FMU PWR green, ACT off, B/E red flashing pattern. Despite LED pattern, MAVLink connection and fixed-wing identification confirm application is running. |
| ESC BEC output voltage | 5 V nominal | TBD | TBD | |
| Servo rail voltage, idle | Stable near BEC nominal | TBD | TBD | |
| Servo rail voltage, three servos moving | Stable near BEC nominal | TBD | TBD | |
| Pixhawk-reported battery voltage | Close to multimeter measurement | TBD | TBD | |

## Propulsion Measurements

Propeller remains removed until the propulsion-test stage explicitly authorizes installation.

| Throttle | Battery V | Current A | Motor Temp | ESC Temp | Result / Notes |
|---:|---:|---:|---:|---:|---|
| 0% | TBD | TBD | TBD | TBD | |
| 25% | TBD | TBD | TBD | TBD | |
| 50% | TBD | TBD | TBD | TBD | |
| 75% | TBD | TBD | TBD | TBD | |
| 100% | TBD | TBD | TBD | TBD | |

## Observations / Exceptions

- Initial unloaded flight-battery voltage measured 16.63 V using the TESMEN TM-510.
- PM02 V3 unloaded output measured 15.84 V several days later, consistent with the battery having rested since the earlier full-charge measurement.
- PM02 V3 regulated Pixhawk supply measured 5.31 V at the loose 6-pin power connector.
- With the Pixhawk 6C Mini powered from PM02 V3 POWER1, both I/O and FMU PWR LEDs were solid green. I/O ACT flashed blue and I/O B/E flashed orange. FMU ACT flashed blue and FMU B/E remained off.
- Mission Planner initially connected successfully to the Pixhawk over USB, confirming software-level communication and successful flight-controller boot.
- After firmware transition testing, ArduPlane 4.6.3 on the Pixhawk6C target booted successfully with the microSD card removed. Mission Planner connected on COM6 and identified the vehicle as FIXED WING.
- During the successful ArduPlane 4.6.3/no-microSD boot, the FMU B/E LED continued a red flashing pattern and FMU ACT remained off. Because MAVLink was live and Mission Planner identified FIXED WING, this LED pattern alone is not being treated as a boot failure.
- The current diagnostic has two changed variables relative to the earlier failed state: ArduPlane 4.7.1 was replaced with 4.6.3, and the microSD card was removed. A controlled re-test with the same microSD card reinstalled is required to isolate whether the failure was firmware-version-related, microSD-related, or an interaction between the two.

## Test Completion

This record remains **In progress** until the applicable bench checks are completed and results are reviewed against the MP-1 test plan.
