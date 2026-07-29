# MP-1 Testing

**Status:** Draft

## Purpose

This document defines how Meadowlark Platform 1 (MP-1) is verified before and during flight testing.

It answers **how the aircraft is tested**.

It does **not** define:

- System architecture (see [design.md](design.md))
- Hardware selection (see [components.md](components.md))
- Assembly and configuration (see [build.md](build.md))
- Engineering rationale (see [decisions.md](decisions.md))

Actual test records, logs, photographs, measurements, parameter exports, and mission files will be stored under `docs/platforms/mp-1/evidence/` once evidence records exist.

---

## Test Philosophy

Testing should progress from low-risk checks to higher-risk flight operations.

The aircraft should not advance to the next test stage until the current stage has passed or an explicit exception has been documented.

Testing should be:

- Incremental
- Repeatable
- Observable
- Configuration-controlled
- Supported by recorded evidence

A successful flight does not replace a test record.

---

## Test Stages

MP-1 testing follows this sequence:

1. Documentation review
2. Physical inspection
3. Electrical checks
4. Flight-controller checks
5. Servo and control-surface checks
6. Propulsion checks
7. Ground-operation checks
8. Manual flight
9. Stabilized flight
10. Return-to-launch
11. Autonomous waypoint flight

Each stage should be completed before proceeding to the next.

---

## Test Configuration

Before testing, record:

- Aircraft identifier
- Date
- Test location
- Weather conditions
- Hardware configuration
- Firmware version
- Parameter-file revision
- Mission-file revision
- Propeller
- Battery identifier
- Aircraft mass
- Center of gravity

The tested configuration must match the configuration described in [components.md](components.md) and [build.md](build.md).

---

## Documentation Review

Before physical testing:

- Confirm all required hardware is listed in [components.md](components.md).
- Confirm the aircraft was assembled according to [build.md](build.md).
- Confirm unresolved design questions do not block the planned test.
- Confirm major deviations are recorded in [decisions.md](decisions.md).
- Confirm the intended test objective and pass criteria are written down.

Do not begin testing when the aircraft configuration is uncertain.

---

## Physical Inspection

Inspect the aircraft for:

- Structural damage
- Loose fasteners
- Wing and tail alignment
- Control-surface freedom of movement
- Secure hinges and linkages
- Secure battery retention
- Secure avionics mounting
- Protected and restrained wiring
- Proper antenna placement
- Correct propeller installation

Any defect that may affect safe operation is a test failure until corrected.

---

## Electrical Checks

Perform initial electrical checks with the propeller removed where practical.

Verify:

- Correct battery voltage
- Correct polarity
- Secure power connectors
- No exposed conductors
- No unexpected heating
- Stable flight-controller power
- Stable servo-rail voltage
- Correct battery-monitor readings
- Proper power-up and shutdown behavior

Stop immediately if smoke, odor, abnormal heat, or unstable voltage is observed.

---

## Flight-Controller Checks

Verify:

- Correct board orientation
- Correct airframe type
- Accelerometer calibration
- Compass calibration
- GPS operation
- Home-position acquisition
- Battery monitoring
- Flight-mode assignments
- Data logging
- Failsafe configuration
- Return-to-launch configuration

Export the final parameter file before flight testing.

---

## RC and Failsafe Checks

Verify:

- All required channels respond correctly
- Control inputs move in the expected direction
- Flight modes are assigned correctly
- RC range is acceptable
- RC-loss behavior matches the intended failsafe
- Pilot takeover is immediate and predictable

Failsafe testing should be performed with the aircraft restrained and the propeller removed unless propulsion is required for the specific check.

---

## Servo and Control-Surface Checks

Verify:

- Correct servo assignment
- Correct control direction
- Full required travel
- No binding
- No excessive linkage play
- No interference through the full range of motion
- Stable servo power under simultaneous movement
- Neutral positions are consistent

Control directions must be checked from the aircraft's point of view.

---

## Propulsion Checks

Conduct propulsion testing with the aircraft restrained and the test area clear.

Verify:

- Correct motor rotation
- Correct propeller orientation
- Smooth throttle response
- Stable ESC operation
- No abnormal vibration
- No abnormal sound
- No overheating
- Acceptable current draw
- Acceptable battery voltage under load
- Reliable throttle cutoff

Record current, voltage, and temperature where practical.

---

## Ground-Operation Checks

Before flight, verify:

- GPS lock is reliable
- Home position is correct
- Telemetry is stable
- Flight modes switch correctly
- Control surfaces respond correctly in each mode
- Stabilization corrections move in the correct direction
- Return-to-launch settings are reasonable
- Logging starts correctly
- Battery status is credible

A final preflight inspection is required after all powered ground tests.

---

## Manual Flight Testing

The first flight should use manual control with conservative limits.

Objectives:

- Confirm safe launch behavior
- Confirm basic controllability
- Confirm trim
- Confirm adequate propulsion
- Confirm acceptable stall behavior
- Confirm predictable landing behavior
- Confirm reliable logging

Pass criteria:

- Aircraft remains controllable
- No unexpected structural or electrical behavior occurs
- Pilot can complete a safe landing
- Logs are recovered and readable

Do not proceed to stabilized or autonomous testing if manual flight is not consistently safe.

---

## Stabilized Flight Testing

After manual flight is verified, test stabilized modes.

Verify:

- Mode transitions are predictable
- Attitude stabilization is correct
- Control authority remains adequate
- Oscillation is absent or acceptable
- Pilot takeover remains immediate
- Aircraft returns safely to manual control

Any unstable or counter-correcting behavior is a failure.

---

## Return-to-Launch Testing

Return-to-launch testing should begin from a safe altitude and distance.

Verify:

- RTL engages reliably
- Aircraft turns toward the expected return path
- Target altitude is appropriate
- Loiter behavior is predictable
- Pilot takeover works immediately
- RTL does not depend on telemetry

Initial RTL testing should be terminated manually before landing unless autonomous landing has been separately designed and approved.

---

## Autonomous Waypoint Testing

Autonomous waypoint testing should begin with a short, simple mission.

Verify:

- Mission upload is correct
- Waypoint order is correct
- Altitude references are correct
- Aircraft tracks the route acceptably
- Mission completion behavior is correct
- RTL or pilot takeover works as expected
- Logs capture the mission

Expand mission complexity only after the basic waypoint mission is repeatable.

---

## Environmental Limits

Test limits should be established before flight.

At minimum, define:

- Maximum wind
- Minimum visibility
- Minimum cloud clearance
- Maximum temperature
- Minimum temperature
- Battery condition limits
- Flight-area boundaries
- Minimum safe altitude
- Maximum planned distance

Do not infer safe limits from one successful flight.

---

## Pass and Fail Criteria

A test passes only when:

- The planned objective is achieved
- No unplanned safety-critical behavior occurs
- The tested configuration is known
- Required evidence is recorded
- Results are repeatable where repetition is required

A test fails when:

- The aircraft behaves unpredictably
- A safety limit is exceeded
- Required data is unavailable
- The configuration cannot be confirmed
- The result cannot be interpreted confidently

A failed test should produce a corrective action before retesting.

---

## Evidence Requirements

Each test record should include:

- Test identifier
- Date and location
- Objective
- Aircraft configuration
- Procedure
- Environmental conditions
- Results
- Pass or fail status
- Anomalies
- Corrective actions
- Associated logs, photographs, measurements, or configuration files

Evidence should make it possible for another person to understand what was tested and why the conclusion was reached.

---

## Post-Test Review

After each test:

1. Inspect the aircraft.
2. Preserve logs and configuration files.
3. Record anomalies.
4. Compare results with pass criteria.
5. Identify corrective actions.
6. Update documentation when the aircraft or procedure changed.
7. Decide whether the next test stage is authorized.

Do not rely on memory to reconstruct test results later.

---

## Regression Testing

Repeat affected tests whenever changes are made to:

- Propulsion
- Servos or linkages
- Flight-controller mounting
- Power system
- GPS or compass
- RC receiver
- Firmware
- Parameters
- Mission logic
- Aircraft mass
- Center of gravity

The scope of regression testing should match the risk introduced by the change.

---

## Revision Policy

Update this document when verification methods, pass criteria, or test sequencing change.

Update [components.md](components.md) when hardware changes.

Update [build.md](build.md) when assembly or configuration changes.

Record significant engineering decisions in [decisions.md](decisions.md).

The test plan should always describe how the current reference aircraft is verified.
