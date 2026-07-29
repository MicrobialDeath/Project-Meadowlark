# MP-1 Initial Flight Requirements

**Document ID:** MP1-REQ-INITIAL-FLIGHT  
**Revision:** 0  
**Status:** Draft  
**Author:** Project Meadowlark  
**Last Updated:** 2026-07-29  
**Evidence Level:** E1 — Preliminary Requirements

## Purpose

This document defines the minimum requirements for the initial MP-1 flight configuration.

The initial MP-1 aircraft shall reproduce the essential Flightory-style fixed-wing configuration while supporting controlled autonomous waypoint navigation using onboard ArduPlane mission execution.

The initial configuration shall remain deliberately simple. It shall not depend on a companion computer, payload system, payload battery, payload regulator, or redundant avionics power system.

## Scope

These requirements apply to the first MP-1 configuration intended to support:

- Manual takeoff
- Manual flight
- Stabilized flight
- Onboard execution of a pre-programmed waypoint mission
- Return-to-launch
- Pilot takeover
- Manual landing
- Flight-data logging
- Controlled engineering verification

These requirements do not establish autonomous takeoff or autonomous landing as initial-flight capabilities.

## Initial Flight Configuration Boundary

The initial flight-critical system includes:

- Flight battery
- Propulsion motor
- Propeller
- Electronic speed controller
- Flight-controller power module
- Flight controller
- Control-surface servos
- RC receiver
- GPS and compass
- Telemetry radio
- Required wiring, connectors, mounts, and antennas
- ArduPlane firmware and approved configuration

The initial flight configuration excludes:

- Companion computer
- Payload computer
- Payload battery
- Payload regulator
- Mission-equipment power distribution
- Camera payload
- Experimental payload sensors
- Redundant flight-controller power supply
- Redundant servo-power supply
- Nonessential avionics

## Requirement Language

The word **shall** identifies a mandatory requirement.

Verification methods are:

| Method | Meaning |
|--------|---------|
| Inspection | Confirmed through physical or documentary examination |
| Analysis | Confirmed through calculation or engineering assessment |
| Demonstration | Confirmed through observed operation without formal measurement |
| Test | Confirmed through controlled measurement or flight testing |

---

# Platform-Level Requirements

| ID | Requirement | Verification |
|----|-------------|--------------|
| MP1-IFR-001 | MP-1 shall support safe manual takeoff, controlled flight, and manual landing in its initial configuration. | Demonstration and Test |
| MP1-IFR-002 | MP-1 shall use the Flightory LARK airframe as the initial reference aircraft. | Inspection |
| MP1-IFR-003 | MP-1 shall use only the hardware required for basic flight, autonomous waypoint navigation, return-to-launch, pilot takeover, telemetry, and logging. | Inspection |
| MP1-IFR-004 | MP-1 shall not require a companion computer for initial-flight operation. | Inspection and Demonstration |
| MP1-IFR-005 | MP-1 shall not require a payload battery, payload regulator, or mission-equipment power system for initial-flight operation. | Inspection |
| MP1-IFR-006 | MP-1 shall not require redundant avionics power for initial-flight operation. | Inspection |
| MP1-IFR-007 | Removal or absence of all non-flight-critical equipment shall not prevent manual flight, autonomous waypoint navigation, return-to-launch, pilot takeover, or safe landing. | Inspection and Demonstration |

---

# Autonomous Mission Requirements

| ID | Requirement | Verification |
|----|-------------|--------------|
| MP1-AUT-001 | The flight controller shall execute a pre-programmed waypoint mission onboard without assistance from a companion computer. | Demonstration and Test |
| MP1-AUT-002 | The mission shall remain stored on the flight controller after removal of ground-station and telemetry connections. | Demonstration |
| MP1-AUT-003 | The aircraft shall navigate through mission waypoints in the programmed sequence. | Flight Test |
| MP1-AUT-004 | The aircraft shall recognize waypoint completion using the configured waypoint acceptance criteria. | Flight Test and Log Review |
| MP1-AUT-005 | The aircraft shall command the configured altitude for each applicable mission segment. | Flight Test and Log Review |
| MP1-AUT-006 | The aircraft shall command the configured navigation behavior between waypoints using ArduPlane. | Flight Test and Log Review |
| MP1-AUT-007 | The aircraft shall support operator-commanded entry into autonomous mission mode. | Demonstration and Flight Test |
| MP1-AUT-008 | The aircraft shall support operator-commanded exit from autonomous mission mode. | Demonstration and Flight Test |
| MP1-AUT-009 | The aircraft shall support return-to-launch using onboard navigation without a companion computer. | Flight Test |
| MP1-AUT-010 | Loss of telemetry shall not prevent continued execution of an already loaded onboard mission. | Demonstration and Flight Test |
| MP1-AUT-011 | Autonomous mission execution shall not depend on payload power or mission-equipment power. | Inspection and Demonstration |
| MP1-AUT-012 | Autonomous takeoff shall not be required for the initial MP-1 flight configuration. | Inspection |
| MP1-AUT-013 | Autonomous landing shall not be required for the initial MP-1 flight configuration. | Inspection |

---

# Manual Control and Pilot-Takeover Requirements

| ID | Requirement | Verification |
|----|-------------|--------------|
| MP1-CTL-001 | The pilot shall be able to command manual or stabilized control through the RC link. | Demonstration and Flight Test |
| MP1-CTL-002 | The pilot shall be able to take control from autonomous mission mode using a configured RC flight-mode command. | Flight Test |
| MP1-CTL-003 | Pilot takeover shall not require a ground-control-station command. | Demonstration and Flight Test |
| MP1-CTL-004 | The flight controller shall provide configured manual, stabilized, autonomous-mission, and return-to-launch modes. | Inspection and Demonstration |
| MP1-CTL-005 | Control-surface outputs shall remain available whenever the flight-critical power system is operating. | Test |
| MP1-CTL-006 | The throttle output shall remain under flight-controller and pilot control according to the active flight mode and failsafe configuration. | Demonstration and Test |

---

# Navigation Requirements

| ID | Requirement | Verification |
|----|-------------|--------------|
| MP1-NAV-001 | MP-1 shall include a GPS receiver suitable for ArduPlane waypoint navigation. | Inspection and Test |
| MP1-NAV-002 | MP-1 shall include a compass suitable for heading estimation and ArduPlane navigation. | Inspection and Test |
| MP1-NAV-003 | The GPS and compass shall be recognized by the flight controller before autonomous mission testing. | Test |
| MP1-NAV-004 | Autonomous mission mode shall not be enabled for flight testing unless the configured navigation health checks pass. | Inspection and Demonstration |
| MP1-NAV-005 | The aircraft shall support a configurable geofence. | Demonstration |
| MP1-NAV-006 | The configured geofence response shall be verified before autonomous mission testing. | Test |
| MP1-NAV-007 | The launch location shall be recorded as the home position before autonomous mission testing. | Demonstration and Log Review |
| MP1-NAV-008 | Return-to-launch behavior shall use the recorded home position and configured return altitude. | Flight Test and Log Review |

---

# Failsafe Requirements

| ID | Requirement | Verification |
|----|-------------|--------------|
| MP1-FS-001 | The aircraft shall provide a configured RC-link-loss failsafe. | Test |
| MP1-FS-002 | The aircraft shall provide a configured GPS-loss response. | Test or Hardware-in-the-Loop Test |
| MP1-FS-003 | The aircraft shall provide a configured low-battery warning and failsafe response. | Test |
| MP1-FS-004 | The aircraft shall provide a configured geofence-breach response. | Test |
| MP1-FS-005 | Loss of telemetry alone shall not remove manual RC control. | Test |
| MP1-FS-006 | Loss of telemetry alone shall not stop an onboard waypoint mission unless specifically commanded by the configured failsafe logic. | Test |
| MP1-FS-007 | Loss or shutdown of any future non-flight-critical system shall not remove power from the flight controller, receiver, GPS/compass, or control-surface servos. | Inspection and Test |
| MP1-FS-008 | Failsafe settings shall be reviewed and recorded before each autonomous flight-test phase. | Inspection |

---

# Flight-Critical Power Requirements

| ID | Requirement | Verification |
|----|-------------|--------------|
| MP1-PWR-001 | MP-1 shall use one removable 4S flight battery for the initial configuration. | Inspection |
| MP1-PWR-002 | The flight battery shall power the propulsion system and the initial flight-critical avionics architecture. | Inspection |
| MP1-PWR-003 | The flight controller shall receive regulated power through a compatible power module. | Inspection and Test |
| MP1-PWR-004 | The power module shall provide battery-voltage and battery-current measurement to the flight controller. | Test |
| MP1-PWR-005 | The control-surface servo rail shall receive regulated power from the selected baseline servo-power source. | Inspection and Test |
| MP1-PWR-006 | The initial baseline shall use the selected ESC BEC as the servo-power source unless verification testing shows inadequate voltage stability, current margin, electrical-noise performance, or thermal performance. | Test |
| MP1-PWR-007 | Flight-controller logic power shall not depend solely on the servo rail. | Inspection and Test |
| MP1-PWR-008 | The power architecture shall support continued flight-controller operation during normal servo transients. | Test |
| MP1-PWR-009 | The power architecture shall support continued flight-controller operation during rapid throttle changes. | Test |
| MP1-PWR-010 | No payload or companion-computer power branch shall be installed in the initial-flight configuration. | Inspection |
| MP1-PWR-011 | The flight battery shall remain replaceable without changing the motor, ESC, flight controller, servos, receiver, GPS/compass, telemetry radio, or aircraft wiring configuration. | Demonstration |
| MP1-PWR-012 | All flight-critical power-path current limits shall exceed the verified operating current for their respective loads with documented engineering margin. | Analysis and Test |

---

# Flight-Control Requirements

| ID | Requirement | Verification |
|----|-------------|--------------|
| MP1-FC-001 | MP-1 shall use a flight controller supported by current ArduPlane firmware. | Inspection |
| MP1-FC-002 | The flight controller shall store and execute onboard waypoint missions. | Demonstration and Test |
| MP1-FC-003 | The flight controller shall support GPS, compass, receiver, telemetry, power monitoring, and PWM servo outputs concurrently. | Inspection and Test |
| MP1-FC-004 | The flight controller shall record flight logs to removable or onboard nonvolatile storage. | Test |
| MP1-FC-005 | The flight controller shall record navigation state, flight mode, attitude, position, power-system measurements, and failsafe events. | Log Review |
| MP1-FC-006 | The flight controller shall support return-to-launch without a companion computer. | Flight Test |
| MP1-FC-007 | The flight controller shall support pilot takeover without a companion computer or telemetry link. | Flight Test |
| MP1-FC-008 | The flight controller configuration and firmware version shall be archived before each flight-test phase. | Inspection |

---

# Telemetry Requirements

| ID | Requirement | Verification |
|----|-------------|--------------|
| MP1-TEL-001 | MP-1 shall provide a telemetry link for ground monitoring during engineering flight tests. | Demonstration |
| MP1-TEL-002 | The telemetry link shall report flight mode, position, altitude, battery voltage, battery current, and navigation status when the link is available. | Test |
| MP1-TEL-003 | The telemetry link shall permit mission upload and parameter review before flight. | Demonstration |
| MP1-TEL-004 | The aircraft shall not require an active telemetry link to continue an already loaded onboard waypoint mission. | Test |
| MP1-TEL-005 | Telemetry failure shall not disable RC pilot takeover. | Test |

---

# Logging and Traceability Requirements

| ID | Requirement | Verification |
|----|-------------|--------------|
| MP1-LOG-001 | Every autonomous flight test shall produce a flight-controller log. | Inspection |
| MP1-LOG-002 | Each flight log shall be associated with the aircraft configuration, firmware version, parameter set, mission file, battery identification, and test record. | Inspection |
| MP1-LOG-003 | Mission completion, waypoint transitions, mode changes, failsafe events, and pilot takeover shall be identifiable in the recorded data. | Log Review |
| MP1-LOG-004 | Verification evidence shall be retained in the MP-1 verification documentation. | Inspection |

---

# Initial Operational Sequence

The initial autonomous-flight sequence shall be:

1. Inspect the aircraft and verify configuration.
2. Install and secure the flight battery.
3. Power the aircraft.
4. Confirm flight-controller, receiver, GPS, compass, telemetry, and power-monitoring health.
5. Confirm the home position.
6. Confirm the loaded waypoint mission.
7. Confirm failsafe and geofence configuration.
8. Perform manual takeoff.
9. Establish safe altitude and stable flight.
10. Command autonomous mission mode.
11. Allow the flight controller to execute the programmed waypoint route.
12. Exercise return-to-launch or pilot takeover as required by the test plan.
13. Perform manual landing.
14. Power down and inspect the aircraft.
15. Archive logs and test evidence.

---

# Deferred Capabilities

| Capability | Initial Status |
|------------|----------------|
| Autonomous takeoff | Future Evaluation |
| Autonomous landing | Future Evaluation |
| Companion-computer navigation | Future Evaluation |
| Payload-computer integration | Future Evaluation |
| Separate payload battery | Future Evaluation |
| Separate payload regulator | Future Evaluation |
| Mission-equipment power distribution | Future Evaluation |
| Redundant flight-controller power | Future Evaluation |
| Redundant servo power | Future Evaluation |
| Camera payload | Future Evaluation |
| Experimental mission sensors | Future Evaluation |

Deferred systems shall not become dependencies of the initial flight-critical system.

---

# Verification Exit Criteria

The initial-flight configuration may proceed to autonomous waypoint testing only after:

1. Manual control has been verified.
2. Stabilized flight has been verified.
3. Flight-controller power stability has been verified.
4. Servo-rail power stability has been verified.
5. Static propulsion current has been measured.
6. Battery voltage and current sensing have been calibrated.
7. GPS and compass operation have been verified.
8. RC-loss failsafe has been verified.
9. Telemetry-loss behavior has been verified.
10. Return-to-launch has been verified or approved for controlled initial testing.
11. Pilot takeover has been verified.
12. The mission and geofence have been reviewed.
13. Logging has been verified.
14. The approved configuration has been archived.

---

# Related Documentation

```text
docs/platforms/mp-1/architecture/electrical-power-architecture.md
docs/platforms/mp-1/edr/edr-0001-initial-flight-baseline.md
docs/platforms/mp-1/procurement/approved-components.md
docs/platforms/mp-1/procurement/procurement-matrix.md
docs/platforms/mp-1/procurement/vendor-notes.md
docs/platforms/mp-1/verification/
```

---

# Revision History

## Revision 0

- Established the MP-1 minimal initial-flight configuration.
- Required onboard execution of pre-programmed waypoint missions.
- Required GPS-guided navigation, return-to-launch, pilot takeover, telemetry, and logging.
- Defined manual takeoff and manual landing as the initial baseline.
- Excluded companion computers, payload systems, payload power, and redundant avionics power from the initial configuration.
- Established the principle that non-flight-critical systems shall not become dependencies of safe flight or landing.
