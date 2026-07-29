# MP-1 Components

**Status:** Draft

## Purpose

This document defines the hardware selected for Meadowlark Platform 1 (MP-1), records alternatives that were evaluated, and identifies remaining procurement and verification work.

It answers **what hardware the aircraft uses**.

It does **not** describe:

- System architecture (see [design.md](design.md))
- Assembly and configuration (see [build.md](build.md))
- Test procedures (see [testing.md](testing.md))
- Engineering rationale (see [decisions.md](decisions.md))

---

# Component Selection Philosophy

MP-1 is intended to establish a reliable, reproducible baseline aircraft.

Components are selected according to the following priorities:

1. Compatibility with ArduPlane
2. Proven reliability
3. Ease of replacement
4. Availability
5. Cost
6. Future expandability

The baseline aircraft favors mature, well-understood hardware over maximum performance.

---

# Current Reference Configuration

| System | Selected Component | Status |
|---------|--------------------|--------|
| Airframe | Flightory LARK | Reference |
| Flight Controller | Holybro Pixhawk 6C Mini | Selected |
| Firmware | ArduPlane | Selected |
| Motor | T-Motor F90 2806.5 1300KV | Baseline |
| ESC | Hobbywing Skywalker 50A V2 | Baseline |
| Battery | Tattu G-Tech 4S 5200 mAh | Baseline |
| Servos | Corona DS929MG | Baseline |

The remaining systems are still under evaluation.

---

# Flight Controller

## Selected

- Holybro Pixhawk 6C Mini

Selection criteria:

- Full ArduPilot support
- Mature hardware
- Integrated vibration isolation
- Reliable documentation
- Sufficient I/O for future expansion

No companion computer is required for MP-1.

---

# Propulsion

## Selected Motor

- T-Motor F90 2806.5 1300KV

### Alternatives Evaluated

- EMAX ECO II 2807
- FlyFishRC Flash

Motor verification remains part of propulsion testing.

---

# Electronic Speed Controller

## Selected

- Hobbywing Skywalker 50A V2

### Alternatives Evaluated

- Hobbywing Skywalker 40A V2
- ZTW Beatles 40A
- T-Motor AT40A

Selection may be revisited if testing identifies a clear requirement.

---

# Servos

## Selected

- Corona DS929MG

### Alternatives Evaluated

- Hitec HS-82MG
- EMAX ES08MD II

Servo performance will be verified during ground and flight testing.

---

# Battery

## Selected

- Tattu G-Tech 4S 5200 mAh

### Alternatives Evaluated

- Admiral 5000
- SMC 5200

The baseline aircraft uses a single removable 4S battery.

---

# Remaining Component Selection

The following items remain open:

- Propeller
- Flight-controller power module
- GPS and compass
- RC receiver
- Telemetry radio
- Connectors
- Wiring materials

These items should be selected only after confirming compatibility with the baseline configuration.

---

## Compatibility Requirements

All selected hardware should support:

- ArduPlane
- 4S electrical system
- Pixhawk-compatible interfaces
- Standard PWM servo outputs
- Standard RC protocols
- GPS with integrated compass
- MAVLink telemetry

---

## Procurement Checklist

Before purchasing hardware, verify:

- Model number
- Current manufacturer specifications
- Electrical compatibility
- Physical fit
- Connector compatibility
- Availability of replacement parts
- Documentation availability

Avoid substituting components solely because they appear similar.

---

## Verification Required

Component selection is not considered complete until each subsystem has been verified.

Verification includes:

- Mechanical fit
- Electrical compatibility
- Configuration
- Ground operation
- Flight performance
- Reliability

Verification procedures are defined in [testing.md](testing.md).

---

## Future Hardware

Future hardware may include:

- Companion computer
- Payload systems
- Vision hardware
- Additional sensors
- Redundant power
- Alternative propulsion

These additions should not change the baseline aircraft until the initial platform has been fully validated.

---

## Revision Policy

This document records the current hardware baseline for MP-1.

When hardware changes:

- Update the selected component.
- Move replaced hardware to the alternatives list if still relevant.
- Record significant engineering decisions in [decisions.md](decisions.md).
- Verify the updated configuration using the procedures in [testing.md](testing.md).

Specific build records and test results belong in the future `docs/platforms/mp-1/evidence/` directory once evidence is produced.
