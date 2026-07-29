# MP-1 Electrical Power Architecture

**Document ID:** MP1-ARCH-ELECTRICAL-POWER  
**Revision:** 2  
**Status:** Draft  
**Author:** Project Meadowlark  
**Last Updated:** 2026-07-29  
**Evidence Level:** E1 — Preliminary Architecture

## Purpose

This document defines the electrical power architecture for the MP-1 initial-flight configuration.

The architecture is intentionally limited to the equipment required for:

- Manual takeoff
- Manual and stabilized flight
- Onboard execution of a pre-programmed waypoint mission
- Return-to-launch
- RC pilot takeover
- Manual landing
- Telemetry
- Flight logging
- Controlled engineering verification

The initial architecture does not include a companion computer, payload battery, payload regulator, mission-equipment power distribution, or redundant avionics power system.

Detailed component comparisons, procurement rankings, connector pin assignments, wiring drawings, harness definitions, and verification procedures are maintained separately.

## Governing Decision

This architecture implements:

```text
docs/platforms/mp-1/edr/edr-0001-initial-flight-baseline.md
```

The governing design principle is:

> MP-1 shall use the simplest flight-critical architecture that safely reproduces the Flightory-style aircraft and supports onboard autonomous waypoint navigation without a companion computer.

## Scope

This document covers electrical power for:

- Main flight battery
- Propulsion ESC
- Propulsion motor
- Flight controller
- Flight-controller power module
- Control-surface servos
- RC receiver
- GPS and compass
- Telemetry radio
- Required flight sensors
- Flight-critical wiring and connectors

This document does not yet define:

- Final power-module selection
- Final power-module current-path rating
- Final connector pin assignments
- Final wire gauges
- Fuse or circuit-protection ratings
- Detailed wiring-harness routing
- Final grounding and shielding layout
- Final component placement
- Final cooling provisions
- Final service-loop lengths
- Final physical and electrical interface matrix

These details shall be completed after the remaining initial-flight components are selected.

---

# Current Reference Components

| Function | Reference Component | Status |
|----------|---------------------|--------|
| Main Battery | Tattu G-Tech 4S 5200 mAh 35C LiPo with XT60 | Provisional |
| Propulsion Motor | T-Motor F90 2806.5 1300KV | Provisional |
| Propulsion ESC | Hobbywing Skywalker 50A V2 | Provisional |
| Flight Controller | Holybro Pixhawk 6C Mini | Provisional |
| Flight Servos | Corona DS929MG | Provisional |
| Flight-Controller Power Module | To Be Selected | Research |
| Servo-Power Source | Hobbywing Skywalker 50A V2 integrated 5 V/5 A BEC | Provisional |
| GPS / Compass | To Be Selected | Pending |
| RC Receiver | To Be Selected | Pending |
| Telemetry Radio | To Be Selected | Pending |
| Airspeed Sensor | To Be Determined by Test Plan | Pending |

---

# Initial Flight-Critical Boundary

The initial flight-critical electrical system includes:

- One removable 4S flight battery
- One propulsion ESC
- One propulsion motor
- One flight-controller power module
- One flight controller
- One servo-power source
- Three primary flight servos
- One RC receiver
- One GPS and compass system
- One telemetry radio
- Required antennas
- Required flight sensors
- Required wiring, connectors, and mounts

The initial configuration excludes:

- Companion computer
- Payload computer
- Payload battery
- Payload regulator
- Mission-equipment power distribution
- Camera payload
- Experimental payload sensors
- Redundant flight-controller supply
- Redundant servo-power supply
- Nonessential radios

No excluded subsystem shall be required for manual flight, autonomous waypoint navigation, return-to-launch, pilot takeover, or safe landing.

---

# Architectural Principles

The MP-1 initial electrical architecture follows these principles:

1. Simplicity is preferred over unnecessary complexity.
2. The flight controller shall execute waypoint missions onboard.
3. The flight-critical system shall not depend on a companion computer.
4. The flight-critical system shall not depend on payload power.
5. The main battery shall remain directly exchangeable without rewiring the aircraft.
6. The battery interface shall remain standardized on XT60.
7. Flight-controller logic power shall be separate from servo-rail power.
8. The flight controller shall remain powered during normal servo and throttle transients.
9. The selected power module shall measure main-battery voltage and propulsion current.
10. The selected ESC BEC shall power the servo rail unless verification shows inadequate performance.
11. No parallel BEC connection shall be permitted unless the devices are explicitly designed for parallel operation.
12. Future mission equipment shall be added through a separate architecture revision.
13. Final harnesses shall minimize unnecessary adapters.
14. Connector polarity, gender, and pin assignments shall be documented.
15. The physical and electrical interface matrix shall be completed after the full initial procurement set is selected.
16. Verification shall demonstrate voltage stability, current margin, thermal margin, noise tolerance, and failsafe behavior.

---

# Electrical Power Domains

The initial MP-1 architecture contains three power domains.

## 1. Main Battery Domain

The main battery is a removable 4S LiPo pack.

| Parameter | Requirement |
|-----------|-------------|
| Chemistry | Conventional LiPo |
| Cell Count | 4S |
| Nominal Voltage | 14.8 V |
| Maximum Charged Voltage | 16.8 V |
| Main Connector | XT60 |
| Reference Capacity | Approximately 5,200 mAh |
| Normal Evaluation Range | 5,000–6,000 mAh |
| Reference Pack | Tattu G-Tech 4S 5200 mAh 35C |
| Normal Adapter Use | Not permitted |

The battery supplies:

- The propulsion power path
- The flight-controller power-module path
- The ESC BEC input through the propulsion ESC

## 2. Propulsion and Servo Domain

The propulsion and servo domain contains:

- Main battery
- Propulsion ESC
- Brushless motor
- Propeller
- ESC integrated BEC
- Servo rail
- Flight servos
- RC receiver, if powered from the servo rail

The reference ESC is the Hobbywing Skywalker 50A V2.

The ESC performs two electrical functions:

1. Converts battery power into three-phase motor power.
2. Converts battery power into regulated 5 V servo-rail power through its integrated 5 V/5 A switching BEC.

The ESC BEC is the baseline servo-power source for the initial MP-1 build.

This arrangement remains provisional until bench verification confirms adequate current margin, voltage stability, noise performance, and thermal performance.

## 3. Flight Avionics Domain

The flight avionics domain is centered on the Holybro Pixhawk 6C Mini.

The Pixhawk shall receive regulated primary power through a compatible external analog power module.

The flight avionics domain includes:

- Flight controller
- GPS and compass
- Telemetry radio
- Required flight sensors
- Battery voltage sensing
- Battery current sensing
- Flight logging

The flight-controller power module shall provide:

- Regulated flight-controller power
- Main-battery voltage measurement
- Main-battery current measurement
- Compatibility with the Pixhawk 6C Mini analog power input
- Adequate current-path capability for the propulsion system
- Adequate current-sensor range
- Manufacturer-documented calibration values or an approved calibration procedure
- A keyed and documented flight-controller harness

The exact power module remains under evaluation.

---

# High-Level Architecture

```text
                         MP-1 4S LiPo Battery
                          14.8 V nominal
                                 │
                                 │
                ┌────────────────┴────────────────┐
                │                                 │
                │                                 │
       Propulsion / Servo Path          Flight Avionics Path
                │                                 │
                │                                 │
      Hobbywing Skywalker 50A V2         External Power Module
                │                                 │
       ┌────────┴─────────┐                       ├── Regulated FC power
       │                  │                       ├── Battery-voltage sense
       │                  │                       └── Battery-current sense
       │                  │                                  │
 T-Motor F90 Motor   Integrated 5 V/5 A BEC                  │
                          │                                   │
                          │                                   │
                    Servo Power Rail                          │
                          │                                   │
             ┌────────────┼────────────┐                      │
             │            │            │                      │
       Left Aileron  Right Aileron  Elevator                  │
          Servo          Servo        Servo                   │
             │            │            │                      │
             └────────────┴────────────┴──────────┐           │
                                                  │           │
                                           Holybro Pixhawk 6C Mini
                                                  │
                   ┌──────────────────────────────┼──────────────────────────────┐
                   │                              │                              │
                   │                              │                              │
              RC Receiver                  GPS / Compass                 Telemetry Radio
                                                  │
                                            Required Sensors
                                                  │
                                      Onboard ArduPlane Mission
```

No companion-computer branch or payload-power branch is installed in the initial configuration.

---

# Flight-Controller Power Architecture

## Primary Logic Power

The Pixhawk 6C Mini shall receive regulated primary power through its analog power input using a compatible external power module.

The flight-controller logic-power path shall not depend solely on the servo rail.

This separation is required so that:

- Normal servo transients do not directly disturb flight-controller logic power
- Servo-rail faults do not automatically remove autopilot power
- Battery voltage and current sensing remain available
- The servo-power source can be changed later without replacing the flight controller
- Onboard mission execution remains isolated from ordinary servo load changes

## Power-Module Current Path

The selected power module may be placed in series with the main battery and ESC power path.

If so, the following shall be verified:

- Continuous current rating
- Burst current rating
- Connector current rating
- Wire-gauge current rating
- Voltage drop
- Thermal performance
- Current-sensor calibration
- Compatibility with the selected propeller and measured motor current

A power module shall not be accepted merely because its current sensor can measure the expected load. The complete current path, including connectors and wire, shall support the verified propulsion current.

## Flight-Controller Loads

The flight-controller logic supply may power:

- Pixhawk 6C Mini
- GPS and compass
- Telemetry radio, if permitted by the selected hardware
- Required low-power flight sensors

Servo loads shall not be powered from the flight-controller logic-power output.

---

# Servo-Power Architecture

## Baseline Source

The Hobbywing Skywalker 50A V2 integrated 5 V/5 A switching BEC is the baseline servo-power source.

It shall supply:

- Left aileron servo
- Right aileron servo
- Elevator servo
- RC receiver, if the selected receiver is assigned to the servo rail

## Servo-Load Basis

Published normal operating current for the Corona DS929MG is substantially below the BEC rating when three servos are considered together.

Published servo stall current is not available.

The servo-power design therefore remains provisional until measured testing confirms transient performance under realistic mechanical loading.

## Acceptance Criteria

The ESC BEC shall remain the baseline servo-power source only if testing confirms:

- Servo rail remains within the servo operating-voltage range
- Servo rail remains above 4.8 V during simultaneous rapid servo movement
- No Pixhawk reset occurs
- No receiver reset occurs
- No GPS or telemetry reset occurs
- No unacceptable control-surface jitter occurs
- No unacceptable voltage sag occurs during rapid throttle changes
- No unacceptable electrical noise is introduced
- ESC and BEC temperature remain within acceptable limits
- Loaded operation remains stable for the required test duration

## External BEC Contingency

A dedicated external BEC may be introduced only if:

- The ESC BEC fails verification
- Additional servos increase the servo-rail load
- Later flight-critical equipment requires greater current
- Fault separation becomes a formal requirement

If an external BEC is installed:

- The ESC BEC positive lead shall be removed or isolated
- The ESC throttle signal and ground shall remain connected
- Only one BEC positive output shall feed the servo rail
- Reverse-current and backfeed behavior shall be verified
- The architecture change shall be documented

A dedicated external BEC is not part of the initial baseline.

---

# Autonomous Mission Power Requirement

Onboard autonomous waypoint navigation shall remain available whenever the flight-critical power system is operating.

The power architecture shall support:

- Flight-controller operation
- GPS and compass operation
- RC receiver operation
- Servo operation
- Battery monitoring
- Flight logging
- Telemetry operation, when the link is available

The aircraft shall not require telemetry power to continue an already loaded waypoint mission.

The aircraft shall not require companion-computer power for:

- Mission storage
- Waypoint sequencing
- Navigation
- Return-to-launch
- Pilot takeover
- Flight logging

---

# Telemetry Power Role

Telemetry is included in the initial flight-test configuration for:

- Ground monitoring
- Mission upload
- Parameter review
- Status reporting
- Test observation

Telemetry is not a control dependency for an already loaded mission.

Loss of telemetry shall not:

- Remove RC control
- Remove pilot takeover
- Stop onboard mission execution unless explicitly required by configured failsafe logic
- Remove GPS or flight-controller power
- Remove servo power

---

# Power Monitoring Requirements

The selected power module shall measure:

- Main battery voltage
- Main propulsion current
- Estimated consumed capacity
- Remaining battery percentage through flight-controller estimation

The current sensor and current path shall support the verified propulsion load with documented engineering margin.

Initial design targets are:

| Parameter | Target |
|-----------|--------|
| Battery Voltage Range | Must safely include 16.8 V |
| Continuous Current Path | Must exceed verified sustained propulsion current |
| Burst Current Path | Must exceed verified takeoff and climb current |
| Current Sensor Range | Must include verified peak propulsion current |
| Flight-Controller Interface | Pixhawk 6C Mini analog power interface |
| Connector System | Keyed and documented where practical |
| Calibration | Supported by ArduPlane |
| Installed Voltage Drop | Minimized and measured |
| Thermal Margin | Verified under static propulsion load |
| Logging | Voltage and current values recorded in flight logs |

Static propulsion testing shall determine the final current requirement.

---

# Grounding and Noise Control

The final harness shall use a controlled common electrical reference while minimizing high-current noise coupling into avionics.

The design shall:

- Keep battery, ESC, and motor wiring separated from GPS, compass, receiver, telemetry, and sensor wiring
- Keep motor phase leads as short as practical
- Avoid unnecessary ground loops
- Route analog sense wiring away from motor leads
- Use signal-and-ground pairs where appropriate
- Use the manufacturer-supplied power-module harness where practical
- Mount the compass away from battery, ESC, motor wiring, and current-sensor conductors
- Avoid unsupported parallel BEC outputs
- Prevent power backfeed through telemetry, USB, receiver, or sensor connections
- Verify flight-controller stability during rapid throttle changes
- Verify GPS and compass performance with propulsion operating

Detailed grounding and electromagnetic-compatibility requirements shall be documented during harness design.

---

# Connector Strategy

The initial connector strategy is:

| Interface | Connector Strategy |
|-----------|--------------------|
| Battery to Aircraft | XT60 |
| Battery Balance | JST-XH |
| Battery to ESC / Power Module | XT60-compatible documented path |
| ESC to Motor | Matching bullet connectors or documented direct connection |
| Power Module to Flight Controller | Manufacturer-compatible keyed harness |
| Pixhawk Peripheral Ports | JST-GH manufacturer-standard harnesses |
| Servo Connections | JR/Futaba-compatible three-pin connectors |
| GPS / Compass | Pixhawk-compatible keyed harness |
| RC Receiver | Protocol-specific keyed or documented harness |
| Telemetry Radio | Pixhawk-compatible serial harness |
| Future Mission Equipment | Not installed in initial configuration |

Commercially available adapters may be used during development only when:

- Pin assignments are verified
- Voltage compatibility is documented
- Connector gender is documented
- The adapter is mechanically secure
- The adapter does not create an ambiguous connection
- The adapter is recorded in the interface matrix

The final aircraft harness shall minimize adapter chains.

---

# Fault-Containment Goals

The initial architecture shall support the following behavior:

| Fault | Desired Result |
|-------|----------------|
| Servo transient | Flight controller remains powered |
| Servo overload | Flight controller remains powered if practical |
| ESC BEC failure | Loss of servo power may occur, but flight-controller logic remains powered |
| Power-module regulator failure | Flight-controller loss is recognized as a flight-critical single-point failure |
| Power-module sensing failure | Flight-controller behavior is defined and logged where possible |
| ESC propulsion shutdown | Flight controller, receiver, GPS, and telemetry remain powered if the main battery and power module remain functional |
| Motor stall | ESC protection operates without damaging avionics |
| RC receiver loss | Flight controller executes configured failsafe |
| GPS loss | Flight controller executes configured navigation failsafe |
| Telemetry loss | RC control and onboard mission execution remain available |
| Future non-flight-critical system loss | No effect on initial flight-critical power |
| Battery disconnect | Complete system shutdown with no unsafe backfeed path |

The initial configuration does not provide complete redundancy. All single-point failures shall be documented and tested where practical.

---

# Deferred Mission-Equipment Power Domain

No mission-equipment power domain shall be installed in the initial MP-1 configuration.

A future mission-equipment power domain may support:

- Companion computer
- Camera
- Payload sensors
- Additional radios
- Mission processor
- Other non-flight-critical equipment

Future mission-equipment power shall:

- Be documented through a new architecture revision
- Not become a dependency of manual flight
- Not become a dependency of onboard waypoint navigation
- Not become a dependency of return-to-launch
- Not remove power from the flight controller, receiver, GPS/compass, or servos when it fails
- Include defined signal-ground and backfeed controls
- Include independent current, thermal, and connector analysis
- Be recorded in a new EDR if it materially changes the platform architecture

---

# Remaining Power-System Decisions

The following decisions remain open:

1. Select the external Pixhawk-compatible analog power module.
2. Confirm the power-module continuous and burst current path.
3. Confirm current-sensor range and calibration.
4. Confirm the exact ESC BEC wiring into the servo rail.
5. Confirm receiver power-source assignment.
6. Confirm total servo and receiver current.
7. Confirm servo-rail voltage under load.
8. Confirm connector types and genders.
9. Define wire gauges.
10. Define protection devices and ratings.
11. Define grounding and shielding.
12. Define physical routing and mounting.
13. Confirm cooling requirements.
14. Complete the physical and electrical interface matrix.
15. Create the detailed wiring diagram.
16. Create the electrical verification procedure.

Redundant power, payload power, and companion-computer power are not open initial-build decisions. They are deferred capabilities.

---

# Verification Requirements

The completed initial electrical system shall be verified through inspection, analysis, demonstration, and test.

Minimum verification activities include:

1. Inspect all connector polarity and pin assignments.
2. Confirm exact power-module model and revision.
3. Confirm power-module harness compatibility.
4. Measure battery voltage at each power-domain input.
5. Confirm Pixhawk logic voltage.
6. Confirm servo-rail voltage unloaded.
7. Confirm servo-rail voltage during simultaneous servo movement.
8. Confirm receiver voltage.
9. Confirm GPS and telemetry power stability.
10. Calibrate voltage sensing.
11. Calibrate current sensing.
12. Measure idle avionics current.
13. Measure servo transient current.
14. Measure static propulsion current.
15. Measure voltage drop across the power module and connectors.
16. Measure voltage sag during motor acceleration.
17. Measure ESC, BEC, power-module, connector, and wire temperature.
18. Confirm no Pixhawk reset during servo transients.
19. Confirm no Pixhawk reset during rapid throttle changes.
20. Confirm no receiver reset during servo transients.
21. Confirm no GPS or telemetry reset during throttle changes.
22. Confirm voltage and current logging.
23. Confirm low-voltage warnings and failsafe thresholds.
24. Confirm RC-loss failsafe.
25. Confirm GPS-loss response.
26. Confirm telemetry-loss behavior.
27. Confirm onboard mission execution without an active telemetry link.
28. Confirm return-to-launch.
29. Confirm pilot takeover.
30. Confirm the battery can be replaced without altering other hardware.
31. Archive logs, calibration values, measurements, photographs, and configuration records.

---

# Related Documentation

```text
docs/platforms/mp-1/requirements/initial-flight-requirements.md
docs/platforms/mp-1/edr/edr-0001-initial-flight-baseline.md
docs/platforms/mp-1/procurement/approved-components.md
docs/platforms/mp-1/procurement/procurement-matrix.md
docs/platforms/mp-1/procurement/vendor-notes.md
```

The future physical and electrical interface matrix shall reside under:

```text
docs/platforms/mp-1/interfaces/
```

Detailed electrical verification procedures and results shall reside under:

```text
docs/platforms/mp-1/verification/
```

---

# Revision History

## Revision 2

- Aligned the architecture with EDR-0001.
- Defined the minimal initial flight-critical system boundary.
- Required onboard execution of pre-programmed waypoint missions.
- Removed companion-computer power from the initial architecture.
- Removed payload power from the initial architecture.
- Removed redundant avionics power from the initial architecture.
- Established the ESC integrated 5 V/5 A BEC as the provisional baseline servo-power source.
- Retained a dedicated external BEC only as a contingency.
- Defined telemetry as a test and monitoring system rather than a mission-execution dependency.
- Added explicit autonomous-mission power requirements.
- Added a deferred future mission-equipment power domain.
- Updated fault-containment and verification requirements.

## Revision 1

- Added the selected 4S LiPo battery architecture.
- Added the Tattu G-Tech 4S 5200 mAh reference battery.
- Added the Hobbywing Skywalker 50A V2 reference ESC.
- Added the T-Motor F90 2806.5 1300KV reference motor.
- Added the Holybro Pixhawk 6C Mini reference flight controller.
- Separated propulsion, flight-controller logic, servo, and peripheral power domains.
- Defined the requirement for an external Pixhawk-compatible power module.
- Added preliminary power-monitoring requirements.
- Added connector, grounding, fault-containment, and verification requirements.

## Revision 0

- Initial high-level electrical power architecture established.
