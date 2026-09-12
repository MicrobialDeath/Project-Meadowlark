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
- Receiver: RadioMaster RP4TD ExpressLRS 2.4 GHz
- Transmitter: RadioMaster TX16S MK3, internal ExpressLRS
- Multimeter: TESMEN TM-510

## Bench Measurements

| Test | Expected / Reference | Measured | Result | Notes |
|---|---|---:|---|---|
| Battery voltage, unloaded | Approximately 16.8 V when fully charged | 16.63 V | PASS | Fully charged pack after resting; normal value |
| Battery polarity | Correct | Positive 16.63 V with red probe on + and black probe on − | PASS | Confirms expected terminal polarity |
| PM02 V3 input voltage | Near battery voltage | TBD | TBD | |
| PM02 V3 output voltage, unloaded | Near battery voltage | 15.84 V | PASS | Measured several days after initial full-charge battery reading; output is consistent with present pack voltage |
| Pixhawk supply voltage | 5 V-class regulated supply | 5.31 V | PASS | Measured at PM02 V3 6-pin Pixhawk power output with Pixhawk disconnected |
| Pixhawk power-on / boot indication | Stable powered state with processor activity | I/O: PWR solid green, B/E flashing orange, ACT flashing blue; FMU: PWR green, ACT blue flashing, B/E off | PASS | Power and processor activity observed |
| Mission Planner USB connection | Flight controller enumerates and establishes MAVLink connection | Connected successfully | PASS | Initial software-level communication with Pixhawk over USB |
| ArduPlane 4.6.3 boot, no microSD | Mission Planner connects and identifies fixed-wing vehicle | COM6 connected; FIXED WING | PASS | Pixhawk6C target, ArduPlane 4.6.3; microSD removed |
| ArduPlane 4.6.3 boot, microSD installed | Mission Planner connects and identifies fixed-wing vehicle | Connected; FIXED WING | PASS | Same microSD card reinstalled; board continued to boot and connect normally |
| 3D accelerometer calibration | Calibration completes successfully | Calibration successful; trim roll=0.52°, pitch=0.81°, yaw=0.00° | PASS | Mission Planner reported successful calibration |
| Post-calibration reboot / startup | Clean ArduPlane startup with FMU/IOMCU/IMU initialized | ArduPlane V4.6.3 (3fc7011a); Pixhawk6C; IOMCU 410 2003 411FC231; RCOut PWM:1-16 | PASS | Confirms application firmware and output subsystem startup |
| GPS1 acquisition / EKF3 initialization | GPS obtains usable fix; EKF3 establishes origin and becomes active | GPS warning cleared; EKF3 origin set; AHRS EKF3 active | PASS | Field elevation 268 m |
| Compass calibration | Both detected compasses calibrate and warning clears | Mag 1 and Mag 2 completed | PASS | External M10 compass priority 1; internal Pixhawk compass priority 2 |
| ESC BEC output voltage | 5 V nominal | 5.26 V | PASS | Measured on Skywalker ESC control/BEC lead |
| Servo rail voltage, idle | Stable near BEC nominal | 5.24 V | PASS | Measured on unused MAIN OUT connector |
| Servo rail voltage, three servos connected idle | Stable near BEC nominal | 5.24 V | PASS | Three EMAX servos connected on MAIN OUT 1, 2, and 4 |
| Servo rail voltage, three servos moving | Stable near BEC nominal | TBD | TBD | Dynamic three-servo load test remains pending |
| Pixhawk-reported battery voltage, before calibration | Close to multimeter measurement | 16.22 V vs. 16.59 V | REVIEW | About 2.2% low |
| Pixhawk-reported battery voltage, after calibration | Match multimeter reference closely | 16.5896 V vs. 16.59 V | PASS | Voltage divider recalculated |
| Independent servo motion check | All three selected servos move normally | All three moved on Spektrum XBC200 | PASS | Confirms servo hardware operation |
| MAIN OUT 8 throttle-signal check | Valid minimum-throttle PWM output | Test servo moved to endpoint and held | PASS | Output 8 temporarily set to Throttle (~1100 µs) |
| ESC initialization from MAIN OUT 8 | ESC recognizes signal and 4S battery | Startup sequence, four cell beeps, long ready tone | PASS | Propeller removed |
| ESC initialization from MAIN OUT 3 | Final throttle output recognizes signal and 4S battery | Startup sequence, four cell beeps, long ready tone | PASS | ESC moved to standard ArduPlane throttle output; Output 8 restored to Disabled |
| RP4TD TELEM2 configuration | CRSF/RC input enabled on TELEM2 | SERIAL2_PROTOCOL=23; SERIAL2_OPTIONS=0 | PASS | Setting persisted after reboot |
| TX16S stick-channel mapping | Standard AETR order | CH1 Aileron, CH2 Elevator, CH3 Throttle, CH4 Rudder | PASS | Verified on TX16S Channel Monitor |
| TX16S arm-channel check | CH5 low for disarmed state | SF controls CH5; -100% selected | PASS | ExpressLRS `!Armed!` warning cleared |
| RP4TD ExpressLRS binding/link | Receiver binds and establishes telemetry link | TX16S reported `Telemetry connected`; RP4TD LED became solid light blue | PASS | Confirms active 2.4 GHz ExpressLRS link between TX16S MK3 and RP4TD |
| Mission Planner RC input / calibration | CH1-CH5 detected across normal full ranges | CH1 988-2011; CH2 988-2011; CH3 988-2011; CH4 988-2011; CH5 999-2000 | PASS | Center values after calibration: CH1 1501, CH2 1500, CH4 1498; throttle low 988 |
| TX16S-to-servo live control | Aileron, elevator, and rudder servos respond through full live command chain | All three EMAX servos moved as expected from TX16S control inputs through RP4TD and Pixhawk | PASS | Motor disconnected during RC calibration and live servo verification |
| RC failsafe activation | Loss of transmitter link should trigger ArduPlane RC failsafe actions | `Throttle failsafe on`; short failsafe switched to CIRCLE; long failsafe switched to RTL | PASS | TX16S intentionally powered off with motor disconnected; spoken alert reported `Failsafe on, RTL` |
| RC failsafe recovery | Restored transmitter link should clear failsafe and return to normal command availability | `Throttle failsafe off`; `RC Long Failsafe Cleared`; ELRS link restored at 500 Hz | PASS | Flight mode remained RTL after link recovery and was manually returned to MANUAL; direct servo control then resumed normally |

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
- ArduPlane 4.6.3 on the Pixhawk6C target remains the current stable MP-1 baseline after successful boot and MAVLink verification with and without the microSD card installed.
- Source review established that the Pixhawk 6C Mini FMU red double-flash/pause pattern under ArduPilot corresponds to aggregate pre-arm failure while disarmed, not a bootloader or board hardware fault.
- Accelerometer, GPS/EKF3, and dual-compass calibration checks have passed. After `BRD_SAFETY_DEFLT=0` and clean initialization, the remaining pre-arm blocker had been `Waiting for RC`.
- Skywalker BEC output and shared servo rail both measured in the expected 5 V range. All three selected servos passed independent motion testing.
- PM02/Pixhawk voltage sensing was calibrated against the TESMEN TM-510 and now matches the multimeter reference closely. Current-sensor calibration remains pending until a meaningful known-current load can be applied.
- Mission Planner Battery Capacity was corrected to 5000 mAh for the selected Spektrum flight battery.
- ESC signal-path testing first verified MAIN OUT 8 temporarily, then the ESC was moved to the standard ArduPlane throttle output on MAIN OUT 3. MAIN OUT 8 was restored to Disabled. The final output mapping is MAIN OUT 1 Aileron, 2 Elevator, 3 Throttle, 4 Rudder, 5-8 unused.
- The RP4TD harness uses Pixhawk TELEM2 Pin 1 +5 V to RP4TD `+`, Pin 2 TX to RP4TD RX, Pin 3 RX to RP4TD TX, and Pin 6 GND to RP4TD `-`; CTS/RTS are unused. Harness color convention is red +5 V, green to RP4TD RX, yellow to RP4TD TX, black ground.
- TELEM2 was configured for serial RC input with `SERIAL2_PROTOCOL=23` and `SERIAL2_OPTIONS=0`; the configuration persisted after reboot.
- TX16S stick mapping was verified as CH1 Aileron, CH2 Elevator, CH3 Throttle, CH4 Rudder. SF controls CH5/AUX1 and was placed at -100% for the disarmed state.
- The RP4TD entered ExpressLRS bind mode, the TX16S completed binding, reported `Telemetry connected`, and the RP4TD LED changed to solid light blue. This confirms the RF link between the TX16S MK3 and RP4TD is established.
- Mission Planner received all five active RC channels through the RP4TD and completed radio calibration successfully. CH1-CH4 calibrated to approximately 988-2011 with centered roll/pitch/yaw values essentially at 1500; CH5 calibrated to 999-2000.
- With the motor disconnected for safety, all three installed EMAX servos responded normally to live TX16S commands through the complete TX16S -> ExpressLRS -> RP4TD -> Pixhawk -> MAIN OUT control path.
- With `THR_FAILSAFE=1`, intentionally powering off the TX16S triggered `Throttle failsafe on`, then `RC Short Failsafe: switched to CIRCLE`, followed by `RC Long Failsafe On: RTL`. The servos then moved autonomously as expected under ArduPlane navigation control while the motor remained disconnected.
- Powering the TX16S back on restored the ExpressLRS link and produced `Throttle failsafe off` and `RC Long Failsafe Cleared`. ArduPlane remained in RTL after link recovery until the mode was manually changed back to MANUAL; direct TX16S servo control then resumed normally.
- Bench GPS/EKF messages observed during the failsafe recovery included `AHRS: EKF3[1] vel error` and `RTL mode not armable`; these were associated with bench navigation state and the retained RTL mode, not with failure of the recovered RC link.
- Current baseline recommendation: retain ArduPlane 4.6.3 on MP-1 until the 4.7.x behavior on Pixhawk 6C Mini is better understood or a later release is verified on this hardware.

## Test Completion

This record remains **In progress** until the applicable bench checks are completed and results are reviewed against the MP-1 test plan.
