# Meadowlark Platform 1 (MP-1)

MP-1 is the first aircraft platform developed under Project Meadowlark.

It uses the Flightory LARK airframe as a practical starting point for building, documenting, and validating a reproducible autonomous fixed-wing aircraft.

The current goal is deliberately narrow:

> Build a simple aircraft that can take off manually, fly safely, execute a pre-programmed waypoint mission onboard, return to launch, allow immediate pilot takeover, land manually, and preserve enough evidence for another person to reproduce the result.

MP-1 is an engineering testbed, not a final production aircraft.

---

# Current Status

MP-1 is in active design and component-selection work.

The current reference configuration includes:

- Flightory LARK airframe
- Holybro Pixhawk 6C Mini
- ArduPlane
- T-Motor F90 2806.5 1300KV motor
- Hobbywing Skywalker 50A V2 ESC
- Corona DS929MG servos
- Tattu G-Tech 4S 5200 mAh battery
- ESC-integrated 5 V/5 A BEC for servo power
- External flight-controller power module, still under evaluation
- GPS and compass, still to be selected
- RC receiver, still to be selected
- Telemetry radio, still to be selected
- Propeller, still to be selected

The initial aircraft does not include a companion computer, payload battery, payload regulator, redundant avionics power, or mission payload.

---

# Initial Flight Objective

The initial MP-1 flight program is intended to demonstrate:

1. Safe manual takeoff
2. Safe manual and stabilized flight
3. Onboard waypoint mission storage
4. Autonomous waypoint navigation
5. Return-to-launch
6. Immediate RC pilot takeover
7. Manual landing
8. Reliable flight logging
9. Reproducible configuration and test records

Autonomous takeoff and autonomous landing are deferred.

Telemetry is required for setup and test monitoring, but an already loaded mission must continue without an active telemetry link.

---

# Documentation

MP-1 documentation is intentionally compact.

```text
docs/platforms/mp-1/
├── README.md
├── design.md
├── components.md
├── build.md
├── testing.md
├── decisions.md
└── evidence/
```

## `design.md`

Defines:

- What MP-1 is intended to do
- Initial system boundary
- Flight-control design
- Power architecture
- Fault behavior
- Open design items

## `components.md`

Records:

- Selected hardware
- Alternatives
- Open selections
- Purchase checks
- Verification still required

## `build.md`

Explains:

- Airframe preparation
- Mechanical assembly
- Wiring
- Flight-controller installation
- Firmware and configuration
- Build records
- Reproducibility expectations

## `testing.md`

Defines:

- Ground-test stages
- Power and load testing
- Propulsion testing
- Manual flight
- Stabilized flight
- Return-to-launch
- Autonomous waypoint testing
- Evidence and acceptance criteria

## `decisions.md`

Records significant project decisions and the reasons behind them.

## `evidence/`

Stores or indexes:

- Build records
- Inspection records
- Ground-test records
- Flight-test records
- Logs
- Photographs
- Measurements
- Configuration exports

---

# Recommended Reading Order

For a new reader:

1. `README.md`
2. `design.md`
3. `components.md`
4. `build.md`
5. `testing.md`
6. `decisions.md`

For someone reproducing the aircraft:

1. `components.md`
2. `build.md`
3. `testing.md`
4. Relevant files under `evidence/`

---

# Design Principles

MP-1 follows a few practical rules:

- Keep the first aircraft simple.
- Add capability only when a clear requirement exists.
- Prefer onboard mission execution over unnecessary extra computers.
- Keep pilot takeover available.
- Separate flight-controller power from servo power.
- Avoid adapter-dependent battery wiring.
- Record exact hardware, firmware, parameters, and mission files.
- Verify one stage before moving to the next.
- Preserve enough evidence for another person to repeat the work.
- Use process only where it improves clarity, safety, or reproducibility.

---

# Current Open Items

The main unresolved items are:

1. Propeller selection
2. Flight-controller power-module selection
3. GPS and compass selection
4. RC receiver selection
5. Telemetry radio selection
6. Airspeed-sensor decision
7. Final wiring and connector details
8. Final component placement
9. Final center-of-gravity target
10. Final test limits and procedures

The propeller should be selected before the power module is finalized because the propeller determines the actual propulsion current.

---

# Repository Locations

Project overview:

```text
README.md
```

MP-1 documentation:

```text
docs/platforms/mp-1/
```

Original Meadowlark hardware:

```text
hardware/
```

Software and configuration:

```text
software/
```

Third-party reference material:

```text
references/
```

Project utilities and templates:

```text
tools/
```

---

# Reproducibility

A future builder should be able to identify:

- Exact airframe reference
- Exact component models
- Hardware revisions
- Wiring and connector details
- Firmware version
- Parameter file
- Mission file
- Aircraft mass
- Center of gravity
- Battery identifier
- Test conditions
- Test results
- Known limitations

If any of those cannot be determined from the repository, the documentation is incomplete.

---

# Contributing

Changes should improve at least one of the following:

- Technical accuracy
- Safety
- Reproducibility
- Clarity
- Maintainability
- Test evidence

Avoid adding process or document layers unless they solve a real problem.

Significant architecture or scope changes should be recorded in:

```text
docs/platforms/mp-1/decisions.md
```

---

# Acknowledgement

MP-1 uses the Flightory LARK as its initial reference airframe.

Flightory reference material remains the property of its original creators. Project Meadowlark documents its own component selection, integration, configuration, testing, and engineering conclusions.
