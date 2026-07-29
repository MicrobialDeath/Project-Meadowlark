# MP-1 Electrical Power Architecture

**Status:** Draft  
**Revision:** 1  
**Evidence Level:** E1 — Preliminary Architecture

## Purpose

This document defines the current electrical power architecture for the MP-1 platform. It identifies the major electrical power domains, their relationships, current architectural decisions, and the unresolved selections that must be completed before detailed harness design.

Detailed component comparisons, procurement rankings, interface definitions, wiring diagrams, test procedures, and verification results are documented separately.

## Scope

This document covers the high-level distribution of electrical power to:

- Propulsion
- Flight controller
- Control-surface servos
- Navigation equipment
- Radio-control equipment
- Telemetry equipment
- Air-data and other sensors
- Future payloads
- Future companion-computer equipment

This document does not yet define:

- Final power-module model
- Final external BEC or servo regulator
- Final connector pin assignments
- Final wire gauges
- Fuse or circuit-protection ratings
- Detailed wiring-harness routing
- Final grounding and shielding strategy
- Final physical placement
- Final service-loop lengths
- Final physical and electrical interface matrix

Those details will be completed after the remaining MP-1 components are selected.

---

# Current Reference Components

| Function | Reference Component | Status |
|----------|---------------------|--------|
| Main Battery | Tattu G-Tech 4S 5200 mAh 35C LiPo with XT60 | Provisional |
| Propulsion Motor | T-Motor F90 2806.5 1300KV | Provisional |
| Propulsion ESC | Hobbywing Skywalker 50A V2 | Provisional |
| Flight Controller | Holybro Pixhawk 6C Mini | Provisional |
| Flight Servos | Corona DS929MG | Provisional |
| Power Module | To Be Selected | Research |
| Servo-Power Source | To Be Selected | Research |
| GPS / Compass | To Be Selected | Pending |
| RC Receiver | To Be Selected | Pending |
| Telemetry Radio | To Be Selected | Pending |
| Airspeed Sensor | To Be Selected | Pending |
| Companion Computer | Future Selection | Future Evaluation |

---

# Architectural Principles

The MP-1 power architecture follows these principles:

1. The propulsion and avionics power paths must be clearly separated.
2. The flight controller must not rely solely on the servo rail for primary logic power.
3. Servo power must be sized independently from flight-controller logic power.
4. The main battery must remain directly exchangeable without rewiring the aircraft.
5. The battery interface must remain standardized on XT60.
6. Power monitoring must measure the main battery voltage and propulsion-system current.
7. The architecture must support modular replacement of the battery, ESC, motor, flight controller, power module, receiver, GPS, and telemetry radio.
8. Wiring and connectors must be documented and keyed wherever practical.
9. No component may be powered outside its documented voltage range.
10. Final harnesses must minimize unnecessary adapters and unsupported connector conversions.
11. The physical and electrical interface matrix will be completed after all procurement selections are finalized.
12. Verification testing must validate voltage stability, current margin, thermal performance, and fault behavior.

---

# Electrical Power Domains

MP-1 is divided into four electrical power domains.

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
| Normal Capacity Range | 5,000–6,000 mAh |
| Reference Pack | Tattu G-Tech 4S 5200 mAh 35C |

The battery supplies both the propulsion branch and the avionics power-module branch.

## 2. Propulsion Domain

The propulsion domain contains:

- Main battery
- Electronic speed controller
- Brushless motor
- Propeller

The reference ESC is the Hobbywing Skywalker 50A V2. It accepts the 4S battery voltage and drives the T-Motor F90 brushless motor.

The ESC includes a 5 V/5 A switching BEC. That BEC is available as a possible servo-power source, but it is not yet approved as the final MP-1 servo-power architecture.

## 3. Flight Avionics Domain

The flight avionics domain is centered on the Holybro Pixhawk 6C Mini.

The Pixhawk must receive regulated primary logic power through a compatible external power module connected to its power input.

The power module must provide:

- Regulated flight-controller power
- Main-battery voltage measurement
- Main-battery current measurement
- Electrical isolation and filtering appropriate for autopilot use
- Compatibility with the Pixhawk 6C Mini analog power interface
- Adequate current-measurement range for the propulsion system

The exact power module remains to be selected.

## 4. Servo and Peripheral Domain

The servo and peripheral domain includes:

- Left aileron servo
- Right aileron servo
- Elevator servo
- Any additional control-surface servo
- RC receiver, if powered from the servo rail
- Other low-voltage peripherals where appropriate

The servo rail must be powered independently from the Pixhawk logic-power input.

Possible servo-power sources include:

1. The Hobbywing Skywalker 50A V2 integrated 5 V/5 A BEC
2. A dedicated external BEC
3. A dedicated regulated servo-power module
4. A redundant dual-source arrangement, if later justified

The final choice will be made during the power-module / external-BEC evaluation.

---

# High-Level Architecture

```text
                         MP-1 4S LiPo Battery
                          14.8 V nominal
                                 │
                                 │
                  ┌──────────────┴──────────────┐
                  │                             │
                  │                             │
         Propulsion Power Branch      Avionics Power Branch
                  │                             │
                  │                             │
      Hobbywing Skywalker 50A V2        External Power Module
                  │                             │
         ┌────────┴────────┐                    │
         │                 │                    │
         │                 │                    ├── Regulated FC power
         │                 │                    ├── Battery-voltage sense
         │                 │                    └── Battery-current sense
         │                 │                             │
 T-Motor F90 Motor    ESC Integrated BEC                 │
                           5 V / 5 A                      │
                               │                          │
                               │                          │
                     Candidate Servo-Power Source         │
                               │                          │
                               └──────────────┬───────────┘
                                              │
                                   Holybro Pixhawk 6C Mini
                                              │
             ┌────────────────────────────────┼────────────────────────────────┐
             │                                │                                │
             │                                │                                │
       PWM Signal Outputs                Avionics Interfaces              Future MAVLink
             │                                │                           Companion Link
             │                                │                                │
       Servo Power Rail                ┌───────┼────────┐                Companion Computer
             │                         │       │        │
      ┌──────┼──────┐                  │       │        │
      │      │      │                  │       │        │
 Left Ail. Right Ail. Elevator        GPS     RC Rx   Telemetry
 Servo     Servo      Servo          /Compass          Radio
                                          │
                                      Airspeed /
                                       Sensors
```

---

# Flight-Controller Power Architecture

## Primary Logic Power

The Pixhawk 6C Mini must receive regulated power through its primary analog power input using a compatible power module.

The flight-controller logic-power path must not depend on the servo rail.

This separation is required so that:

- Servo transients do not directly disturb flight-controller logic power
- Servo-rail faults do not automatically remove autopilot power
- Voltage and current measurement remain available through the power module
- The servo-power source can be changed without replacing the flight controller

## Servo Rail

The Pixhawk PWM output rail distributes servo control signals and servo-rail power, but it does not create servo power.

A separate regulated source must energize the servo rail.

The final servo-power source must support:

- All installed servos under simultaneous transient loading
- Receiver and peripheral loads connected to the rail
- Adequate voltage stability
- Acceptable thermal margin
- Protection against reverse current where required
- Compatibility with the Pixhawk PWM rail
- Defined grounding with the flight controller and ESC

## Backup-Power Consideration

The current MP-1 baseline does not yet require redundant flight-controller power.

Redundant logic power may be considered later if:

- The selected power module supports backup power
- A lightweight secondary regulated source is available
- The added wiring and mass are justified
- Fault-isolation testing demonstrates a meaningful reliability benefit

The Pixhawk 6C Mini's single primary analog power input makes power-source selection and connector reliability particularly important.

---

# Propulsion and BEC Architecture

## ESC Propulsion Path

The ESC receives raw battery voltage through the main propulsion branch.

The ESC then provides:

- Three-phase motor power
- PWM throttle control input
- Optional 5 V/5 A BEC output
- Propulsion protection and configuration functions

## ESC BEC Use

The integrated ESC BEC is a candidate for the servo rail because it is rated at 5 V/5 A.

It must not be accepted as the final servo-power source until testing confirms:

- Continuous servo-current margin
- Simultaneous servo transient performance
- Voltage stability during motor acceleration
- Acceptable electrical noise
- Acceptable temperature
- Safe behavior during ESC faults or shutdown
- No unintended power backfeed into the Pixhawk power input

If these conditions are not met, a dedicated external BEC or servo regulator will be selected.

## Throttle Signal

The Pixhawk sends the throttle-control signal to the ESC using a conventional PWM output.

The signal ground must share the required reference with the flight controller and servo-power system.

The final interface matrix must identify whether the ESC's BEC positive lead is retained, isolated, or removed, depending on the chosen servo-power architecture.

---

# Power Monitoring

The MP-1 power module must measure:

- Main battery voltage
- Main propulsion current
- Estimated consumed capacity
- Remaining battery percentage through flight-controller estimation

The current sensor must support the verified peak propulsion current with adequate margin.

The initial design target is:

| Parameter | Target |
|-----------|--------|
| Continuous Measurement Range | At least 60 A preferred |
| Peak Measurement Range | At least 80 A preferred |
| Battery Voltage Range | Must safely include 16.8 V |
| Flight-Controller Interface | Pixhawk 6C Mini analog power interface |
| Connector System | Keyed and documented |
| Calibration | Supported by ArduPlane |
| Installed Voltage Drop | Minimized |
| Thermal Margin | Verified at maximum propulsion load |

These values remain preliminary until static propulsion testing confirms actual current draw with the selected motor and propeller.

---

# Grounding and Noise Control

The final architecture must use a controlled common electrical reference while minimizing high-current noise coupling into avionics.

The harness design should:

- Keep high-current battery, ESC, and motor wiring physically separated from GPS, compass, receiver, and sensor wiring
- Keep motor phase leads as short as practical
- Avoid large ground loops
- Route analog power-sense wiring away from motor leads
- Use twisted signal-and-ground pairs where appropriate
- Use the manufacturer-supplied power-module harness where possible
- Mount the compass away from the battery, ESC, motor wiring, and current sensor
- Include adequate input filtering where recommended by component manufacturers
- Avoid unsupported parallel BEC outputs

Detailed grounding and electromagnetic-compatibility requirements will be documented during harness design.

---

# Connector Strategy

The current connector strategy is:

| Interface | Connector Strategy |
|-----------|--------------------|
| Battery to Aircraft | XT60 |
| Battery Balance | JST-XH |
| Battery to ESC | XT60 installed on ESC input |
| ESC to Motor | Matching bullet connectors or documented direct connection |
| Power Module to Flight Controller | Manufacturer-compatible keyed harness |
| Pixhawk Peripheral Ports | JST-GH manufacturer-standard harnesses |
| Servo Connections | JR/Futaba-compatible three-pin connectors |
| CAN Devices | Pixhawk-compatible CAN harnessing |
| GPS / Compass | Pixhawk-compatible keyed harness |
| Receiver | Protocol-specific keyed or documented harness |
| Telemetry | Pixhawk-compatible serial harness |

Commercially available adapters may be used during development only when:

- Pin assignments are verified
- Voltage compatibility is documented
- The adapter is mechanically secure
- The adapter does not create an ambiguous or reversible connection
- The final interface matrix records the adapter

The production MP-1 harness should minimize adapters and avoid loose conversion chains.

---

# Fault Containment Goals

The electrical architecture should reduce the likelihood that one subsystem fault disables unrelated systems.

Desired fault-containment behavior includes:

| Fault | Desired Result |
|-------|----------------|
| Servo overload | Flight controller remains powered if practical |
| Servo BEC failure | Flight controller logic remains powered |
| Power-module sensing failure | Flight controller behavior is defined and logged |
| ESC propulsion shutdown | Flight controller and telemetry remain powered |
| Motor short or stall | ESC protection operates without damaging avionics |
| Receiver loss | Flight controller executes configured failsafe |
| Telemetry loss | Autonomous and RC control remain available |
| Companion-computer fault | Flight controller retains primary control |
| Battery disconnect | Complete system shutdown; no unsafe backfeed path |

The final design may not provide full redundancy for every fault, but dependencies must be explicit and tested.

---

# Remaining Power-System Decisions

The following decisions remain open:

1. Select the external Pixhawk-compatible power module.
2. Select the servo-power source.
3. Determine whether the ESC BEC will be used.
4. Define servo-rail voltage.
5. Confirm total servo and receiver current requirements.
6. Define any backup-power architecture.
7. Confirm power-module current range.
8. Define connector types and genders.
9. Define wire gauges.
10. Define protection devices and ratings.
11. Define grounding and shielding.
12. Define physical routing and mounting.
13. Confirm cooling requirements.
14. Complete the physical and electrical interface matrix.
15. Create the detailed electrical wiring diagram.
16. Create the electrical verification plan.

---

# Verification Requirements

The completed electrical power system must be verified through inspection, measurement, demonstration, and test.

Minimum verification activities include:

1. Inspect all connector polarity and pin assignments.
2. Measure battery voltage at each power-domain input.
3. Confirm Pixhawk logic voltage.
4. Confirm servo-rail voltage unloaded and under load.
5. Confirm receiver and peripheral voltage.
6. Calibrate voltage sensing.
7. Calibrate current sensing.
8. Measure idle avionics current.
9. Measure servo transient current.
10. Measure static propulsion current.
11. Measure voltage sag during motor acceleration.
12. Measure ESC, BEC, power-module, connector, and wire temperature.
13. Confirm no Pixhawk reset during servo transients.
14. Confirm no Pixhawk reset during rapid throttle changes.
15. Confirm current and voltage logging.
16. Confirm low-voltage warnings and failsafe thresholds.
17. Confirm safe behavior during receiver loss.
18. Confirm safe behavior during propulsion shutdown.
19. Confirm the battery can be replaced without altering other hardware.
20. Archive test data, logs, calibration values, photographs, and configuration records.

---

# Related Documentation

Detailed procurement decisions are maintained in:

```text
docs/platforms/mp-1/procurement/approved-components.md
docs/platforms/mp-1/procurement/procurement-matrix.md
docs/platforms/mp-1/procurement/vendor-notes.md
```

The future physical and electrical interface matrix should reside under:

```text
docs/platforms/mp-1/interfaces/
```

Detailed verification procedures and results should reside under:

```text
docs/platforms/mp-1/verification/
```

Significant final architectural decisions should be recorded through an Engineering Decision Record under:

```text
docs/platforms/mp-1/edr/
```

---

# Revision History

## Revision 1

- Added the selected 4S LiPo battery architecture.
- Added the Tattu G-Tech 4S 5200 mAh reference battery.
- Added the Hobbywing Skywalker 50A V2 reference ESC.
- Added the T-Motor F90 2806.5 1300KV reference motor.
- Added the Holybro Pixhawk 6C Mini reference flight controller.
- Separated propulsion, flight-controller logic, servo, and peripheral power domains.
- Defined the requirement for an external Pixhawk-compatible power module.
- Defined the requirement for a separately evaluated servo-power source.
- Added preliminary power-monitoring requirements.
- Added connector, grounding, fault-containment, and verification requirements.
- Deferred the final interface matrix and detailed harness design until procurement selections are complete.

## Revision 0

- Initial high-level electrical power architecture established.
