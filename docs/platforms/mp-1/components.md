
# MP-1 Components

**Status:** Draft

## Purpose

This document identifies the hardware used for Meadowlark Platform 1 (MP-1), records why it was selected, identifies acceptable alternatives, and tracks outstanding procurement decisions.

Design intent is documented in `design.md`.

Assembly procedures belong in `build.md`.

Verification belongs in `testing.md`.

---

# Component Status

| Category | Status |
|-----------|--------|
| Airframe | Selected |
| Flight Controller | Selected |
| Battery | Selected |
| Motor | Selected |
| ESC | Selected |
| Servos | Selected |
| Power Module | Open |
| GPS / Compass | Open |
| RC Receiver | Open |
| Telemetry Radio | Open |
| Propeller | Open |

---

# Selected Components

## Airframe

**Selected:** Flightory LARK

Reason:
- Proven fixed-wing platform
- Modular construction
- Good fit for MP-1 objectives

---

## Flight Controller

**Selected:** Holybro Pixhawk 6C Mini

Reason:
- Mature ArduPlane support
- Reliable navigation hardware
- Well documented ecosystem

---

## Battery

**Selected:** Tattu G-Tech 4S 5200 mAh XT60

Alternatives:

- Admiral 5000 mAh
- SMC 5200 mAh
- Ovonic 6000 mAh (research)

Selection Criteria:

- 4S LiPo
- XT60 connector
- Approximately 5000–6000 mAh
- Suitable aircraft mass

---

## Motor

**Selected:** T-Motor F90 2806.5 1300KV

Alternatives:

- EMAX ECO II 2807
- FlyFishRC Flash 2806.5

Selection Criteria:

- Efficient cruise
- Reliable thermal performance
- Compatible with 4S operation

---

## ESC

**Selected:** Hobbywing Skywalker 50A V2

Alternatives:

- Hobbywing Skywalker 40A V2
- ZTW Beatles 40A
- T-Motor AT40A (research)

Selection Criteria:

- Integrated switching BEC
- Adequate current capacity
- Proven fixed-wing use

---

## Servos

**Selected:** Corona DS929MG

Alternatives:

- Hitec HS-82MG
- EMAX ES08MD II

Selection Criteria:

- Metal gears
- Suitable torque
- Good reliability

---

# Remaining Selections

The following hardware remains under evaluation:

- Flight-controller power module
- GPS / Compass
- RC receiver
- Telemetry radio
- Propeller

Selection should prioritize compatibility with the chosen flight controller and documented reliability over feature count.

---

# Compatibility Requirements

All selected hardware should support:

- One 4S battery architecture
- ArduPlane
- Pixhawk 6C Mini
- Manual flight
- Autonomous waypoint navigation
- Return-to-launch
- Manual landing

---

# Purchase Checklist

Before purchasing a component confirm:

- Correct model number
- Connector compatibility
- Voltage compatibility
- Physical fit
- Manufacturer documentation
- Availability of replacement parts

---

# Verification Required

Selection alone does not approve a component.

Each installed component should be verified through inspection and testing.

Verification includes:

- Physical inspection
- Correct installation
- Functional operation
- Integration with adjacent systems
- Flight validation where applicable

Testing procedures are defined in `testing.md`.

---

# Configuration Control

Whenever a selected component changes:

1. Update this document.
2. Record the reason in `decisions.md` if the change is significant.
3. Update build documentation if assembly changes.
4. Re-test affected systems.

---

# Relationship to Other Documents

| Document | Purpose |
|----------|---------|
| design.md | System architecture |
| components.md | Hardware selection |
| build.md | Installation |
| testing.md | Verification |
| decisions.md | Engineering rationale |

This document is the authoritative source for the MP-1 hardware baseline.
