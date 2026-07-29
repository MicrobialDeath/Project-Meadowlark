# Meadowlark Platform 1 (MP-1)

MP-1 is the first aircraft platform developed under Project Meadowlark.

It uses the Flightory LARK as a reference airframe to develop a reproducible autonomous fixed-wing aircraft. The emphasis is on understanding and documenting the complete engineering process rather than simply producing a working aircraft.

---

# Current Objective

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

# Current Project Status

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
- GPS/Compass selection
- RC receiver selection
- Telemetry radio selection
- First physical build
- Ground testing
- Flight testing

---

# Documentation Map

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

## design.md

Defines:

- Mission
- System boundary
- Flight architecture
- Electrical architecture
- Fault behavior
- Deferred capabilities

## components.md

Defines:

- Selected hardware
- Alternatives
- Procurement guidance
- Remaining selections
- Component verification

## build.md

Defines:

- Assembly
- Wiring
- Configuration
- Firmware
- Build records

## testing.md

Defines:

- Inspection
- Bench testing
- Ground testing
- Flight testing
- Acceptance criteria
- Evidence requirements

## decisions.md

Records significant engineering decisions and why they were made.

## evidence/

Contains build records, measurements, logs, photographs, inspection reports, and flight-test evidence.

---

# Engineering Workflow

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

# Current Reference Configuration

Current reference hardware:

- Flightory LARK airframe
- Holybro Pixhawk 6C Mini
- ArduPlane
- T-Motor F90 2806.5 1300KV
- Hobbywing Skywalker 50A V2
- Corona DS929MG servos
- Tattu G-Tech 4S 5200 mAh battery

Additional hardware is documented in `components.md`.

---

# Evidence

Evidence should be stored under:

```text
docs/platforms/mp-1/evidence/
```

Typical evidence includes:

- Build records
- Inspection reports
- Ground-test reports
- Flight-test reports
- Flight logs
- Parameter files
- Mission files
- Measurements
- Photographs

Engineering conclusions should reference evidence whenever practical.

---

# Reading Order

If you are new to MP-1:

1. README.md
2. design.md
3. components.md
4. build.md
5. testing.md
6. decisions.md

If you are building an aircraft:

1. components.md
2. build.md
3. testing.md

If you are reviewing engineering history:

1. decisions.md
2. evidence/

---

# Future Development

After the baseline aircraft is proven, future work may include:

- Companion computing
- Vision systems
- Payload integration
- Longer endurance
- Advanced navigation
- Additional sensors
- New airframes

Those capabilities should be layered onto a verified flight platform rather than developed simultaneously with it.
