
# MP-1 Engineering Decisions

**Status:** Active

## Purpose

This document records significant engineering decisions for Meadowlark Platform 1 (MP-1).

---

# Decision 001

## Use the Flightory LARK as the MP-1 reference airframe

**Reason**

Provides a proven, modular fixed-wing platform suitable for validating the Meadowlark engineering process.

**Consequences**

- Third-party design files are not redistributed.
- MP-1 remains transferable to future airframes.

**Revisit When**

A new reference platform is selected.

---

# Decision 002

## Establish a minimum viable flight baseline

**Reason**

Validate the core aircraft before adding advanced capabilities.

**Consequences**

- Manual takeoff
- Manual landing
- Autonomous waypoint navigation
- Return-to-launch

**Revisit When**

Baseline flight testing is complete.

---

# Decision 003

## Use ArduPlane on a Holybro Pixhawk 6C Mini

**Reason**

Mature, well-supported autopilot ecosystem.

**Consequences**

Future hardware should remain compatible where practical.

**Revisit When**

Requirements exceed platform capability.

---

# Decision 004

## Use a single 4S battery architecture

**Reason**

Reduce complexity and improve reproducibility.

**Consequences**

No separate payload power during the initial phase.

**Revisit When**

Mission equipment requires independent power.

---

# Decision 005

## Use the ESC integrated BEC for initial servo power

**Reason**

Simplest architecture for baseline verification.

**Consequences**

Must be validated during testing before becoming permanent.

**Revisit When**

Testing identifies inadequate performance.

---

# Decision 006

## Separate flight-controller logic power from the servo rail

**Reason**

Improve resilience against servo power disturbances.

**Consequences**

External power module required.

**Revisit When**

Flight-controller architecture changes.

---

# Decision 007

## Telemetry is not a mission dependency

**Reason**

Waypoint missions execute onboard the flight controller.

**Consequences**

Loss of telemetry alone should not terminate a mission.

**Revisit When**

Mission architecture changes.

---

# Decision 008

## Adopt a simplified documentation structure

**Reason**

Reduce duplication and maintain one authoritative document for each topic.

**Consequences**

- README
- design
- components
- build
- testing
- decisions

serve as the primary engineering documentation.

**Revisit When**

The project grows beyond the scope of the current structure.

---

# Decision Template

```text
Decision:
Reason:
Consequences:
Revisit When:
Date:
Reference:
```
