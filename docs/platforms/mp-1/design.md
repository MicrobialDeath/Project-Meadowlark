# MP-1 Design

**Status:** Draft  
**Last Updated:** 2026-07-29

## Purpose

This document defines what Meadowlark Platform 1 (MP-1) is intended to do and how the initial aircraft is designed to accomplish it.

MP-1 uses the Flightory LARK airframe as a practical starting point for building and validating a reproducible autonomous fixed-wing aircraft.

The initial aircraft is intentionally simple. It is designed to:

- Take off under manual control
- Fly under manual or stabilized control
- Execute a pre-programmed waypoint mission onboard
- Return to launch
- Allow immediate pilot takeover
- Land under manual control
- Record useful flight data
- Operate without a companion computer or payload-power system

The initial design is not intended to include every future capability. It establishes a reliable flight baseline that later versions can extend.

---

# Initial Success Criteria

MP-1 is ready for initial autonomous waypoint testing when it can:

1. Power on without wiring or configuration changes.
2. Establish a valid home position.
3. Respond correctly to manual RC control.
4. Fly safely in manual or stabilized mode.
5. Store a waypoint mission onboard the flight controller.
6. Continue an already loaded mission without an active telemetry link.
7. Navigate through the programmed waypoints.
8. Return to launch.
9. Allow pilot takeover using the RC transmitter.
10. Maintain stable flight-controller and servo power during normal operation.
11. Record flight mode, position, attitude, power data, waypoint progress, and failsafe events.
12. Complete a manual landing.
13. Preserve all logs, parameters, mission files, and test notes needed to reproduce the flight.

Autonomous takeoff and autonomous landing are deferred.

---

# System Boundary

## Included in the Initial Aircraft

The initial flight system includes:

- Flightory LARK airframe
- 4S flight battery
- Propulsion motor
- Propeller
- Electronic speed controller
- Flight-controller power module
- Flight controller
- Control-surface servos
- RC receiver
- GPS and compass
- Telemetry radio
- Required flight sensors
- Wiring, connectors, antennas, and mounting hardware
- ArduPlane firmware
- Approved flight-controller parameters
- Approved waypoint mission

## Not Included in the Initial Aircraft

The initial aircraft does not include:

- Companion computer
- Payload computer
- Payload battery
- Payload regulator
- Mission-equipment power distribution
- Camera payload
- Experimental payload sensors
- Redundant flight-controller power
- Redundant servo-power system
- Autonomous takeoff
- Autonomous landing

Future mission equipment must not become a dependency of the basic flight system.

---

# Operating Concept

The planned initial flight sequence is:

1. Inspect the aircraft.
2. Install and secure the flight battery.
3. Power the aircraft.
4. Confirm flight-controller, receiver, GPS, compass, telemetry, and battery-monitoring health.
5. Confirm the home position.
6. Confirm the loaded waypoint mission.
7. Confirm flight modes, geofence, and failsafe settings.
8. Perform a manual takeoff.
9. Climb to a safe altitude.
10. Enter autonomous mission mode.
11. Allow the aircraft to navigate the programmed route.
12. Exercise return-to-launch or pilot takeover as required by the test plan.
13. Perform a manual landing.
14. Power down and inspect the aircraft.
15. Archive logs and test evidence.

---

# Flight-Control Design

## Flight Controller

The reference flight controller is the Holybro Pixhawk 6C Mini running ArduPlane.

The flight controller is responsible for:

- Manual and stabilized flight modes
- Onboard mission storage
- Waypoint navigation
- Return-to-launch
- RC pilot takeover
- Geofence behavior
- Failsafe behavior
- Battery monitoring
- Flight logging
- Telemetry communication

A companion computer is not required for the initial mission.

## Onboard Mission Execution

The waypoint mission is stored and executed by the flight controller.

An active ground-control-station or telemetry connection is not required once the mission is loaded.

Telemetry is used for:

- Mission upload
- Parameter review
- Ground monitoring
- Battery and navigation status
- Test observation

Loss of telemetry alone must not remove RC control or stop an already loaded mission unless the configured failsafe explicitly requires it.

## Manual Control

The RC system must provide:

- Manual or stabilized control
- Flight-mode selection
- Entry into autonomous mission mode
- Exit from autonomous mission mode
- Immediate pilot takeover
- Link-loss failsafe behavior

Pilot takeover must not depend on telemetry or a ground-control-station command.

## Navigation

The initial navigation system requires:

- GPS position
- Compass heading
- Valid home position
- Waypoint navigation
- Return-to-launch
- Configurable geofence

Autonomous mission testing must not begin until navigation health checks pass.

---

# Electrical Power Design

The initial aircraft uses one removable 4S LiPo battery.

The power system has three functional paths:

1. Main battery power
2. Propulsion and servo power
3. Flight-controller and avionics power

## High-Level Power Layout

```text
                         4S Flight Battery
                        14.8 V nominal
                               |
                 +-------------+-------------+
                 |                           |
                 |                           |
       Propulsion / Servo Path       Flight Avionics Path
                 |                           |
       Hobbywing Skywalker 50A V2    External Power Module
                 |                           |
         +-------+-------+                   +-- Regulated flight-controller power
         |               |                   +-- Battery-voltage sensing
         |               |                   +-- Battery-current sensing
         |               |                           |
     T-Motor F90      5 V / 5 A BEC                  |
        Motor             |                           |
                          |                           |
                     Servo Rail                Pixhawk 6C Mini
                          |                           |
                 +--------+--------+          +------+-------+--------+
                 |        |        |          |              |        |
              Aileron  Aileron  Elevator   RC Receiver   GPS/Compass Telemetry
```

No payload-power or companion-computer branch is installed in the initial configuration.

---

# Main Battery

The initial battery architecture is:

| Item | Baseline |
|------|----------|
| Chemistry | Conventional LiPo |
| Cell Count | 4S |
| Nominal Voltage | 14.8 V |
| Fully Charged Voltage | 16.8 V |
| Construction | Soft pack |
| Main Connector | XT60 |
| Balance Connector | JST-XH |
| Reference Capacity | Approximately 5,200 mAh |
| Evaluation Range | 5,000–6,000 mAh |
| Preferred Mass | 450 g or less |
| Experimental Mass Limit | Approximately 525 g |

The battery must be replaceable without changing the aircraft wiring or component configuration.

Adapter cables are not permitted for normal operation.

---

# Propulsion Power

The reference propulsion system is:

- T-Motor F90 2806.5 1300KV motor
- Hobbywing Skywalker 50A V2 ESC
- 4S LiPo battery
- Propeller to be selected and verified

The final propeller determines the actual static current.

Static testing must measure:

- Peak current
- Sustained current
- Battery voltage sag
- ESC temperature
- Motor temperature
- Connector temperature
- Power-module voltage drop

The power module cannot be finalized until this current is known.

---

# Servo Power

The Skywalker 50A V2 integrated 5 V/5 A switching BEC is the baseline servo-power source.

It is expected to power:

- Left aileron servo
- Right aileron servo
- Elevator servo
- RC receiver, if assigned to the servo rail

The integrated BEC remains provisional until testing confirms:

- Servo rail remains above 4.8 V
- Simultaneous servo movement does not reset the flight controller
- The receiver does not reset
- No unacceptable control-surface jitter occurs
- Rapid throttle changes do not cause unacceptable voltage sag or noise
- ESC and BEC temperatures remain acceptable

A separate external BEC is a contingency, not part of the initial design.

If an external BEC is later used:

- The ESC BEC positive lead must be isolated
- The ESC signal and ground remain connected
- Only one positive regulated source may feed the servo rail

---

# Flight-Controller Power

The Pixhawk 6C Mini requires a compatible external analog power module.

The power module must provide:

- Regulated flight-controller power
- Main-battery voltage measurement
- Main-battery current measurement
- Compatibility with the Pixhawk 6C Mini analog power input
- A documented and keyed harness
- Adequate current-sensor range
- Adequate current-path capability

The complete current path must be evaluated, including:

- Circuit board
- Connectors
- Wire gauge
- Wire length
- Sustained current
- Burst current
- Voltage drop
- Thermal performance

A current sensor that can measure the load is not automatically a safe current path for that load.

The Holybro PM02 V3 is the leading candidate, but it remains under evaluation until the measured propulsion current is reconciled with its complete stock power path.

---

# Power Independence

Flight-controller logic power must not depend solely on the servo rail.

This separation is intended to ensure that:

- Normal servo transients do not reset the flight controller
- Servo-rail faults do not automatically remove autopilot power
- Battery monitoring remains available
- The servo-power source can be changed without replacing the flight controller

The initial design does not include redundant flight-controller power.

---

# Fault Behavior

The design should produce the following results where practical:

| Fault | Intended Result |
|------|-----------------|
| Telemetry loss | RC control and onboard mission remain available |
| RC link loss | Flight controller executes the configured failsafe |
| GPS loss | Flight controller executes the configured navigation failsafe |
| Servo transient | Flight controller remains powered |
| Servo overload | Flight controller remains powered where practical |
| ESC propulsion shutdown | Flight controller and navigation avionics remain powered |
| Future payload failure | No effect on the initial flight system |
| Battery disconnect | Complete shutdown without unsafe backfeed |

The initial aircraft does not eliminate every single-point failure. Known single-point failures must be documented and tested where practical.

---

# Wiring and Connector Principles

The initial aircraft uses:

| Interface | Baseline |
|-----------|----------|
| Battery main connection | XT60 |
| Battery balance connection | JST-XH |
| Power module to Pixhawk | Manufacturer-compatible keyed harness |
| Pixhawk peripheral ports | JST-GH manufacturer-standard harnesses |
| Servo connectors | JR/Futaba-compatible three-pin connectors |
| GPS and compass | Pixhawk-compatible keyed harness |
| RC receiver | Protocol-specific documented harness |
| Telemetry radio | Pixhawk-compatible serial harness |

The final harness should:

- Minimize adapter chains
- Document connector type, gender, polarity, and pinout
- Keep high-current wiring away from GPS, compass, receiver, and telemetry wiring
- Keep motor phase leads short
- Avoid unnecessary ground loops
- Prevent backfeed through USB, telemetry, receiver, or sensor connections
- Use manufacturer-supplied harnesses where practical

A detailed interface matrix and wiring diagram will be created after all initial components are selected.

---

# Deferred Mission Equipment

Future mission systems may include:

- Companion computer
- Camera
- Payload sensors
- Additional radios
- Mission processor
- Separate payload battery
- Separate payload regulator

Any future mission-power system must:

- Be documented in a later design revision
- Not become a dependency of manual flight
- Not become a dependency of onboard waypoint navigation
- Not become a dependency of return-to-launch
- Not remove power from the flight controller, RC receiver, GPS/compass, or servos when it fails
- Include defined grounding and backfeed controls

---

# Verification Before Autonomous Flight

The initial aircraft must complete the following before waypoint flight testing:

1. Confirm connector polarity and pin assignments.
2. Confirm flight-controller model and hardware revision.
3. Confirm power-module model and harness compatibility.
4. Measure flight-controller supply voltage.
5. Measure servo-rail voltage unloaded and under load.
6. Measure receiver, GPS, and telemetry supply stability.
7. Calibrate battery voltage sensing.
8. Calibrate battery current sensing.
9. Measure idle avionics current.
10. Measure servo transient current.
11. Measure static propulsion current.
12. Measure power-path voltage drop.
13. Measure ESC, BEC, power-module, connector, and wire temperatures.
14. Confirm no flight-controller reset during servo transients.
15. Confirm no reset during rapid throttle changes.
16. Confirm RC-loss failsafe.
17. Confirm GPS-loss behavior.
18. Confirm telemetry-loss behavior.
19. Confirm mission storage and execution without an active telemetry link.
20. Confirm return-to-launch.
21. Confirm RC pilot takeover.
22. Confirm flight logging.
23. Archive firmware, parameters, mission file, measurements, and test results.

---

# Open Design Items

The following items remain unresolved:

1. Final power-module selection
2. Final propeller selection
3. GPS and compass selection
4. RC receiver selection
5. Telemetry radio selection
6. Airspeed-sensor need and selection
7. Exact connector genders and pinouts
8. Final wire gauges
9. Detailed wiring layout
10. Component placement
11. Cooling and vibration-isolation details
12. Final physical and electrical interface matrix
13. Detailed verification procedures

---

# Related Documents

```text
docs/platforms/mp-1/README.md
docs/platforms/mp-1/components.md
docs/platforms/mp-1/build.md
docs/platforms/mp-1/testing.md
docs/platforms/mp-1/decisions.md
```

---

# Change History

## 2026-07-29

- Consolidated the initial-flight requirements and electrical-power architecture.
- Defined the minimal flight-critical system.
- Required onboard ArduPlane waypoint execution.
- Kept manual takeoff and landing as the initial baseline.
- Excluded companion computers, payload power, and redundant avionics power.
- Established the ESC BEC as the provisional servo-power source.
- Retained the external power module as an unresolved selection.
