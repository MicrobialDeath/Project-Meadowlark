
# MP-1 Testing

**Status:** Draft

## Purpose

This document defines the verification process for Meadowlark Platform 1 (MP-1).

---

# Test Progression

1. Documentation Review
2. Component Inspection
3. Build Inspection
4. Electrical Verification
5. Flight Controller Configuration
6. Bench Testing
7. Propulsion Testing
8. Ground Testing
9. Manual Flight Testing
10. Stabilized Flight Testing
11. Return-to-Launch Testing
12. Autonomous Waypoint Testing

---

# Component Inspection

Verify:

- Correct part numbers
- Physical condition
- Connector compatibility
- Installation hardware

Record results in:

```text
docs/platforms/mp-1/evidence/inspections/
```

---

# Build Verification

Confirm:

- Wiring
- Connector polarity
- Fastener security
- Control surface direction
- Center of gravity
- Firmware version
- Parameters loaded

---

# Electrical Testing

Verify:

- Battery voltage
- Flight controller power
- Servo rail voltage
- Receiver operation
- GPS operation
- Telemetry operation

---

# Bench Testing

Verify:

- Sensor calibration
- RC control
- Flight modes
- Logging
- Failsafes
- Mission upload

---

# Propulsion Testing

Measure:

- Static current
- Voltage sag
- ESC temperature
- Motor temperature
- Throttle response

---

# Ground Testing

Verify:

- GPS lock
- Home position
- Mode changes
- RTL logic
- Mission loading

---

# Flight Testing

Progress through:

1. Manual flight
2. Stabilized flight
3. RTL
4. Autonomous waypoint mission

Advance only after successful completion of the previous stage.

---

# Acceptance Criteria

The aircraft shall:

- Remain controllable
- Complete the planned mission
- Return telemetry when available
- Preserve flight logs
- Allow immediate pilot takeover

---

# Evidence

Store evidence under:

```text
docs/platforms/mp-1/evidence/
├── inspections/
├── ground-tests/
├── flight-tests/
├── logs/
├── measurements/
├── configurations/
└── photos/
```

Each test should include:

- Date
- Aircraft configuration
- Battery used
- Weather (flight tests)
- Results
- Pass/Fail
- Notes

---

# Relationship to Other Documents

| Document | Purpose |
|----------|---------|
| design.md | System definition |
| components.md | Hardware baseline |
| build.md | Assembly |
| testing.md | Verification |
| decisions.md | Engineering history |

This document is the authoritative source for MP-1 verification procedures.
