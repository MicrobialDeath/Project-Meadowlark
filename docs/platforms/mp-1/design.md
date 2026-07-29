# MP-1 Design

**Status:** Draft

## Purpose

This document defines what Meadowlark Platform 1 (MP-1) is intended to do and how the aircraft is arranged at the system level.

It answers **what the aircraft must do and how its major systems relate**.

It does **not** define:

- Hardware selection (see [components.md](components.md))
- Assembly and configuration (see [build.md](build.md))
- Test procedures (see [testing.md](testing.md))
- Engineering rationale and history (see [decisions.md](decisions.md))

---

## Mission

MP-1 exists to demonstrate a reproducible autonomous fixed-wing aircraft capable of:

- Manual takeoff
- Manual and stabilized flight
- Onboard waypoint navigation
- Return-to-launch
- Immediate RC pilot takeover
- Manual landing
- Reliable flight logging

The baseline aircraft is an engineering testbed, not a production aircraft.

---

## System Boundary

### Included

The baseline MP-1 system includes:

- Flightory LARK reference airframe
- One removable 4S LiPo battery
- Brushless propulsion system
- Pixhawk-class flight controller
- ArduPlane firmware
- Flight-controller power module
- Three primary control servos
- RC receiver
- GPS and compass
- Telemetry radio
- Required wiring, connectors, and mounting hardware

### Excluded

The baseline system intentionally excludes:

- Companion computer
- Payload computer
- Mission payload
- Payload battery or regulator
- Redundant flight-controller power
- Redundant servo power
- Autonomous takeoff
- Autonomous landing
- Vision systems
- Advanced onboard processing

Future capabilities must not become dependencies of the baseline aircraft.

---

## Design Principles

1. Keep the aircraft as simple as practical.
2. Use one primary flight battery.
3. Execute waypoint missions onboard the flight controller.
4. Use telemetry for setup and monitoring, not mission execution.
5. Preserve immediate manual pilot control.
6. Keep flight-controller logic power independent of the servo rail.
7. Add complexity only when testing or mission requirements justify it.
8. Preserve enough configuration and test information for reproduction.

---

## Functional Architecture

```text
Pilot
   │
RC Transmitter
   │
RC Receiver
   │
Pixhawk 6C Mini
   ├── Servos
   ├── ESC
   ├── GPS and Compass
   ├── Telemetry Radio
   └── Flight Logging
```

The flight controller is responsible for:

- Stabilization
- Flight-mode management
- Waypoint execution
- Return-to-launch
- Failsafe behavior
- Battery monitoring
- Data logging

The RC system provides manual control and immediate pilot takeover.

The telemetry link supports configuration, monitoring, and data review but is not required for onboard mission execution.

---

## Electrical Architecture

The aircraft uses one removable 4S battery feeding separate functional power paths.

```text
4S Flight Battery
   ├── ESC
   │    ├── Motor
   │    └── Servo-Rail BEC
   │         └── Servos
   │
   └── Flight-Controller Power Module
        ├── Pixhawk
        ├── GPS and Compass
        ├── RC Receiver
        └── Telemetry Radio
```

The baseline design separates flight-controller logic power from servo power.

The ESC-integrated BEC supplies the servo rail unless testing demonstrates that an external regulator is required.

The flight-controller power module supplies regulated avionics power and battery-voltage and current sensing.

---

## Flight-Control Architecture

ArduPlane runs on the flight controller and provides:

- Manual flight modes
- Stabilized flight modes
- Autonomous waypoint navigation
- Return-to-launch
- RC failsafe behavior
- Battery monitoring
- Flight logging

The mission is stored and executed onboard.

Loss of telemetry must not prevent the aircraft from completing a mission, returning to launch, or responding to RC input.

---

## Operating Concept

A normal MP-1 mission follows this sequence:

1. Inspect the aircraft.
2. Install and connect the flight battery.
3. Power the aircraft.
4. Confirm sensor health and flight-controller status.
5. Acquire GPS lock and establish the home position.
6. Verify RC control and flight modes.
7. Take off manually.
8. Enter stabilized or autonomous flight as planned.
9. Execute the onboard waypoint mission.
10. Use return-to-launch or manual pilot takeover as required.
11. Land manually.
12. Preserve logs and configuration records.
13. Inspect the aircraft after flight.

Autonomous takeoff and landing are outside the baseline operating concept.

---

## Manual Control and Pilot Takeover

Manual pilot control is a core safety requirement.

The pilot must be able to:

- Select manual or stabilized control
- Interrupt autonomous flight
- Recover from unexpected mission behavior
- Command return-to-launch when appropriate
- Complete the landing manually

Pilot takeover should not depend on the telemetry link or ground-control software.

---

## Return-to-Launch

Return-to-launch provides a predictable recovery behavior when commanded or triggered by an applicable failsafe.

RTL behavior must be configured and tested for:

- Return altitude
- Navigation to the home position
- Loiter behavior
- Pilot takeover
- Mission termination

The baseline aircraft does not use autonomous landing after RTL.

---

## Fault Behavior

The design should respond predictably to foreseeable failures.

### Loss of Telemetry

The aircraft continues executing the onboard mission or follows the active flight mode.

Telemetry loss alone must not remove RC control or stop onboard navigation.

### Loss of RC Link

The aircraft follows the configured ArduPlane RC failsafe behavior.

The exact failsafe configuration must be verified before flight.

### Loss or Degradation of GPS

The aircraft follows the configured navigation and sensor-failsafe behavior.

GPS-dependent modes must not be treated as available when position data is invalid.

### Low Battery

The flight controller monitors battery condition and applies configured warnings or failsafe behavior.

Battery thresholds must be established through testing rather than assumption.

### Propulsion Failure

The aircraft becomes a glider and remains dependent on available control authority, altitude, and pilot response.

No redundant propulsion system is included.

### Flight-Controller or Power Failure

Loss of flight-controller power or complete flight-controller failure may result in loss of stabilization, navigation, and control.

These remain accepted single-point failures in the baseline aircraft.

---

## Known Single-Point Failures

The baseline design does not eliminate every single-point failure.

Known examples include:

- One flight battery
- One flight controller
- One GPS and compass unit
- One RC receiver
- One ESC
- One motor
- One servo per control function
- One primary avionics power path

These risks are accepted temporarily to keep the baseline aircraft simple and testable.

Redundancy should be added only when a documented requirement justifies the added weight and complexity.

---

## Hardware Selection

The current hardware baseline, alternatives, open selections, and compatibility checks are maintained exclusively in [components.md](components.md).

This document intentionally avoids duplicating component-selection details.

---

## Build and Configuration

Assembly, wiring, firmware installation, parameter configuration, weight, and balance procedures are maintained in [build.md](build.md).

The physical aircraft must remain consistent with the architecture described here.

---

## Verification

Inspection, ground testing, propulsion testing, manual flight testing, stabilized flight testing, RTL testing, and autonomous mission testing are defined in [testing.md](testing.md).

An architectural claim should not be treated as verified until supported by test evidence.

---

## Deferred Capabilities

The following capabilities are intentionally deferred:

- Autonomous takeoff
- Autonomous landing
- Companion computing
- Computer vision
- Mission payloads
- Additional sensors
- Redundant avionics power
- Redundant servo power
- Alternative propulsion systems
- Alternative airframes

Deferred features may be introduced only after the baseline aircraft is demonstrated to be reliable and reproducible.

---

## Open Design Questions

The following architectural questions remain open:

- Final division of avionics loads on the flight-controller power path
- Acceptable servo-rail current margin
- Required electrical noise mitigation
- Final component placement
- Final antenna placement
- Acceptable center-of-gravity range
- Environmental operating limits
- Required safety margins for battery endurance
- Whether testing justifies an external servo regulator
- Whether later mission requirements justify power or control redundancy

Hardware-specific selections remain in [components.md](components.md).

Test limits and acceptance criteria remain in [testing.md](testing.md).

---

## Revision Policy

Update this document when the system boundary, architecture, operating concept, fault behavior, or deferred scope changes.

Update [components.md](components.md) when hardware changes.

Update [build.md](build.md) when assembly or configuration changes.

Update [testing.md](testing.md) when verification methods change.

Record significant changes and their rationale in [decisions.md](decisions.md).

This document should always describe the current intended architecture of MP-1.
