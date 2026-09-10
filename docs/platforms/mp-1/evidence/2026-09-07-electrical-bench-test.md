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
| ArduPlane 4.6.3 boot, microSD installed | Mission Planner connects and identifies fixed-wing vehicle | Connected; FIXED WING | PASS | Same microSD card reinstalled. Board continued to boot and connect normally. FMU B/E red flashing pattern remained present. |
| 3D accelerometer calibration | Calibration completes successfully | Calibration successful; trim roll=0.52°, pitch=0.81°, yaw=0.00° | PASS | Mission Planner reported successful calibration; reboot required before pre-arm check clears |
| Post-calibration reboot / startup | Clean ArduPlane startup with FMU/IOMCU/IMU initialized | ArduPlane V4.6.3 (3fc7011a); Pixhawk6C; IOMCU 410 2003 411FC231; RCOut PWM:1-16; IMU0 fast sampling 2.0kHz/2.0kHz | PASS | Confirms application firmware, I/O MCU communication, RC output initialization, and IMU startup after reboot |
| GPS1 acquisition / EKF3 initialization | GPS obtains usable fix; EKF3 establishes origin and becomes active | GPS bad-fix warning cleared; EKF3 IMU0/IMU1 origin set and using GPS; AHRS EKF3 active; field elevation 268 m | PASS | Previous AHRS roll/pitch and yaw inconsistency messages cleared after GPS acquisition and EKF3 initialization |
| Compass calibration | Both detected compasses calibrate and pre-arm compass warning clears after reboot | Mag 1 and Mag 2 completed; post-reboot `Compass not calibrated` no longer present | PASS | External M10 IST8310 remains priority 1; internal Pixhawk IST8310 priority 2 |
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
- Reinstalling the same microSD card did not reproduce the failure. ArduPlane 4.6.3 continued to boot and connect as FIXED WING with the card installed. This substantially reduces the likelihood that the microSD card caused the earlier failure and makes the ArduPlane 4.7.1 build or a 4.7.1-specific interaction the primary suspect.
- During both successful ArduPlane 4.6.3 boots, the FMU B/E LED continued a red flashing pattern and FMU ACT remained off. Because MAVLink was live, Mission Planner identified FIXED WING, and the same behavior has been reported on Pixhawk 6C/6C Mini hardware under ArduPilot, this LED pattern alone is not being treated as a boot failure.
- Source-code review of the exact Plane 4.6.3 codebase shows that Pixhawk6C maps GPIO 90 to the physical red FMU LED and assigns it as BoardLED2 LED A. AP_BoardLED2 deliberately commands LED A to a two-flash-then-pause sequence whenever the vehicle is disarmed and the aggregate pre-arm check flag is false. Therefore the observed two-red-flashes/pause pattern is interpreted as **pre-arm checks failing**, not as a bootloader or hardware-fault code. The LED pattern does not identify which specific pre-arm check is failing; Mission Planner pre-arm messages must be used for that diagnosis.
- Mission Planner reported `Calibration successful` for the 3D accelerometer calibration, with trim values roll=0.52°, pitch=0.81°, yaw=0.00°. The subsequent pre-arm message changed to `Accels calibrated requires reboot`, confirming calibration was accepted but requires a restart before the check is cleared.
- After the requested reboot, Mission Planner startup messages reported `ArduPlane V4.6.3 (3fc7011a)`, `ChibiOS: 88b84600`, `Pixhawk6C`, `IOMCU: 410 2003 411FC231`, `RCOut: PWM:1-16`, and `IMU0: fast sampling 2.0kHz/2.0kHz`. This provides a clean post-calibration startup baseline and confirms the I/O microcontroller, PWM output subsystem, and primary IMU initialized under ArduPlane 4.6.3.
- With the M10 GPS connected and moved to an outdoor clear-sky environment, the prior `GPS 1: Bad fix` warning cleared. EKF3 reported tilt alignment, initial yaw alignment, origin set for IMU0 and IMU1, both IMUs using GPS, and `AHRS: EKF3 active`; Mission Planner also reported `Field Elevation Set: 268m`.
- Transient startup messages including `EKF3 Yaw inconsistent`, `EKF3 Roll/Pitch inconsistent`, `Gyros inconsistent`, and `AHRS: not using configured AHRS type` disappeared once GPS/EKF initialization completed. They are not present in the latest pre-arm block.
- Compass setup detected two IST8310 devices: the external compass in the Holybro M10 GPS as priority 1 and the Pixhawk 6C Mini internal compass as priority 2. Mission Planner initially timed out waiting for the start-calibration command acknowledgement, but subsequent pre-arm messages confirmed `Compass calibration running`, showing the autopilot had accepted the command.
- During onboard MagCal, both Mag 1 and Mag 2 progress bars reached full completion. Mission Planner then requested `Please reboot autopilot`, indicating the calibration data was accepted.
- After reboot, `Compass not calibrated` no longer appeared in the pre-arm messages. The current pre-arm state is reduced to two blockers: `Waiting for RC` and `Hardware safety switch`.
- Current baseline recommendation: retain ArduPlane 4.6.3 on MP-1 until the 4.7.x behavior on Pixhawk 6C Mini is better understood or a later release is verified on this hardware.

## Test Completion

This record remains **In progress** until the applicable bench checks are completed and results are reviewed against the MP-1 test plan.
