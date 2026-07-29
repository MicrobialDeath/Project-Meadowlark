
# MP-1 Design

**Status:** Draft

## Purpose

This document defines what Meadowlark Platform 1 (MP-1) is intended to do and the engineering decisions that shape the aircraft. It describes the system, not how to build or test it.

Implementation details belong in `build.md`, component selection in `components.md`, and verification in `testing.md`.

---

# Mission

MP-1 exists to demonstrate a reproducible autonomous fixed-wing aircraft capable of:

- Manual takeoff
- Manual and stabilized flight
- Onboard waypoint navigation
- Return-to-launch
- Immediate RC pilot takeover
- Manual landing
- Flight logging

Autonomous takeoff, autonomous landing, payloads, and companion computers are outside the initial scope.

---

# System Boundary

## Included

- Flightory LARK reference airframe
- One 4S LiPo battery
- Brushless propulsion system
- Pixhawk-class flight controller
- ArduPlane firmware
- Flight-controller power module
- Three primary control servos
- RC receiver
- GPS/Compass
- Telemetry radio
- Required wiring and connectors

## Excluded

- Companion computer
- Payload systems
- Payload power
- Redundant avionics power
- Autonomous takeoff
- Autonomous landing

Future capabilities must not become dependencies of the baseline aircraft.

---

# Design Principles

1. Keep the aircraft as simple as practical.
2. One battery powers the aircraft.
3. Waypoint missions execute onboard the flight controller.
4. Telemetry is for setup and monitoring, not mission execution.
5. Manual flight must always remain possible.
6. Flight-controller logic power should remain independent of the servo rail.
7. Every design decision should improve reproducibility.

---

# Functional Architecture

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
   ├── GPS / Compass
   ├── Telemetry
   └── Flight Logging
```

The flight controller is responsible for stabilization, waypoint execution, return-to-launch, failsafes, battery monitoring, and logging.

---

# Electrical Architecture

The aircraft uses three logical power paths:

1. Main battery
2. Propulsion and servo power
3. Flight-controller and avionics power

A single removable 4S battery supplies both propulsion and avionics through separate paths.

The baseline design uses the ESC's integrated BEC for servo power. An external UBEC will only be introduced if testing demonstrates a requirement.

---

# Flight Operations

Normal mission sequence:

1. Aircraft inspection
2. Battery installation
3. System health checks
4. GPS lock and home position
5. Manual takeoff
6. Autonomous waypoint mission
7. Return-to-launch or pilot takeover
8. Manual landing
9. Log preservation

---

# Fault Philosophy

The design should tolerate the loss of telemetry without ending a mission.

Loss of RC link, GPS, or propulsion should be handled by configured ArduPlane failsafes.

Known single-point failures will be documented and evaluated during testing rather than eliminated prematurely.

---

# Current Reference Configuration

The current baseline hardware is maintained in `components.md`.

Only high-level architectural assumptions belong here.

---

# Deferred Capabilities

Future revisions may introduce:

- Companion computing
- Vision systems
- Payloads
- Additional sensors
- Redundant power
- Alternative airframes

Each addition should preserve compatibility with the proven baseline wherever practical.

---

# Open Design Questions

Current unresolved items include:

- Final propeller
- Flight-controller power module
- GPS/Compass
- RC receiver
- Telemetry radio
- Final wiring layout
- Component placement

These items are tracked in `components.md` until selected.

---

# Relationship to Other Documents

| Document | Purpose |
|----------|---------|
| README.md | Navigation and project status |
| design.md | System definition |
| components.md | Hardware selection |
| build.md | Assembly and configuration |
| testing.md | Verification |
| decisions.md | Engineering history |

This document should change only when the intended design changes, not when a build or test is performed.
