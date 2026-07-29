# Meadowlark Platform 1 (MP-1)

MP-1 is the first aircraft platform developed under Project Meadowlark.

It uses the Flightory LARK as a reference airframe to develop a reproducible autonomous fixed-wing aircraft. The emphasis is on understanding and documenting the complete engineering process rather than simply producing a working aircraft.

---

## Current Objective

The current objective is intentionally limited:

- Manual takeoff
- Manual and stabilized flight
- Onboard waypoint mission execution
- Return-to-launch
- Immediate RC pilot takeover
- Manual landing
- Reliable flight logging
- Complete build and test documentation

Companion computers, payloads, and advanced autonomy are intentionally deferred until the basic aircraft is proven.

---

## Current Project Status

**Phase:** Design and Integration

Completed:

- Initial system architecture
- Initial component selection
- Build documentation
- Test plan
- Decision log

Open work:

- Propeller selection
- Power-module selection
- GPS and compass selection
- RC receiver selection
- Telemetry radio selection
- First physical build
- Ground testing
- Flight testing

---

## Documentation Map

- [Design](design.md) — mission, system boundary, architecture, fault behavior, and deferred capabilities
- [Components](components.md) — selected hardware, alternatives, procurement guidance, and remaining selections
- [Build](build.md) — assembly, wiring, configuration, firmware, and build records
- [Testing](testing.md) — inspection, bench testing, ground testing, flight testing, acceptance criteria, and evidence requirements
- [Engineering decisions](decisions.md) — significant decisions and their rationale

Build and test evidence will be stored under `docs/platforms/mp-1/evidence/` once records exist.

---

## Engineering Workflow

The normal workflow is:

1. Define or update the design.
2. Select components.
3. Build the aircraft.
4. Verify each subsystem.
5. Fly progressively.
6. Record evidence.
7. Update documentation.

Only move to the next stage after the current stage is understood.

---

## Current Hardware Baseline

The authoritative MP-1 hardware baseline is maintained in [components.md](components.md).

---

## Reading Order

For a general review:

1. [README.md](README.md)
2. [design.md](design.md)
3. [components.md](components.md)
4. [build.md](build.md)
5. [testing.md](testing.md)
6. [decisions.md](decisions.md)

For building an aircraft:

1. [components.md](components.md)
2. [build.md](build.md)
3. [testing.md](testing.md)

For reviewing engineering history:

1. [decisions.md](decisions.md)
2. Review the applicable build and test evidence once records exist.

---

## Future Development

Future capabilities and deferred scope are maintained in [design.md](design.md).

New capabilities should be layered onto a verified flight platform rather than developed simultaneously with it.
