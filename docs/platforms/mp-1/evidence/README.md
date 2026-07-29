
# MP-1 Evidence

**Status:** Active

## Purpose

This directory contains objective evidence supporting the design, build, verification, and operation of Meadowlark Platform 1 (MP-1).

Engineering conclusions should reference evidence stored here whenever practical.

---

# Directory Structure

```text
evidence/
├── builds/
├── configurations/
├── flight-tests/
├── ground-tests/
├── inspections/
├── logs/
├── measurements/
└── photos/
```

---

# Directory Contents

## builds/

Build records for individual aircraft.

## configurations/

Firmware, parameter files, and mission files used during testing.

## flight-tests/

Flight test reports and associated data.

## ground-tests/

Ground test procedures and results.

## inspections/

Pre-build, pre-flight, and post-flight inspection records.

## logs/

Flight controller logs and exported telemetry.

## measurements/

Recorded electrical, mechanical, and performance measurements.

## photos/

Photographic documentation of builds, installations, inspections, and tests.

---

# Evidence Requirements

Where applicable, each record should include:

- Date
- Aircraft configuration
- Test or activity performed
- Results
- Pass/Fail status
- Notes
- Associated photographs or logs

---

# File Naming

Use descriptive, chronological names whenever practical.

Example:

```text
2026-08-15_ground-test-motor-verification.md
2026-08-22_flight-test-rtl.md
```

---

# Relationship to Documentation

Evidence supports, but does not replace, the primary engineering documentation.

- `design.md` defines the system.
- `components.md` defines the hardware.
- `build.md` defines assembly.
- `testing.md` defines verification.
- `decisions.md` records engineering decisions.

This directory contains the records demonstrating those documents in practice.
