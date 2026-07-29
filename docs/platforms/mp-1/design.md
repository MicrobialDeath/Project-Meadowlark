# MP-1 Design

**Status:** Draft

## Purpose

This document defines what Meadowlark Platform 1 (MP-1) is intended to do and the engineering decisions that shape the aircraft.

It describes the system, not how to build or test it.

Implementation belongs in:

- [components.md](components.md) — hardware selection
- [build.md](build.md) — assembly and configuration
- [testing.md](testing.md) — verification

---

## Mission

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

## System Boundary

### Included

- Flightory LARK reference airframe
- One 4S LiPo battery
- Brushless propulsion system
- Pixhawk-class flight controller
- ArduPlane firmware
- Flight-controller power module
- Three primary control servos
- RC receiver
- GPS and compass
- Telemetry radio
- Required wiring and connectors

### Excluded

- Companion computer
- Payload systems
- Payload power
- Redundant avionics power
- Autonomous takeoff
- Autonomous landing

Future capabilities must not become dependencies of the baseline aircraft.

---

## Design Principles

1. Keep the aircraft as simple as practical.
2. One battery powers the aircraft.
3. Waypoint missions execute onboard the flight controller.
4. Telemetry is for setup and monitoring, not mission execution.
5. Manual flight must always remain possible.
6. Flight-controller logic power should remain independent of the servo rail.
7. Every design decision should improve reproducibility.

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
   ├── GPS / Compass
   ├── Telemetry
   └── Flight Logging
   