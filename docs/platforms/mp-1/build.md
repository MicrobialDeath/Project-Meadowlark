# MP-1 Build

**Status:** Draft

## Purpose

This document defines how Meadowlark Platform 1 (MP-1) is assembled, configured, and prepared for operation.

It answers **how the aircraft is built**.

It does **not** define:

- System architecture (see [design.md](design.md))
- Hardware selection (see [components.md](components.md))
- Test procedures (see [testing.md](testing.md))
- Engineering rationale (see [decisions.md](decisions.md))

---

## Build Philosophy

The objective is to produce a reliable, reproducible aircraft that another builder can assemble using the documented procedures.

Every completed build should be:

- Safe
- Repeatable
- Inspectable
- Maintainable

If assembly requires undocumented knowledge, the documentation is incomplete.

---

## Prerequisites

Before beginning assembly:

- Review [design.md](design.md).
- Confirm all selected hardware in [components.md](components.md).
- Inspect all components for shipping or manufacturing damage.
- Verify compatibility between all selected hardware.

Do not begin assembly with unresolved hardware selections.

---

## Airframe Preparation

Prepare the airframe according to the manufacturer's instructions.

Before installing electronics:

- Inspect structural components.
- Verify wing alignment.
- Verify control surface freedom of movement.
- Verify fasteners.
- Remove debris from the airframe.

Any structural defects should be corrected before continuing.

---

## Component Installation

Install components in the following general order:

1. Servos
2. Motor
3. ESC
4. Flight controller
5. Power module
6. GPS and compass
7. RC receiver
8. Telemetry radio
9. Battery mounting hardware

Temporary installation is acceptable until component placement has been validated.

---

## Wiring

General wiring principles:

- Keep wiring as short as practical.
- Protect wires from abrasion.
- Secure wiring against vibration.
- Avoid routing signal wires alongside high-current power wires where practical.
- Provide service loops where maintenance may be required.
- Label connectors when practical.

The completed wiring should be understandable without tracing every conductor individually.

---

## Power System

The baseline aircraft uses:

- One removable 4S LiPo battery
- ESC-integrated BEC for servo power
- Flight-controller power module for avionics

Future power-system changes should be evaluated only after the baseline aircraft has been verified.

---

## Flight Controller Installation

Install the flight controller:

- Near the aircraft center of gravity
- On vibration-isolated mounting
- With correct orientation
- With unobstructed cable routing

Record any mounting deviations from the reference configuration.

---

## GPS Installation

Install the GPS and compass:

- Away from high-current wiring
- Away from magnets
- With a clear view of the sky
- Following the orientation specified by the manufacturer

Verify orientation during flight-controller configuration.

---

## Firmware

Install the current approved release of ArduPlane.

Record:

- Firmware version
- Vehicle type
- Installation date

Firmware updates should follow normal verification procedures before flight.

---

## Flight Controller Configuration

Configure at minimum:

- Airframe type
- Servo assignments
- RC calibration
- Accelerometer calibration
- Compass calibration
- Radio failsafe
- Battery monitoring
- Flight modes
- Return-to-launch behavior

Configuration should remain as close as practical to documented defaults.

---

## Mission Configuration

Before autonomous flight:

- Verify the home position.
- Verify waypoint order.
- Confirm altitude references.
- Review return-to-launch behavior.

Mission files should be retained for future reference.

---

## Weight and Balance

Record:

- Aircraft mass
- Center of gravity
- Battery position

Verify the center of gravity before every first flight following configuration changes.

---

## Pre-Flight Inspection

Before initial power-up:

- Verify fasteners.
- Verify propeller installation.
- Verify servo operation.
- Verify control direction.
- Verify wiring security.
- Verify battery installation.
- Verify flight-controller mounting.
- Verify antenna placement.

Inspection procedures are defined in [testing.md](testing.md).

---

## Build Records

Record at minimum:

- Build date
- Aircraft configuration
- Firmware version
- Hardware revisions
- Aircraft mass
- Center of gravity
- Known deviations from the reference configuration

Build records should be stored under `docs/platforms/mp-1/evidence/` once evidence records are introduced.

---

## Configuration Management

Retain copies of:

- Flight-controller parameter files
- Mission files
- Firmware version information

Configuration files should match the aircraft that was actually flown.

---

## Revision Policy

Whenever the aircraft configuration changes:

- Update this document if the assembly procedure changes.
- Update [components.md](components.md) if hardware changes.
- Record significant engineering decisions in [decisions.md](decisions.md).
- Re-verify the aircraft using [testing.md](testing.md).

The documented build procedure should always reflect the current reference aircraft.
