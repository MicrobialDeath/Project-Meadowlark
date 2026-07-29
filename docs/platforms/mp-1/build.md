# MP-1 Build Guide

**Status:** Draft  
**Last Updated:** 2026-07-29

## Purpose

This document explains how to assemble, wire, configure, and prepare Meadowlark Platform 1 (MP-1) for ground testing and flight.

It is intended to make the aircraft reproducible for a future builder who has access to the selected components, the Flightory LARK reference material, and this repository.

This guide is incomplete until all remaining components are selected and the first aircraft has been assembled and tested.

---

# Build Scope

The initial MP-1 build includes:

- Flightory LARK airframe
- Three control-surface servos
- Propulsion motor
- Propeller
- Electronic speed controller
- 4S flight battery
- Flight-controller power module
- Holybro Pixhawk 6C Mini
- GPS and compass
- RC receiver
- Telemetry radio
- Required wiring, connectors, antennas, mounts, and fasteners
- ArduPlane firmware
- Approved parameter file
- Approved waypoint mission

The initial build excludes:

- Companion computer
- Payload computer
- Payload battery
- Payload regulator
- Mission payload
- Redundant avionics power
- Redundant servo power
- Autonomous takeoff hardware
- Autonomous landing hardware

---

# Prerequisites

Before assembly begins:

1. Review `design.md`.
2. Review `components.md`.
3. Confirm that each selected component matches the exact manufacturer and model.
4. Record the hardware revision where applicable.
5. Inspect all parts for damage.
6. Record measured mass for each major component.
7. Confirm connector types and wire polarity.
8. Confirm that no required adapter chain has been introduced.
9. Confirm that the airframe parts match the Flightory LARK reference geometry.
10. Create a build record for the specific aircraft.

Recommended aircraft identifier:

```text
MP1-A01
```

Use a new identifier for each separately assembled aircraft.

---

# Required Tools

The exact tool list may change, but the initial build is expected to require:

- Metric ruler or calipers
- Digital scale
- Soldering iron
- Solder
- Flux
- Heat-shrink tubing
- Wire cutters
- Wire strippers
- Crimping tools appropriate to the selected connectors
- Multimeter
- Servo tester or receiver test setup
- Hex drivers
- Small screwdrivers
- Thread-locking compound suitable for metal fasteners
- Adhesive suitable for the airframe material
- Double-sided mounting tape
- Hook-and-loop straps
- Cable ties
- Labeling materials
- Propeller balancer
- Battery charger with LiPo balance mode
- Computer with Mission Planner or another supported ArduPilot ground station

Do not use thread-locking compound on plastic unless the product is explicitly safe for that plastic.

---

# Build Record

Create a build record under:

```text
docs/platforms/mp-1/evidence/builds/
```

Suggested file name:

```text
mp1-a01-build-record.md
```

Record:

- Aircraft identifier
- Build date
- Builder
- Airframe revision
- Component models
- Hardware revisions
- Serial numbers
- Measured component masses
- Connector details
- Wire lengths
- Mounting methods
- Firmware version
- Parameter-file version
- Calibration dates
- Photographs
- Deviations from this guide

Any deviation that changes the aircraft architecture should also be recorded in `decisions.md`.

---

# Airframe Preparation

## Reference Material

Use the Flightory LARK reference files for:

- Airframe geometry
- Printed parts
- Control-surface arrangement
- Motor-mount location
- Servo placement
- Battery location
- Center-of-gravity guidance
- Assembly sequence

Third-party reference files should remain under:

```text
references/flightory-lark/
```

Do not modify third-party source files in place. Store Meadowlark-specific derivatives or replacements under the appropriate `hardware/` path.

## Initial Inspection

Before installing electronics:

1. Inspect all airframe parts.
2. Confirm left and right parts are not reversed.
3. Confirm control surfaces move freely.
4. Confirm hinges are secure.
5. Confirm pushrod paths are unobstructed.
6. Confirm the motor mount is rigid.
7. Confirm the battery bay is accessible.
8. Confirm planned avionics locations are serviceable.
9. Confirm antenna locations are clear of moving parts.
10. Confirm the GPS and compass location is separated from high-current wiring.

Record any airframe modification in the build record.

---

# Servo Installation

The initial aircraft uses three primary flight servos:

- Left aileron
- Right aileron
- Elevator

## Installation Steps

1. Center each servo using a servo tester or receiver.
2. Record the servo’s neutral pulse setting if available.
3. Install the servo arm as close to mechanically centered as possible.
4. Mount each servo securely.
5. Route the servo lead without sharp bends or contact with moving parts.
6. Install the control linkage.
7. Confirm the linkage does not bind.
8. Confirm the control surface reaches the required travel.
9. Confirm the servo does not reach its mechanical stop before the commanded endpoint.
10. Label each servo lead.

Recommended labels:

```text
AIL-L
AIL-R
ELEV
```

## Initial Checks

Before connecting to the Pixhawk:

- Verify neutral position
- Verify direction
- Verify full travel
- Check for binding
- Check for excessive gear play
- Check for unusual sound
- Check no-load current if practical

Do not finalize control-surface direction using mechanical reversal alone. Final direction must also be verified in the flight-controller configuration.

---

# Motor Installation

## Installation Steps

1. Confirm the motor model and KV.
2. Inspect shaft, bell, bearings, and windings.
3. Confirm motor-mount hole spacing.
4. Confirm the mounting screws do not contact the windings.
5. Apply appropriate thread-locking compound to metal-to-metal fasteners.
6. Install the motor.
7. Confirm the bell rotates freely.
8. Route motor wires away from sharp edges.
9. Leave enough service length to disconnect the ESC.
10. Secure the wires so they cannot contact the rotating motor.

Do not install the propeller during electrical setup.

---

# ESC Installation

## Installation Steps

1. Confirm the exact ESC model.
2. Confirm battery input polarity.
3. Confirm motor-phase wire connections.
4. Confirm the throttle signal, positive BEC lead, and ground positions.
5. Mount the ESC where airflow is available.
6. Keep the ESC away from the GPS and compass.
7. Secure the ESC without crushing the case.
8. Route battery and motor wiring separately from signal wiring where practical.
9. Label the battery input and motor outputs.
10. Confirm the BEC lead will reach the selected servo-rail connection.

Recommended labels:

```text
ESC-BATT
ESC-M1
ESC-M2
ESC-M3
ESC-SIGNAL
```

The ESC’s integrated BEC is the initial servo-power source.

Do not connect a second BEC positive output to the same servo rail.

---

# Power Module Installation

The final power module is not yet selected.

The leading candidate is the Holybro PM02 V3.

## Installation Requirements

The selected power module must be installed so that:

- Battery polarity is unambiguous
- XT60 connector gender and orientation are documented
- Current flows through the intended sensing path
- The Pixhawk power cable is keyed and secure
- The power module is protected from mechanical strain
- The board is not exposed to conductive debris
- High-current wiring is kept away from the GPS and compass
- The module remains accessible for inspection
- Wire and connector temperatures can be checked during testing

## Required Records

Record:

- Power-module model
- Hardware revision
- Wire gauge
- Wire length
- Connector gender
- Connector orientation
- Harness pinout
- Installed location
- Mounting method

Do not finalize the installation until propulsion-current testing confirms that the complete current path is adequate.

---

# Flight Controller Installation

## Orientation

Install the Pixhawk 6C Mini:

- Rigidly enough to prevent movement
- With appropriate vibration isolation
- In a known orientation
- Away from direct motor and ESC vibration
- Away from high-current wiring where practical
- Where the microSD card remains accessible
- Where connectors can be serviced
- Where airflow is adequate

Record the installed orientation.

If the flight controller is not installed in the default forward-facing orientation, configure the board orientation parameter accordingly and document it.

## Mounting

Use a mounting method that:

- Does not flex excessively
- Does not allow the controller to shift
- Does not place stress on JST-GH connectors
- Does not trap excessive heat
- Allows removal without damaging the airframe

## Connections

The expected initial connections are:

| Pixhawk Function | Connected Device |
|------------------|------------------|
| POWER1 | Selected analog power module |
| MAIN PWM outputs | Servos and ESC throttle |
| GPS port | GPS and compass unit |
| RC input or serial receiver port | RC receiver |
| Telemetry port | Telemetry radio |
| microSD | Flight logging |

Exact ports and pinouts must be recorded after the remaining components are selected.

---

# Servo-Rail Wiring

The Pixhawk PWM rail distributes control signals but does not generate servo power.

The initial servo rail is powered by the Skywalker ESC BEC.

## Baseline Arrangement

The ESC throttle connector provides:

- Throttle signal
- 5 V BEC output
- Ground

The BEC output energizes the servo rail.

The servos connect to the same rail.

## Required Checks

Before connecting the flight controller:

1. Confirm BEC polarity.
2. Measure BEC voltage.
3. Confirm output is approximately 5 V.
4. Confirm no other positive power source is connected to the rail.
5. Confirm servo connector polarity.
6. Confirm signal and ground continuity.
7. Confirm the ESC cannot backfeed the flight-controller primary power input through an unintended path.

If a future external BEC is installed, isolate the ESC BEC positive lead.

---

# RC Receiver Installation

The receiver has not yet been selected.

Install the selected receiver so that:

- Antennas are clear of carbon, battery wiring, and metal shielding
- Antenna elements are oriented according to manufacturer guidance
- The receiver is secured
- The signal protocol is documented
- The power source is documented
- The receiver remains accessible for binding or firmware updates
- The receiver does not depend on the telemetry radio

Record:

- Receiver model
- Firmware version
- Bound transmitter
- Protocol
- Port
- Power source
- Antenna orientation
- Failsafe configuration

---

# GPS and Compass Installation

The GPS and compass unit has not yet been selected.

Install the unit:

- With a clear view of the sky
- Away from the motor
- Away from the ESC
- Away from battery and motor-current wiring
- Away from magnets and steel fasteners where practical
- In a known orientation
- On a rigid mount
- Where the cable cannot pull on the connector

Record:

- GPS model
- Compass model
- Firmware version if applicable
- Installed orientation
- Cable length
- Pixhawk port
- Mounting location
- Measured compass offsets after calibration

---

# Telemetry Radio Installation

The telemetry system has not yet been selected.

Install the aircraft radio so that:

- Antenna placement follows manufacturer guidance
- The antenna is separated from the RC receiver antennas where practical
- The radio is secured
- The serial connection is documented
- Voltage requirements are confirmed
- Cable strain is relieved
- The radio can be disconnected for troubleshooting

Telemetry is used for test monitoring and setup. The aircraft must continue an already loaded mission without the link.

---

# Battery Installation

## Mechanical Requirements

The battery must:

- Fit without compressing cells
- Be restrained in every direction
- Be removable without disturbing avionics
- Use the common XT60 interface
- Remain clear of sharp edges
- Permit center-of-gravity adjustment
- Avoid contact with hot components
- Avoid pulling on the power-module or ESC wiring

Use at least one positive restraint method in addition to friction.

## Battery Identification

Assign each battery a unique identifier.

Suggested format:

```text
MP1-BAT-001
```

Record:

- Manufacturer
- Model
- Purchase date
- Initial cell voltages
- Measured mass
- Cycle count
- Storage condition
- Retirement date and reason

---

# Propeller Installation

Do not install the propeller until:

- Motor direction is confirmed
- ESC setup is complete
- Throttle failsafe is configured
- The aircraft is restrained for testing
- The propeller has been balanced
- Propeller orientation is confirmed
- Hub and adapter fit are confirmed

After installation:

1. Confirm clearance.
2. Confirm rotation direction.
3. Confirm fastener security.
4. Mark the fastener position if useful for visual inspection.
5. Reinspect after the first ground run.

Treat an installed propeller as an active hazard whenever the battery is connected.

---

# Firmware Installation

The reference firmware is ArduPlane.

## Initial Setup

1. Install a current supported ArduPlane release for the Pixhawk 6C Mini.
2. Record the exact firmware version.
3. Erase or reset parameters only when intended.
4. Save a parameter backup after initial setup.
5. Save a new parameter backup after each major configuration milestone.

Suggested repository location:

```text
software/config/mp-1/
```

Suggested names:

```text
mp1-a01-baseline.param
mp1-a01-first-flight.param
mp1-a01-waypoint-test.param
```

Do not overwrite prior known-good parameter files.

---

# Initial Flight-Controller Configuration

Configure and record:

- Board orientation
- Accelerometer calibration
- Compass calibration
- Radio calibration
- Servo output functions
- Servo directions
- Servo endpoints
- Servo trims
- Throttle range
- Flight modes
- Battery monitor
- Voltage calibration
- Current calibration
- GPS configuration
- Home-position behavior
- Geofence
- RC-loss failsafe
- GPS-loss response
- Low-battery warning and failsafe
- Telemetry port
- Logging
- Return-to-launch altitude and behavior

Do not copy a parameter file from another aircraft without reviewing every safety-critical parameter.

---

# Servo Output Assignment

The final channel assignment must be recorded.

A likely initial assignment is:

| Function | Output |
|----------|--------|
| Left Aileron | To be assigned |
| Right Aileron | To be assigned |
| Elevator | To be assigned |
| Throttle | To be assigned |

After assignment:

1. Confirm each output controls the intended device.
2. Confirm each control surface moves in the correct direction.
3. Confirm stabilization corrections move in the correct direction.
4. Confirm throttle output is inhibited when required.
5. Record the final assignment in the build record.

---

# Initial Mission File

Store approved mission files under:

```text
software/missions/mp-1/
```

Suggested file name:

```text
mp1-a01-initial-waypoint-test.waypoints
```

The initial mission should be deliberately conservative.

It should include:

- A route within visual range
- Safe altitude
- Wide turns
- Few waypoints
- Clear separation from obstacles
- A return-to-launch contingency
- No autonomous takeoff
- No autonomous landing

Record:

- Mission file version
- Test location
- Planned altitude
- Waypoint coordinates
- Expected sequence
- Geofence
- RTL altitude
- Weather limits

---

# Pre-Power Inspection

Before first power:

1. Remove the propeller.
2. Confirm battery polarity.
3. Confirm XT60 polarity.
4. Confirm power-module orientation.
5. Confirm Pixhawk power-cable pinout.
6. Confirm servo connector polarity.
7. Confirm no exposed conductors.
8. Confirm no loose hardware.
9. Confirm no wire can contact the motor.
10. Confirm only one BEC positive source feeds the servo rail.
11. Confirm the flight-controller mount is secure.
12. Confirm the microSD card is installed.
13. Confirm all antennas are connected where required.
14. Confirm the battery is not connected.

---

# First Power-Up

Use a current-limited source or appropriate smoke-stopper where practical during the first low-power check.

With the propeller removed:

1. Connect the battery.
2. Watch for smoke, heat, odor, or abnormal sound.
3. Confirm flight-controller boot.
4. Confirm BEC voltage.
5. Confirm servo-rail voltage.
6. Confirm receiver power.
7. Confirm GPS power.
8. Confirm telemetry power.
9. Confirm no component heats unexpectedly.
10. Disconnect power if any abnormal condition appears.

Record measured voltages.

---

# Bench Configuration Checks

With the propeller removed:

1. Confirm RC input.
2. Confirm flight-mode switch positions.
3. Confirm servo output assignments.
4. Confirm servo directions.
5. Confirm stabilization directions.
6. Confirm throttle output.
7. Confirm motor direction at low power.
8. Confirm GPS detection.
9. Confirm compass detection.
10. Confirm telemetry.
11. Confirm battery-voltage reading.
12. Confirm current reading at idle.
13. Confirm logging.
14. Confirm arming checks.
15. Confirm failsafe configuration.

Do not bypass arming checks merely to accelerate the build.

---

# Cable Management

Final cable management should:

- Leave service loops where necessary
- Avoid tension on JST-GH connectors
- Keep wires clear of control linkages
- Keep high-current wiring separated from sensor wiring
- Avoid sharp bends
- Avoid unsupported heavy connectors
- Permit battery removal
- Permit Pixhawk removal
- Permit microSD access
- Permit visual inspection
- Use labels that remain readable

Do not permanently close the airframe until wiring has passed inspection and bench testing.

---

# Mass and Center of Gravity

After assembly:

1. Measure total aircraft mass without the battery.
2. Measure battery mass.
3. Measure ready-to-fly mass.
4. Record the center of gravity.
5. Confirm the center of gravity remains within the Flightory reference range.
6. Confirm the battery can be adjusted without stressing wiring.
7. Record the final battery position.

Repeat the center-of-gravity check after any component change.

---

# Build Completion Criteria

The aircraft is mechanically and electrically complete when:

- All selected components are installed
- All connectors are labeled
- All pinouts are recorded
- All wires are secured
- The battery is restrained
- The center of gravity is documented
- The flight controller is configured
- The receiver is bound
- GPS and compass are detected
- Telemetry is operational
- Servo directions are correct
- Stabilization directions are correct
- Motor direction is correct
- Battery monitoring is calibrated
- Logging is operational
- Firmware and parameters are archived
- The build record is complete

Completion of the build does not authorize flight. Flight readiness is determined through `testing.md`.

---

# Open Build Items

The following details remain open:

1. Final propeller
2. Final power module
3. GPS and compass model
4. RC receiver model
5. Telemetry radio model
6. Airspeed-sensor decision
7. Exact PWM output mapping
8. Exact connector genders and pinouts
9. Final wire gauges
10. Final component locations
11. Final center-of-gravity target
12. Detailed airframe assembly notes
13. Final photographs and wiring diagram

---

# Related Documents

```text
docs/platforms/mp-1/README.md
docs/platforms/mp-1/design.md
docs/platforms/mp-1/components.md
docs/platforms/mp-1/testing.md
docs/platforms/mp-1/decisions.md
```

---

# Change History

## 2026-07-29

- Created the consolidated MP-1 build guide.
- Defined assembly, wiring, configuration, and recordkeeping expectations.
- Preserved the minimal initial-flight boundary.
- Added reproducibility requirements for firmware, parameters, mission files, photographs, and build records.
