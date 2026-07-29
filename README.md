# Project Meadowlark

Project Meadowlark is an open engineering project focused on building, testing, and documenting autonomous fixed-wing aircraft.

The project emphasizes practical engineering:

- Build a working aircraft
- Keep the design understandable
- Record important decisions
- Verify capability through testing
- Preserve enough information for another person to reproduce the work
- Add complexity only when a clear requirement justifies it

The current development platform is Meadowlark Platform 1 (MP-1).

---

# Meadowlark Platform 1

MP-1 uses the Flightory LARK as its initial reference airframe.

The current goal is to build a simple aircraft that can:

- Take off manually
- Fly under manual or stabilized control
- Execute a pre-programmed waypoint mission onboard
- Return to launch
- Allow immediate RC pilot takeover
- Land manually
- Record useful flight data
- Preserve the configuration and evidence needed for reproduction

MP-1 is an engineering testbed, not a final production aircraft.

Detailed MP-1 documentation is located at:

```text
docs/platforms/mp-1/
```

Start here:

```text
docs/platforms/mp-1/README.md
```

---

# Current Status

MP-1 is in active design, component-selection, integration-planning, and documentation work.

The current reference configuration includes:

- Flightory LARK reference airframe
- Holybro Pixhawk 6C Mini
- ArduPlane
- T-Motor F90 2806.5 1300KV motor
- Hobbywing Skywalker 50A V2 ESC
- Corona DS929MG servos
- Tattu G-Tech 4S 5200 mAh battery
- ESC-integrated 5 V/5 A BEC for servo power

The following items remain open:

- Propeller
- Flight-controller power module
- GPS and compass
- RC receiver
- Telemetry radio
- Final wiring and connector details
- Final component placement
- Final test limits

The initial aircraft does not include:

- Companion computer
- Payload computer
- Payload battery
- Payload regulator
- Mission payload
- Redundant flight-controller power
- Redundant servo power
- Autonomous takeoff
- Autonomous landing

---

# Repository Structure

```text
Project-Meadowlark/
├── README.md
├── CONTRIBUTING.md
├── CHANGELOG.md
├── LICENSE
├── assets/
├── docs/
│   └── platforms/
│       └── mp-1/
│           ├── README.md
│           ├── design.md
│           ├── components.md
│           ├── build.md
│           ├── testing.md
│           ├── decisions.md
│           └── evidence/
├── hardware/
├── references/
├── software/
└── tools/
```

## `assets/`

Project images, logos, and media used by repository documentation.

## `docs/`

Project and platform documentation.

The current platform documentation is under:

```text
docs/platforms/mp-1/
```

## `hardware/`

Original Meadowlark hardware designs and manufacturing files.

Examples may include:

- Avionics trays
- Sensor mounts
- Camera mounts
- Wiring drawings
- Original CAD
- Manufacturing files

Third-party airframe files must not be redistributed here unless their license explicitly permits it.

## `references/`

Third-party reference information, source notes, and licensing guidance.

Flightory LARK reference information is located at:

```text
references/flightory-lark/
```

## `software/`

Source code and aircraft configuration files.

Examples may include:

- ArduPlane parameter files
- Mission files
- Supporting software
- Ground tools
- Data-processing scripts

## `tools/`

Project utilities, templates, and repeatable engineering helpers.

---

# MP-1 Documentation

The MP-1 documentation set is intentionally compact.

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

## `README.md`

Provides the MP-1 overview, current status, open work, and document map.

## `design.md`

Defines what MP-1 must do and how the system is arranged.

It covers:

- Initial objective
- System boundary
- Operating concept
- Flight-control design
- Electrical architecture
- Fault behavior
- Deferred capabilities
- Open design questions

## `components.md`

Records:

- Selected hardware
- Alternatives
- Open selections
- Purchase checks
- Compatibility concerns
- Verification still required

## `build.md`

Explains how to:

- Prepare the airframe
- Install components
- Wire the aircraft
- Configure the flight controller
- Record the build
- Preserve firmware, parameters, and mission files

## `testing.md`

Defines:

- Inspection
- Ground testing
- Electrical testing
- Propulsion testing
- Manual flight testing
- Stabilized flight testing
- Return-to-launch testing
- Autonomous waypoint testing
- Pass/fail criteria
- Evidence requirements

## `decisions.md`

Records the important decisions that shaped MP-1 and the reasons behind them.

## `evidence/`

Stores or indexes:

- Build records
- Inspection records
- Ground-test records
- Flight-test records
- Logs
- Configuration exports
- Photographs
- Measurements

---

# Documentation Principles

Project Meadowlark follows these documentation principles:

1. Keep one authoritative location for each topic.
2. Avoid copying the same information into multiple files.
3. Keep design intent separate from component selection.
4. Keep component selection separate from build instructions.
5. Keep build instructions separate from test procedures.
6. Record major decisions without repeating entire technical documents.
7. Preserve evidence for claims that have been tested.
8. Clearly identify open questions and unverified assumptions.
9. Prefer clear language over formal process for its own sake.
10. Add new documents only when the existing structure is no longer adequate.

---

# Reproducing MP-1

A future builder should be able to determine:

- The reference airframe
- Exact component models
- Hardware revisions
- Wiring and connector details
- Firmware version
- Flight-controller parameters
- Mission file
- Aircraft mass
- Center of gravity
- Battery identification
- Test conditions
- Test results
- Known limitations

The recommended reading order is:

```text
docs/platforms/mp-1/README.md
docs/platforms/mp-1/design.md
docs/platforms/mp-1/components.md
docs/platforms/mp-1/build.md
docs/platforms/mp-1/testing.md
docs/platforms/mp-1/decisions.md
```

Evidence supporting a specific aircraft or test should be stored or indexed under:

```text
docs/platforms/mp-1/evidence/
```

---

# Third-Party Material

Project Meadowlark uses third-party products, software, and reference designs.

Unless explicitly permitted by the applicable license, this repository does not redistribute:

- Proprietary aircraft design files
- Proprietary CAD
- Proprietary printable files
- Copyrighted manuals
- Vendor documentation
- Restricted technical drawings

Third-party rights remain with their respective owners.

The Flightory LARK design must be obtained directly from Flightory and used according to its current licensing terms.

See:

```text
references/flightory-lark/README.md
```

---

# Contributing

Contributions should improve at least one of the following:

- Technical accuracy
- Safety
- Reproducibility
- Clarity
- Maintainability
- Test evidence

Before contributing, review:

```text
CONTRIBUTING.md
```

Avoid creating new folders or documents unless they solve a clear organizational or technical problem.

---

# License

Original Project Meadowlark material is provided under the repository license unless otherwise noted.

See:

```text
LICENSE
```

Third-party material remains subject to its original license and ownership.

---

# Acknowledgements

Project Meadowlark builds on the work of open-source software communities, aircraft designers, manufacturers, researchers, and individual builders.

Their work makes practical experimental engineering possible.
