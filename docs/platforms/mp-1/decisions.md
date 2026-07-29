# MP-1 Decisions

**Status:** Draft  
**Last Updated:** 2026-07-29

## Purpose

This document records significant MP-1 decisions in a compact chronological format.

Each entry should answer:

- What was decided?
- Why was it decided?
- What are the consequences?
- What would justify revisiting it?

This file replaces the need for a separate Engineering Decision Record for every routine project choice.

Use a separate detailed decision document only when a decision is unusually complex, controversial, safety-critical, or likely to require extensive supporting analysis.

---

# Decision Format

Use this structure for future entries:

```markdown
## YYYY-MM-DD — Decision title

**Decision**

State the decision clearly.

**Reason**

Explain the main factors.

**Consequences**

List the important effects, limits, and follow-up work.

**Revisit when**

State the conditions that would justify reconsideration.
```

---

# 2026-07-29 — Use a Minimal Initial-Flight Architecture

## Decision

MP-1 will use the simplest architecture that safely supports:

- Manual takeoff
- Manual and stabilized flight
- Onboard waypoint navigation
- Return-to-launch
- RC pilot takeover
- Manual landing
- Telemetry
- Flight logging

The initial aircraft will not include:

- Companion computer
- Payload computer
- Payload battery
- Payload regulator
- Mission-equipment power distribution
- Redundant flight-controller power
- Redundant servo power
- Camera payload
- Experimental mission sensors

## Reason

The first aircraft needs to prove the basic airframe, propulsion, power, autopilot, control, navigation, and test workflow before additional systems are added.

Removing unnecessary systems reduces:

- Weight
- Wiring
- Power demand
- Integration time
- Software complexity
- Failure modes
- Troubleshooting difficulty

ArduPlane can store and execute the required waypoint mission onboard, so a companion computer is not required for the initial objective.

## Consequences

- Initial autonomous testing is limited to onboard ArduPlane missions.
- Manual takeoff and manual landing remain the baseline.
- Payload systems are deferred.
- Redundant power systems are deferred.
- Future payloads must not become dependencies of the flight-critical system.
- Later expansion will require a separate design update.

## Revisit When

Reconsider this decision when a defined mission requires:

- Onboard vision
- Dynamic path planning
- Payload processing
- Advanced autonomy
- Additional fault tolerance
- Redundant avionics power
- A dedicated payload-power system

---

# 2026-07-29 — Use the Flightory LARK as the MP-1 Reference Airframe

## Decision

MP-1 will use the Flightory LARK as its initial physical airframe reference.

## Reason

The LARK provides a practical and accessible starting point for:

- Fixed-wing assembly
- Propulsion integration
- Avionics installation
- Autonomous-flight testing
- Documentation development
- Reproducible engineering work

Using an existing airframe allows Meadowlark to focus first on systems integration rather than designing every physical structure from zero.

## Consequences

- Flightory reference geometry and assembly information remain important.
- Meadowlark-specific avionics, power, wiring, software, and test documentation remain original project work.
- The LARK does not define the long-term architecture of future Meadowlark platforms.
- Modifications must be documented rather than silently incorporated.

## Revisit When

Reconsider this decision when:

- The LARK cannot meet the required payload, endurance, stability, or integration needs.
- Airframe limitations prevent safe testing.
- A Meadowlark-designed airframe is ready.
- A different reference aircraft offers a clear engineering advantage.

---

# 2026-07-29 — Use the Holybro Pixhawk 6C Mini as the Reference Flight Controller

## Decision

The Holybro Pixhawk 6C Mini is the MP-1 reference flight controller.

## Reason

It provides a strong balance of:

- Full ArduPlane support
- STM32H743 processing
- Onboard mission execution
- Dual IMUs
- Temperature-controlled sensors
- Fourteen PWM outputs
- Dual CAN
- Two GPS interfaces
- Removable microSD logging
- Compact size
- Standard Pixhawk connectors
- Current-production support

It provides enough capability for the initial aircraft without the size and complexity of a larger premium autopilot.

## Consequences

- MP-1 will use ArduPlane.
- An external analog power module is required.
- Servo power must be defined separately from flight-controller logic power.
- GPS, RC receiver, telemetry, and servo interfaces should use documented Pixhawk-compatible harnesses where practical.
- A companion computer is not required for the initial mission.

## Alternatives Considered

- CubePilot Cube Orange+ with Mini Carrier
- Matek H743-WING V3
- Holybro Pixhawk 6X with Mini Baseboard
- SpeedyBee F405 Wing

The Cube Orange+ and Pixhawk 6X add cost, size, and capability beyond the initial need.

The Matek H743-WING V3 offers useful fixed-wing integration but concentrates more functions on one board and requires more soldered integration.

The SpeedyBee F405 Wing was rejected for the reference role because of processor, memory, and redundancy limitations.

## Revisit When

Reconsider this decision when:

- The Pixhawk 6C Mini becomes unavailable.
- Required interfaces exceed its capabilities.
- A future platform requires more redundancy.
- Integrated power distribution becomes a stronger priority than modularity.
- New flight-controller hardware offers a clear lifecycle or support advantage.

---

# 2026-07-29 — Use a 4S LiPo Battery Architecture

## Decision

MP-1 will use a removable 4S soft-pack LiPo battery with:

- 14.8 V nominal voltage
- 16.8 V fully charged voltage
- XT60 main connector
- JST-XH balance connector
- Approximately 5,000–6,000 mAh capacity

The Tattu G-Tech 4S 5200 mAh 35C pack is the current reference battery.

## Reason

A 4S LiPo configuration:

- Matches the selected motor and ESC
- Matches the Flightory-style propulsion baseline
- Provides adequate power and energy
- Is widely available
- Supports simple charging and replacement
- Avoids custom pack construction
- Avoids adapter-dependent operation

The Tattu pack provides the best current balance of mass, energy, dimensions, and connector compatibility.

## Consequences

- 3S and 5S operation are outside the baseline.
- Li-ion packs are outside the initial baseline.
- Hardcase packs are rejected.
- Routine batteries must use XT60 without adapters.
- Larger packs require separate center-of-gravity and flight testing.
- The battery must be replaceable without rewiring the aircraft.

## Alternatives Considered

- Admiral 4S 5000 mAh 40C
- SMC HCL-HP 4S 5200 mAh 80C
- Ovonic 4S 6000 mAh 120C

## Revisit When

Reconsider this decision when:

- Endurance requirements exceed the practical 4S LiPo range.
- A different propulsion system is selected.
- Battery availability changes.
- A future platform justifies Li-ion pack engineering.
- Flight testing supports a heavier or higher-capacity pack.

---

# 2026-07-29 — Use the T-Motor F90 2806.5 1300KV as the Reference Motor

## Decision

The T-Motor F90 2806.5 1300KV is the MP-1 reference propulsion motor.

## Reason

It is the closest match to the original Flightory configuration and has the strongest available published evidence among the evaluated candidates.

It fits the intended:

- 4S battery system
- 7-inch propeller class
- Airframe mass range
- Compact motor installation

## Consequences

- Propeller selection must remain compatible with the 4S system.
- Static current must be measured with the final propeller.
- The measured current will influence the final power-module decision.
- Motor mounting screws must be checked for winding clearance.

## Alternatives Considered

- EMAX ECO II 2807 1300KV
- FlyFishRC Flash 2806.5 1350KV

## Revisit When

Reconsider this decision when:

- The motor is unavailable.
- Static testing shows unacceptable current or heat.
- A different propeller requirement emerges.
- Flight performance is inadequate.
- Airframe mass changes materially.

---

# 2026-07-29 — Use the Hobbywing Skywalker 50A V2 as the Reference ESC

## Decision

The Hobbywing Skywalker 50A V2 is the MP-1 reference electronic speed controller.

## Reason

It provides:

- 50 A continuous current
- 70 A peak current
- 4S compatibility
- Fixed-wing-specific programming
- 5 V/5 A switching BEC
- Strong protection features
- Strong manufacturer documentation
- Useful current margin for the selected motor

## Consequences

- The integrated BEC is available for servo power.
- Telemetry is not provided by the ESC.
- Final acceptance depends on static propulsion testing.
- The exact product revision and connector configuration must be confirmed at purchase.
- The ESC must be mounted with adequate cooling.

## Alternatives Considered

- Hobbywing Skywalker 40A V2
- ZTW Beatles 40A
- T-Motor AT40A

## Revisit When

Reconsider this decision when:

- Static current exceeds the safe operating margin.
- Thermal testing fails.
- ESC availability changes.
- Future propulsion changes require telemetry or higher current.

---

# 2026-07-29 — Use the ESC BEC as the Initial Servo-Power Source

## Decision

The Skywalker 50A V2 integrated 5 V/5 A switching BEC will power the initial servo rail.

A separate external BEC will not be installed unless testing shows it is needed.

## Reason

The initial aircraft has only three primary servos and one RC receiver.

Using the integrated BEC:

- Reduces weight
- Reduces wiring
- Avoids a second regulator
- Avoids unsupported parallel power sources
- Keeps the initial build simple

## Consequences

The integrated BEC must pass load testing that demonstrates:

- Servo rail remains above 4.8 V
- All servos can move simultaneously
- No flight-controller reset occurs
- No receiver reset occurs
- No unacceptable jitter occurs
- Rapid throttle changes do not disturb the rail
- Temperature remains acceptable

The BEC remains a single point of failure for the servo rail.

## Contingency

The Hobbywing UBEC 5A may be introduced if the integrated BEC fails verification.

If used:

- Set it to 5.0 V
- Isolate the ESC BEC positive lead
- Keep ESC signal and ground connected
- Do not parallel the two positive outputs

## Revisit When

Reconsider this decision when:

- Bench testing fails.
- Additional servos are added.
- Receiver or accessory loads increase.
- Separate fault containment becomes a formal requirement.
- Servo voltage requirements change.

---

# 2026-07-29 — Use Separate Flight-Controller and Servo Power Paths

## Decision

Flight-controller logic power will be provided through a compatible external power module.

Servo power will be provided through the servo rail.

The flight controller will not depend solely on the servo rail for logic power.

## Reason

Separating the power paths reduces the chance that normal servo transients will reset the flight controller.

It also allows:

- Battery voltage and current monitoring
- Independent servo-power changes
- Better fault separation
- Easier troubleshooting

## Consequences

- A compatible power module is required.
- The flight controller and servos use different regulated paths.
- The exact grounding and backfeed behavior must be verified.
- The initial design still has single points of failure and is not redundant.

## Revisit When

Reconsider this decision when:

- A different flight controller is selected.
- An integrated wing controller is adopted.
- Redundant avionics power becomes necessary.
- Testing reveals an unexpected grounding or backfeed issue.

---

# 2026-07-29 — Keep the Power Module Unselected Until Propulsion Current Is Known

## Decision

The power module will remain under research until the propeller is selected and the installed propulsion current is measured or bounded with adequate confidence.

The Holybro PM02 V3 is the leading candidate but is not yet selected.

## Reason

The final current path must be sized using the actual propulsion load.

The decision must account for:

- Circuit-board rating
- Connector rating
- Wire rating
- Sustained current
- Burst current
- Burst duration
- Voltage drop
- Temperature
- Current-sensor range

A current sensor that can measure the expected load does not automatically mean the stock connector and wire path can safely carry it.

## Consequences

- Propeller selection must happen before final power-module selection.
- PM02 V3 remains Research.
- PM06 V2, PM07, and Mauch alternatives remain available.
- Static propulsion testing becomes a prerequisite for final power-module approval.

## Revisit When

Reconsider this decision when:

- A propeller is selected.
- Static current is measured.
- A propulsion analysis provides a conservative and credible current bound.
- A power-module candidate with clearly superior current-path documentation becomes available.

---

# 2026-07-29 — Require GPS and Compass for Initial Autonomous Flight

## Decision

GPS and compass are required for the initial autonomous waypoint and return-to-launch capability.

## Reason

They are needed for:

- Position
- Heading
- Home-position establishment
- Waypoint navigation
- Return-to-launch
- Geofence behavior

## Consequences

- Autonomous testing cannot begin without healthy navigation data.
- GPS and compass placement must avoid propulsion-current interference.
- Calibration and preflight health checks are required.
- Final hardware remains to be selected.

## Revisit When

Reconsider the exact hardware when:

- A preferred GPS or compass architecture is selected.
- CAN-based navigation hardware offers a clear advantage.
- Interference testing shows the planned location is inadequate.
- Future navigation requirements change.

---

# 2026-07-29 — Require RC Pilot Takeover

## Decision

MP-1 autonomous testing must always preserve immediate pilot takeover through the RC link.

## Reason

The initial aircraft is experimental.

The pilot needs a direct way to:

- Exit autonomous mode
- Recover from unexpected navigation behavior
- Recover from poor tuning
- Land manually
- Control the aircraft without telemetry

## Consequences

- RC receiver selection is flight-critical.
- Flight modes must include a clear takeover path.
- Pilot takeover must be tested before waypoint flight.
- Telemetry cannot be the only means of changing mode.
- RC failsafe behavior must be documented and tested.

## Revisit When

This decision should remain in place for MP-1.

Only a future platform with a substantially different safety concept should reconsider it.

---

# 2026-07-29 — Treat Telemetry as Required Test Equipment, Not a Mission Dependency

## Decision

Telemetry is required for initial engineering operations but is not required for an already loaded onboard mission to continue.

## Reason

Telemetry is useful for:

- Mission upload
- Parameter review
- Flight monitoring
- Battery monitoring
- Navigation monitoring
- Test observation

However, making mission execution depend on telemetry would create an unnecessary failure mode.

## Consequences

- Telemetry hardware remains part of the initial test configuration.
- Loss of telemetry alone must not remove RC control.
- Loss of telemetry alone must not stop the onboard mission unless a configured failsafe explicitly commands it.
- Telemetry-loss behavior must be tested.

## Revisit When

Reconsider this decision only when a future mission explicitly requires continuous external command or data exchange.

---

# 2026-07-29 — Use Manual Takeoff and Manual Landing for the Initial Baseline

## Decision

Initial MP-1 flights will use manual takeoff and manual landing.

Autonomous takeoff and autonomous landing are deferred.

## Reason

Manual takeoff and landing reduce the number of variables during early testing.

The initial technical objective is to validate:

- Airframe
- Propulsion
- Control
- Stabilization
- Onboard navigation
- Return-to-launch
- Pilot takeover
- Logging

Autonomous takeoff and landing add additional tuning and risk without being necessary for that objective.

## Consequences

- The initial waypoint mission begins after manual climb to a safe altitude.
- Autonomous mission testing ends before landing.
- RTL may return the aircraft to the home area, but the pilot retains landing responsibility.
- Takeoff and landing automation remain future work.

## Revisit When

Reconsider this decision when:

- Manual flight is repeatable.
- Stabilized flight is repeatable.
- Waypoint navigation is repeatable.
- RTL is repeatable.
- A safe and controlled test plan exists for automated takeoff or landing.

---

# 2026-07-29 — Simplify the MP-1 Documentation Structure

## Decision

MP-1 documentation will use a small set of clear authoritative files:

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

The former detailed requirements, architecture, procurement, vendor-notes, and per-decision structure will be consolidated.

## Reason

The earlier structure repeated the same information across too many files.

The simplified structure is easier to:

- Read
- Maintain
- Update
- Review
- Reproduce
- Keep internally consistent

The project does not need heavy process for its own sake.

## Consequences

- `design.md` becomes the authoritative design description.
- `components.md` becomes the authoritative component and procurement record.
- `build.md` becomes the reproducibility guide.
- `testing.md` becomes the verification and evidence guide.
- `decisions.md` becomes the chronological decision record.
- `README.md` becomes the main entry point.
- Old files may be removed or replaced with short redirect notes after consolidation is checked.
- Evidence files remain separate from the concise design documents.

## Revisit When

Reconsider the structure when:

- The project grows to multiple aircraft variants.
- Different teams need separate ownership.
- Regulatory or contractual requirements demand formal traceability.
- Document size or complexity makes consolidation harder to use.
- A subsystem becomes complex enough to justify its own document.

---

# Adding Future Decisions

Add new entries in date order.

Keep entries short enough that a future reader can understand the project history without reading every test log or discussion.

A decision entry should not duplicate entire sections from `design.md`, `components.md`, `build.md`, or `testing.md`.

Use links to those files when the implementation detail already exists elsewhere.

---

# Related Documents

```text
docs/platforms/mp-1/README.md
docs/platforms/mp-1/design.md
docs/platforms/mp-1/components.md
docs/platforms/mp-1/build.md
docs/platforms/mp-1/testing.md
```

---

# Change History

## 2026-07-29

- Created the consolidated MP-1 decision log.
- Replaced the need for routine standalone EDR files.
- Preserved the major initial-flight, component, power, autonomy, and documentation decisions.
