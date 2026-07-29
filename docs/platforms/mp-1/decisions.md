# MP-1 Engineering Decisions

**Status:** Active

## Purpose

This document records the significant engineering decisions made during the development of Meadowlark Platform 1 (MP-1).

It answers **why the aircraft is built the way it is**.

It does **not** duplicate:

- System architecture (see [design.md](design.md))
- Hardware selection (see [components.md](components.md))
- Assembly procedures (see [build.md](build.md))
- Test procedures (see [testing.md](testing.md))

Each entry captures the reasoning behind a decision so future contributors understand the trade-offs without having to reconstruct the project's history.

---

## Decision Format

Each decision should include:

- Decision
- Status
- Date (when known)
- Rationale
- Consequences
- Reconsider When

Not every field needs to be lengthy, but every decision should explain *why* it exists.

---

# D-001 — Establish a Minimal Baseline Aircraft

**Status:** Accepted

### Decision

Develop MP-1 as a simple, reproducible baseline aircraft before introducing advanced capabilities.

### Rationale

A smaller project scope reduces integration risk, shortens development time, and produces a platform that can be tested and understood before adding complexity.

### Consequences

The initial aircraft intentionally excludes advanced features such as payloads, companion computing, and autonomous takeoff or landing.

### Reconsider When

The baseline aircraft has demonstrated reliable and repeatable autonomous flight.

---

# D-002 — Use the Flightory LARK as the Reference Airframe

**Status:** Accepted

### Decision

Use the Flightory LARK as the reference airframe for MP-1.

### Rationale

The airframe is well documented, widely available, and appropriate for developing an autonomous fixed-wing test platform.

### Consequences

Project documentation references the LARK as the baseline airframe but does not redistribute proprietary design files.

### Reconsider When

A different airframe provides a clear engineering advantage or future project requirements change.

---

# D-003 — Use ArduPlane as the Flight Stack

**Status:** Accepted

### Decision

Adopt ArduPlane as the flight-control firmware.

### Rationale

ArduPlane provides mature autonomous flight capabilities, extensive documentation, active community support, and compatibility with Pixhawk-class hardware.

### Consequences

Configuration, testing, and documentation follow ArduPlane terminology and workflows.

### Reconsider When

A future flight stack offers measurable advantages that justify migration.

---

# D-004 — Single-Battery Electrical Architecture

**Status:** Accepted

### Decision

Power the baseline aircraft from a single removable 4S LiPo battery.

### Rationale

A single-battery architecture simplifies assembly, maintenance, troubleshooting, and field operations while reducing weight and component count.

### Consequences

Future redundant or payload power systems remain outside the baseline aircraft.

### Reconsider When

Testing demonstrates that a second power source is necessary for safety or mission requirements.

---

# D-005 — Manual Takeoff and Landing

**Status:** Accepted

### Decision

The pilot performs takeoff and landing manually.

### Rationale

Manual launch and recovery reduce early project complexity while allowing autonomous navigation to be developed independently.

### Consequences

Autonomous flight begins only after a safe manual launch and ends before landing.

### Reconsider When

The baseline aircraft has accumulated sufficient flight experience to justify automated launch or recovery.

---

# D-006 — No Companion Computer

**Status:** Accepted

### Decision

Do not include a companion computer in the baseline aircraft.

### Rationale

Mission execution can be accomplished entirely by the flight controller. Eliminating a companion computer reduces software complexity, wiring, power consumption, and maintenance.

### Consequences

Advanced perception, computer vision, and onboard mission processing are deferred.

### Reconsider When

A future mission requires onboard processing beyond the capabilities of the flight controller.

---

# D-007 — Documentation Owns One Topic

**Status:** Accepted

### Decision

Maintain one authoritative source for each engineering topic.

### Rationale

Duplicated documentation inevitably diverges over time and creates uncertainty regarding which document is correct.

### Consequences

- Architecture belongs in [design.md](design.md).
- Hardware selection belongs in [components.md](components.md).
- Assembly belongs in [build.md](build.md).
- Verification belongs in [testing.md](testing.md).
- Engineering rationale belongs in this document.

### Reconsider When

The documentation structure no longer supports the project effectively.

---

# D-008 — Verify Before Expanding Scope

**Status:** Accepted

### Decision

Validate the baseline aircraft before introducing new hardware or capabilities.

### Rationale

Engineering confidence comes from verified performance rather than planned features.

### Consequences

Major additions such as payloads, companion computing, redundant systems, and alternative airframes are postponed until the baseline platform has been demonstrated.

### Reconsider When

The current platform consistently satisfies its design objectives.

---

# Open Decisions

The following engineering questions remain unresolved:

- Final propulsion configuration
- Flight-controller power module
- GPS and compass selection
- RC receiver selection
- Telemetry radio selection
- Final connector standard
- Final wiring practices

Open hardware selections should be tracked in [components.md](components.md) until a decision has been made.

---

# Superseded Decisions

When a decision changes:

1. Do not delete the original entry.
2. Mark it as **Superseded**.
3. Reference the replacing decision.
4. Record why the change occurred.

Maintaining historical context is more valuable than rewriting project history.

---

# Revision Policy

Create a new decision only when the change affects:

- System architecture
- Hardware philosophy
- Safety
- Documentation structure
- Development strategy
- Long-term maintainability

Routine implementation updates belong in the relevant technical document rather than the engineering decision log.

The decision log should explain **why** the aircraft evolved, not simply **what** changed.
