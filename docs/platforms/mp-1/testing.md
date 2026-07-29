# MP-1 Testing

**Status:** Draft  
**Last Updated:** 2026-07-29

## Purpose

This document defines how Meadowlark Platform 1 (MP-1) will be tested before, during, and after its initial flight campaign.

The goal is to prove that the aircraft can:

- Operate safely under manual control
- Maintain stabilized flight
- Execute a pre-programmed waypoint mission onboard
- Return to launch
- Allow immediate RC pilot takeover
- Land under manual control
- Record enough evidence for another person to reproduce and review the result

This document combines the ground-test plan, flight-test plan, acceptance criteria, and evidence-recording process.

Testing should proceed in small steps. A failed step must be corrected before moving to the next higher-risk step.

---

# Test Philosophy

MP-1 testing follows these principles:

1. Remove unnecessary risk before each test.
2. Change one major variable at a time.
3. Use the simplest test that can answer the question.
4. Record the exact aircraft configuration.
5. Preserve logs, measurements, photographs, and notes.
6. Do not continue when a safety-critical result is unclear.
7. Do not treat a successful single test as proof of repeatability.
8. Repeat critical tests after any relevant hardware or software change.
9. Keep manual pilot takeover available during autonomous testing.
10. Do not add payloads or nonessential systems during initial flight validation.

---

# Test Stages

Testing is divided into the following stages:

| Stage | Purpose |
|------|---------|
| 0 | Documentation and configuration review |
| 1 | Incoming inspection |
| 2 | Unpowered assembly inspection |
| 3 | First power-up |
| 4 | Bench functional testing |
| 5 | Power and load testing |
| 6 | Propulsion ground testing |
| 7 | Manual flight testing |
| 8 | Stabilized-mode testing |
| 9 | Return-to-launch testing |
| 10 | Autonomous waypoint testing |
| 11 | Repeatability and endurance testing |

Each stage must be completed before advancing unless a documented reason supports a different sequence.

---

# Test Records

Create test records under:

```text
docs/platforms/mp-1/evidence/tests/
```

Suggested naming format:

```text
YYYY-MM-DD-mp1-a01-test-name.md
```

Examples:

```text
2026-08-15-mp1-a01-first-power-up.md
2026-08-20-mp1-a01-static-propulsion-test.md
2026-09-02-mp1-a01-first-manual-flight.md
```

Each test record should include:

- Test title
- Date and time
- Location
- Aircraft identifier
- Test operator
- Pilot
- Observer or spotter
- Weather
- Aircraft mass
- Battery identifier
- Battery state
- Firmware version
- Parameter-file version
- Mission-file version
- Hardware configuration
- Test objective
- Procedure
- Measurements
- Result
- Anomalies
- Corrective actions
- Links to logs, photographs, and video
- Go / no-go decision for the next stage

---

# Configuration Control

Before every test, record:

- Aircraft identifier
- Flight-controller model and revision
- Firmware version
- Parameter file
- Mission file
- Motor
- ESC
- Propeller
- Battery
- Power module
- Servos
- RC receiver
- GPS and compass
- Telemetry radio
- Airspeed sensor, if installed
- Ready-to-fly mass
- Center of gravity
- Any change since the previous test

Any unrecorded configuration change invalidates comparison with earlier results.

---

# Stage 0 — Documentation and Configuration Review

## Objective

Confirm that the aircraft configuration is understood before hardware testing begins.

## Procedure

Review:

- `design.md`
- `components.md`
- `build.md`
- Current build record
- Wiring diagram, if available
- Connector pinouts
- Firmware version
- Parameter file
- Mission file
- Battery records
- Previous test results

## Acceptance Criteria

Pass when:

- All installed components are identified
- Open wiring questions are resolved
- Connector polarity is documented
- Current firmware and parameters are archived
- The intended test objective is clear
- Required tools and safety equipment are available
- No unresolved safety-critical discrepancy remains

---

# Stage 1 — Incoming Inspection

## Objective

Confirm that received components match the selected models and are free of obvious damage.

## Procedure

For each component:

1. Confirm manufacturer and model.
2. Confirm revision where applicable.
3. Inspect packaging and hardware.
4. Measure mass.
5. Measure dimensions where important.
6. Confirm connectors and cable lengths.
7. Photograph the component.
8. Record discrepancies.

## Acceptance Criteria

Pass when:

- The component matches the ordered item
- No damage is present
- Connectors and polarity are understood
- Mass and dimensions are within expected range
- No undocumented substitution has occurred

A component with unresolved identity, damage, or incompatible connectors must not be installed.

---

# Stage 2 — Unpowered Assembly Inspection

## Objective

Confirm that the aircraft is mechanically complete and electrically safe before power is applied.

## Procedure

Inspect:

- Airframe joints
- Control surfaces
- Hinges
- Pushrods
- Servo mounts
- Motor mount
- Motor screws
- ESC mount
- Battery restraint
- Flight-controller mount
- GPS mount
- Receiver mount
- Telemetry mount
- Wire routing
- Connector seating
- Antenna placement
- Propeller clearance
- Center of gravity
- Loose hardware
- Exposed conductors

The propeller must be removed.

## Acceptance Criteria

Pass when:

- No control surface binds
- No servo reaches a mechanical stop
- Motor rotates freely
- Wiring cannot contact moving parts
- Battery is restrained
- Flight controller is secure
- GPS and compass are separated from major current paths
- No exposed conductor can short
- Only one positive BEC source is connected to the servo rail
- Center of gravity is within the current target range

---

# Stage 3 — First Power-Up

## Objective

Confirm that the aircraft powers safely without smoke, overheating, or incorrect voltage.

## Safety Conditions

- Propeller removed
- Aircraft restrained
- Battery accessible for immediate disconnection
- Multimeter available
- Current-limited source or smoke stopper used where practical

## Procedure

1. Confirm battery polarity.
2. Confirm XT60 polarity.
3. Confirm power-module orientation.
4. Confirm servo connector polarity.
5. Connect the battery.
6. Observe for smoke, odor, heat, or abnormal sound.
7. Confirm flight-controller boot.
8. Measure flight-controller supply voltage.
9. Measure servo-rail voltage.
10. Confirm receiver power.
11. Confirm GPS power.
12. Confirm telemetry power.
13. Check component temperature.
14. Disconnect power.

## Acceptance Criteria

Pass when:

- No smoke, odor, or abnormal heating occurs
- Flight controller boots normally
- Flight-controller voltage is within specification
- Servo rail is approximately 5 V
- Receiver, GPS, and telemetry power normally
- No connector or wire becomes warm
- No unexpected backfeed is observed

---

# Stage 4 — Bench Functional Testing

## Objective

Confirm that all control, navigation, communication, and logging functions operate with the propeller removed.

## RC Control

Verify:

- Receiver binds correctly
- All control channels respond
- Flight-mode switch positions are correct
- Pilot takeover command is available
- RC failsafe activates as configured

## Servo Outputs

Verify:

- Each output controls the intended servo
- Surface direction is correct
- Servo endpoints do not cause binding
- Neutral positions are reasonable
- Stabilization corrections move surfaces in the correct direction

## Throttle Output

Verify:

- Throttle channel is assigned correctly
- Motor remains disarmed when required
- Throttle failsafe behaves correctly
- Motor direction is correct at low power

## GPS and Compass

Verify:

- GPS is detected
- Compass is detected
- Position lock is obtained outdoors
- Heading changes correctly
- Home position can be established
- Compass orientation is correct

## Telemetry

Verify:

- Ground station connects
- Flight mode is reported
- Position and altitude are reported
- Battery voltage is reported
- Battery current is reported
- Mission upload works
- Parameters can be read
- Link loss does not disable RC control

## Logging

Verify:

- microSD card is detected
- Log file is created
- Flight mode is recorded
- RC input is recorded
- Servo output is recorded
- GPS data is recorded
- Voltage and current are recorded

## Acceptance Criteria

Pass when all required devices operate correctly and no unexplained reset, warning, or data loss occurs.

---

# Stage 5 — Power and Load Testing

## Objective

Confirm that flight-controller power and servo power remain stable under realistic electrical load.

## Servo Load Test

### Setup

- Propeller removed
- Aircraft restrained
- Control surfaces mechanically loaded in a realistic manner
- Servo-rail voltage measured
- Flight-controller and receiver monitored for resets

### Procedure

1. Move each servo individually through full travel.
2. Move all servos rapidly at the same time.
3. Repeat movement for at least 60 seconds.
4. Hold surfaces under moderate load briefly.
5. Repeat while telemetry and GPS are operating.
6. Record minimum servo-rail voltage.
7. Record current if measurable.
8. Check ESC/BEC and servo temperature.

### Acceptance Criteria

Pass when:

- Servo rail remains at or above 4.8 V
- No flight-controller reset occurs
- No receiver reset occurs
- No GPS or telemetry reset occurs
- No unacceptable jitter occurs
- No servo stalls under expected load
- BEC and servo temperatures remain acceptable

Failure requires correction before propulsion or flight testing.

## Rapid Throttle Electrical Test

With the propeller still removed or using a safe low-load setup:

1. Operate servos rapidly.
2. Apply rapid throttle changes.
3. Monitor flight-controller voltage.
4. Monitor servo-rail voltage.
5. Watch for resets or communication loss.

Pass when no reset or unacceptable voltage disturbance occurs.

---

# Stage 6 — Propulsion Ground Testing

## Objective

Measure the actual propulsion load and confirm that the motor, ESC, battery, connectors, and power module operate safely.

## Safety Conditions

- Correct propeller installed
- Propeller balanced
- Rotation direction confirmed
- Aircraft securely restrained
- Clear test area
- No person in the propeller plane
- Emergency battery disconnect available
- Eye protection used
- Test observer present where practical

## Measurements

Record:

- Battery identifier
- Battery voltage before test
- Propeller model and size
- Peak current
- Sustained current
- Voltage sag
- Static thrust, if measured
- Motor temperature
- ESC temperature
- BEC temperature
- Power-module temperature
- Connector temperature
- Wire temperature
- Vibration
- Abnormal sound

## Test Sequence

1. Run at low throttle.
2. Check direction, sound, and vibration.
3. Increase to approximately 25% throttle.
4. Hold briefly and inspect.
5. Increase to approximately 50% throttle.
6. Hold and record measurements.
7. Increase to approximately 75% throttle.
8. Hold and record measurements.
9. Apply full throttle only for the planned short duration.
10. Return to idle.
11. Disconnect power.
12. Inspect all components.

Do not hold full throttle longer than necessary to answer the test objective.

## Acceptance Criteria

Pass when:

- Current remains within motor, ESC, battery, connector, wire, and power-module limits
- Voltage sag is acceptable
- No connector or wire overheats
- Motor and ESC temperatures remain acceptable
- No abnormal vibration occurs
- No flight-controller reset occurs
- Battery monitoring remains accurate
- Mounting hardware remains secure

## Power-Module Decision

The power module may move from Research to Selected only after:

- Sustained current is known
- Burst current is known
- Burst duration is known
- Voltage drop is acceptable
- Connector and wire temperatures are acceptable
- Sensor calibration is verified
- Complete current-path limits exceed the measured load with margin

---

# Stage 7 — Manual Flight Testing

## Objective

Confirm that the aircraft can take off, fly, and land safely under direct pilot control.

## Preconditions

The following must already pass:

- Documentation review
- Incoming inspection
- Unpowered inspection
- First power-up
- Bench functional testing
- Servo load testing
- Propulsion ground testing
- Center-of-gravity check
- Range check
- Failsafe review
- Weather review

## Initial Manual Flight

The first flight should use:

- Experienced pilot
- Open field
- Light wind
- Good visibility
- Visual line of sight
- No autonomous mission
- No payload
- Conservative control throws
- Conservative flight duration

## Test Objectives

Confirm:

- Launch behavior
- Climb performance
- Trim
- Control authority
- Stall tendency
- Glide behavior
- Motor response
- Battery consumption
- Landing behavior
- Structural integrity
- Vibration level
- Log quality

## Acceptance Criteria

Pass when:

- Takeoff is controlled
- Aircraft remains controllable throughout the flight
- No severe trim or stability problem exists
- Propulsion is adequate
- Landing is controlled
- No structural damage occurs
- No power reset occurs
- Logs are complete
- Battery reserve remains acceptable

At least two successful manual flights are recommended before stabilized or autonomous testing.

---

# Stage 8 — Stabilized-Mode Testing

## Objective

Confirm that the flight controller stabilizes the aircraft correctly before autonomous navigation is attempted.

## Procedure

1. Take off manually.
2. Climb to a safe altitude.
3. Enter the selected stabilized mode.
4. Make small control inputs.
5. Confirm roll response.
6. Confirm pitch response.
7. Confirm throttle behavior.
8. Return to manual control.
9. Repeat as required.
10. Land manually.

## Acceptance Criteria

Pass when:

- Mode transition is predictable
- Aircraft remains stable
- Stabilization corrections are in the correct direction
- Control authority remains adequate
- Pilot takeover is immediate
- No oscillation or divergence occurs
- Logs show acceptable attitude control

Tune conservatively. Do not begin waypoint testing while significant oscillation, trim, or navigation issues remain.

---

# Stage 9 — Return-to-Launch Testing

## Objective

Confirm that return-to-launch works before a complete waypoint mission is attempted.

## Preconditions

- Manual flight passed
- Stabilized flight passed
- GPS and compass performance acceptable
- Home position confirmed
- RTL altitude reviewed
- Geofence reviewed
- Pilot takeover verified
- Test area clear

## Procedure

1. Take off manually.
2. Climb to a safe altitude.
3. Fly to a safe test position.
4. Activate return-to-launch.
5. Observe initial turn and altitude behavior.
6. Allow the aircraft to approach the home area.
7. Take over manually before landing unless the test plan specifically authorizes otherwise.
8. Land manually.

## Acceptance Criteria

Pass when:

- RTL activates correctly
- Aircraft turns toward home
- Altitude behavior matches configuration
- Orbit or loiter behavior is predictable
- Pilot takeover works immediately
- No unsafe path is commanded
- Logs match observed behavior

---

# Stage 10 — Autonomous Waypoint Testing

## Objective

Confirm that MP-1 can execute a pre-programmed waypoint route onboard without a companion computer.

## Initial Mission Design

The first mission should have:

- Few waypoints
- Wide spacing
- Wide turns
- Conservative altitude
- Visual line of sight
- Clear terrain
- No obstacles
- No autonomous takeoff
- No autonomous landing
- A route that allows easy pilot takeover
- An appropriate geofence
- A reviewed RTL altitude

## Preconditions

- Manual flight passed
- Stabilized flight passed
- RTL passed
- Pilot takeover passed
- Telemetry-loss behavior verified
- RC-loss failsafe verified
- GPS-loss response reviewed
- Mission file reviewed
- Weather within limits
- Full battery installed
- Logs enabled

## Procedure

1. Power the aircraft.
2. Confirm the correct mission is loaded.
3. Confirm home position.
4. Confirm GPS and compass health.
5. Confirm battery status.
6. Confirm geofence.
7. Confirm flight modes.
8. Take off manually.
9. Climb to a safe altitude.
10. Enter autonomous mission mode.
11. Observe waypoint navigation.
12. Monitor position, altitude, battery, and mode.
13. Use pilot takeover if behavior is unexpected.
14. Use RTL if required by the test plan.
15. Land manually.
16. Archive the log immediately.

## Acceptance Criteria

Pass when:

- Mission starts correctly
- Waypoints are visited in the intended order
- Aircraft remains within the test area
- Altitude remains within the planned range
- Turns are stable
- No unexpected mode change occurs
- Telemetry is not required for mission continuation
- Pilot takeover works immediately
- Return-to-launch remains available
- Landing is completed safely
- Log data confirms the observed mission sequence

At least three successful waypoint flights are recommended before declaring the capability repeatable.

---

# Stage 11 — Repeatability and Endurance Testing

## Objective

Confirm that the validated configuration produces consistent results.

## Repeatability Testing

Repeat the same approved flight profile using:

- Same aircraft
- Same propeller
- Same firmware
- Same parameter file
- Same mission file
- Same battery type
- Similar weather conditions

Compare:

- Current
- Voltage sag
- Energy consumption
- Climb performance
- Waypoint accuracy
- RTL behavior
- Servo performance
- Temperatures
- Flight time
- Landing behavior

## Endurance Testing

Endurance testing should begin only after the aircraft is stable and repeatable.

Record:

- Battery capacity used
- Average current
- Cruise current
- Flight duration
- Reserve at landing
- Wind
- Airspeed, if available
- Groundspeed
- Ready-to-fly mass

Do not pursue maximum duration during early testing.

## Acceptance Criteria

Pass when:

- Results are consistent across multiple flights
- No progressive heating or wear issue appears
- Battery reserve remains adequate
- No unexplained configuration drift occurs
- Mission performance remains stable
- Logs remain complete

---

# Failsafe Testing

Failsafe testing should be performed incrementally.

## RC Link Loss

Verify:

- Receiver failsafe behavior
- Flight-controller detection
- Configured response
- Recovery when the link returns
- Log recording

Conduct initial checks on the bench before flight testing.

## Telemetry Loss

Verify:

- RC control remains available
- Onboard mission continues
- Flight controller does not change mode unexpectedly
- Ground station reconnects when the link returns

## GPS Loss

Use simulation, hardware-in-the-loop, or controlled methods before considering flight testing.

Verify:

- GPS fault is detected
- Configured response occurs
- Pilot takeover remains available
- Event is logged

## Low Battery

Verify:

- Voltage warning
- Capacity warning
- Failsafe threshold
- Configured response
- Log recording

Do not intentionally over-discharge a LiPo battery.

## Geofence

Verify:

- Fence loads correctly
- Boundary is visible in the ground station
- Configured response is understood
- Behavior is tested conservatively

---

# Environmental Limits

Initial testing should use conservative conditions.

Recommended initial limits:

| Condition | Initial Guidance |
|-----------|------------------|
| Wind | Light and steady |
| Gusts | Minimal |
| Visibility | Clear visual line of sight |
| Precipitation | None |
| Temperature | Within all component and battery limits |
| Field | Open, unobstructed, and legal |
| People | Kept outside the operating area |
| RF Environment | Checked for interference where practical |

Exact numerical weather limits should be added after early manual-flight experience.

---

# No-Go Conditions

Do not fly when:

- Aircraft configuration is not recorded
- Battery condition is uncertain
- Center of gravity is outside the approved range
- Control surface direction is uncertain
- Stabilization direction is uncertain
- GPS or compass health is poor
- Home position is invalid
- RC range is uncertain
- Failsafe configuration is unclear
- Propulsion current exceeds a known component limit
- Any connector or wire overheats
- Flight controller, receiver, or servo rail resets
- Weather exceeds current limits
- Required logs are unavailable
- Pilot or observer is not comfortable continuing

A no-go decision is a valid test result.

---

# Post-Test Inspection

After every ground or flight test:

1. Disconnect the battery.
2. Inspect the propeller.
3. Inspect motor and mount.
4. Inspect ESC.
5. Inspect power module.
6. Inspect connectors and wires.
7. Inspect servo mounts and linkages.
8. Inspect control surfaces.
9. Inspect battery.
10. Check component temperature.
11. Download logs.
12. Record anomalies.
13. Update the test record.
14. Decide whether the aircraft may proceed.

Do not begin another flight until any safety-relevant anomaly is understood.

---

# Evidence to Preserve

Preserve:

- Build record
- Test record
- Photographs
- Wiring diagram
- Parameter files
- Mission files
- Flight logs
- Telemetry logs
- Battery records
- Current and voltage measurements
- Temperature measurements
- Video where useful
- Failure notes
- Corrective actions
- Final acceptance decision

Suggested evidence structure:

```text
docs/platforms/mp-1/evidence/
├── builds/
├── inspections/
├── ground-tests/
├── flight-tests/
├── logs/
├── photos/
└── measurements/
```

Large binary logs may be stored outside Git when appropriate, but the repository should contain an index that identifies where they are stored and how they relate to each test.

---

# Capability Completion Criteria

## Manual Flight Capability

Complete when:

- At least two controlled manual flights are completed
- Takeoff and landing are repeatable
- No unresolved power, control, or structural issue remains
- Logs are complete

## Stabilized Flight Capability

Complete when:

- Stabilized mode is predictable
- No unsafe oscillation occurs
- Pilot takeover is immediate
- Logs confirm stable attitude control

## Return-to-Launch Capability

Complete when:

- RTL activates correctly
- Aircraft returns toward home predictably
- Altitude behavior is acceptable
- Pilot takeover works
- Results are confirmed in logs

## Autonomous Waypoint Capability

Complete when:

- At least three successful onboard waypoint missions are completed
- Mission order is correct
- Telemetry is not required for continuation
- Pilot takeover works
- RTL remains available
- Logs confirm expected behavior
- No unresolved safety-critical anomaly remains

---

# Open Testing Items

The following details remain open:

1. Final numerical weather limits
2. Final center-of-gravity range
3. Final control throws
4. Final stabilized-mode selection
5. Final geofence values
6. Final RTL altitude
7. Final battery reserve policy
8. Final propeller-specific current limits
9. Final power-module acceptance limits
10. Final temperature limits
11. Final waypoint mission
12. Final test location
13. Final RC range-test procedure
14. Final GPS-loss test method

These should be updated as components are selected and the aircraft is assembled.

---

# Related Documents

```text
docs/platforms/mp-1/README.md
docs/platforms/mp-1/design.md
docs/platforms/mp-1/components.md
docs/platforms/mp-1/build.md
docs/platforms/mp-1/decisions.md
```

---

# Change History

## 2026-07-29

- Created the consolidated MP-1 testing document.
- Combined ground testing, flight testing, acceptance criteria, and evidence requirements.
- Added staged progression from inspection through autonomous waypoint testing.
- Defined capability completion criteria for manual flight, stabilized flight, RTL, and waypoint navigation.
