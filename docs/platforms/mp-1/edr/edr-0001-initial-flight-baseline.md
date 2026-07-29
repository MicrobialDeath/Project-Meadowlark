# EDR-0001: MP-1 Initial Flight Baseline

**Document ID:** EDR-0001  
**Revision:** 0  
**Status:** Draft  
**Author:** Project Meadowlark  
**Last Updated:** 2026-07-29  

## Decision

MP-1 shall use the simplest flight-critical architecture that safely reproduces the Flightory LARK-style aircraft and supports controlled autonomous waypoint testing.

The initial MP-1 configuration shall:

- Support manual takeoff
- Support manual and stabilized flight
- Execute a pre-programmed waypoint mission onboard the flight controller
- Support return-to-launch
- Support RC pilot takeover
- Support manual landing
- Record flight logs
- Use one main 4S flight battery
- Use the selected ESC BEC as the baseline servo-power source, subject to verification
- Use an external flight-controller power module for regulated autopilot power and battery monitoring
- Include only the avionics required for flight, navigation, telemetry, logging, and failsafe operation

The initial configuration shall not include:

- A companion computer
- A payload computer
- A payload battery
- A payload regulator
- Mission-equipment power distribution
- Redundant flight-controller power
- Redundant servo-power architecture
- Nonessential payload sensors
- Cameras or mission payloads

Future mission equipment shall be treated as a separate subsystem and shall not become a dependency of the flight-critical system.

## Context

MP-1 is the first engineering platform under Project Meadowlark. Its purpose is to establish the project’s engineering, integration, verification, and autonomous-flight workflow using the Flightory LARK airframe as the initial reference aircraft.

Earlier architecture work considered broader future capabilities, including:

- Companion-computer integration
- Separate payload power
- Redundant avionics power
- Additional mission sensors
- Expanded power distribution

Those capabilities remain relevant to future Meadowlark development, but they add weight, wiring, integration complexity, and additional failure modes to the first aircraft.

The initial aircraft must first prove that the platform can:

1. Take off under pilot control.
2. Maintain controlled flight.
3. Navigate a pre-programmed waypoint mission using onboard ArduPlane.
4. Return to launch.
5. Permit immediate pilot takeover.
6. Land safely.
7. Produce useful engineering logs and verification evidence.

A companion computer is not required for these functions. ArduPlane can store and execute the waypoint mission directly on the flight controller.

## Decision Drivers

The decision is driven by the following priorities:

1. Flight safety
2. Simplicity
3. Low integration risk
4. Low installed mass
5. Clear fault boundaries
6. Reproducible testing
7. Onboard autonomous navigation
8. Manual pilot takeover
9. Complete logging and traceability
10. Future expansion without redesigning the initial flight-critical system

## Flight-Critical System Boundary

The initial flight-critical system includes:

- 4S flight battery
- Propulsion motor
- Propeller
- Electronic speed controller
- Flight-controller power module
- Flight controller
- Control-surface servos
- RC receiver
- GPS and compass
- Telemetry radio
- Required antennas
- Required wiring and connectors
- Required mounting hardware
- ArduPlane firmware
- Approved parameter configuration
- Approved waypoint mission
- Battery voltage and current monitoring

The following are outside the initial flight-critical boundary:

- Companion computer
- Payload processor
- Camera payload
- Experimental payload sensors
- Payload battery
- Payload regulator
- Mission-equipment power distribution
- Redundant power systems
- Nonessential radios
- Nonessential environmental sensors

## Autonomous Flight Boundary

For the initial MP-1 configuration:

- Autonomous waypoint navigation is required.
- Return-to-launch is required.
- Manual RC takeover is required.
- Mission execution shall occur onboard the flight controller.
- Telemetry shall support monitoring and configuration but shall not be required for continued execution of an already loaded mission.
- Autonomous takeoff is deferred.
- Autonomous landing is deferred.
- Manual takeoff and manual landing remain the baseline operational method.

## Power Architecture Decision

The initial power architecture shall use:

- One removable 4S LiPo flight battery
- One propulsion branch
- One regulated flight-controller logic-power branch
- One servo-power branch
- No separate payload-power branch
- No redundant avionics-power branch

The flight controller shall receive regulated power and battery-monitoring signals through a compatible external power module.

The servo rail shall use the selected ESC’s integrated BEC as the baseline source, provided verification testing confirms:

- Adequate voltage stability
- Adequate continuous current margin
- Adequate transient current margin
- Acceptable electrical noise
- Acceptable thermal performance
- No flight-controller reset during servo movement
- No flight-controller reset during throttle transients

A dedicated external BEC may be introduced later only if the integrated ESC BEC fails verification or if later hardware increases the servo-rail load.

## Alternatives Considered

### Alternative 1: Companion Computer in Initial Configuration

A companion computer could provide higher-level autonomy, onboard vision, payload processing, and advanced mission logic.

Rejected for the initial configuration because:

- It is not required for waypoint navigation.
- It adds power demand.
- It adds mass.
- It adds wiring.
- It adds software-integration complexity.
- It adds additional failure modes.
- It obscures whether the basic aircraft and autopilot architecture are working correctly.

Status: **Future Evaluation**

### Alternative 2: Separate Payload Battery and Regulator

A separate payload battery would provide strong power-domain separation.

Rejected for the initial configuration because:

- No payload system is required.
- It adds mass and maintenance burden.
- It complicates center-of-gravity management.
- It introduces additional charging and state-of-charge tracking.
- It provides no immediate benefit to the initial flight objective.

Status: **Future Evaluation**

### Alternative 3: Redundant Flight-Controller Power

A secondary flight-controller supply could improve resilience against a single regulator or connector failure.

Rejected for the initial configuration because:

- It adds wiring and mass.
- The Pixhawk 6C Mini baseline does not require it.
- It complicates backfeed and power-priority analysis.
- It is not necessary to demonstrate the initial autonomous-flight objective.

Status: **Future Evaluation**

### Alternative 4: Dedicated External Servo BEC in Initial Configuration

A separate BEC could improve fault separation and transient-current capability.

Not selected as the baseline because:

- The selected ESC already includes a 5 V/5 A switching BEC.
- The initial servo load is limited.
- A second regulator adds weight and wiring.
- The integrated BEC can be evaluated directly through bench testing.

Retained as a contingency alternative if the integrated BEC fails verification.

Status: **Alternative**

### Alternative 5: Fully Integrated Wing Flight Controller

An integrated fixed-wing flight controller could combine autopilot, current sensing, servo regulation, and power distribution.

Not selected because:

- The Pixhawk 6C Mini provides stronger modularity and sensor redundancy.
- Integrated boards concentrate more failure modes.
- Replacement may require rewiring or soldering.
- The current architecture prioritizes a replaceable, standardized autopilot ecosystem.

Status: **Alternative**

## Consequences

### Positive Consequences

- Lower installed mass
- Lower wiring complexity
- Lower procurement cost
- Fewer failure modes
- Clearer troubleshooting
- Easier verification
- Faster path to first flight
- Onboard waypoint navigation without additional compute hardware
- Cleaner separation between current flight requirements and future mission systems
- Easier preservation of the flight-critical baseline during later upgrades

### Negative Consequences

- No companion-computer capability in the initial build
- No payload-power system in the initial build
- No redundant flight-controller power
- No redundant servo-power source
- Future payload integration will require a separate design phase
- The ESC BEC becomes a single point of failure for the servo rail
- The external power module remains a single primary source for flight-controller logic power
- Some future expansion may require additional connectors, mounting provisions, and power-distribution hardware

## Safety and Fault-Containment Intent

The initial design shall preserve the following behavior:

- Loss of telemetry shall not prevent manual control.
- Loss of telemetry shall not stop an already loaded onboard mission unless required by configured failsafe logic.
- Loss of any future non-flight-critical subsystem shall not remove power from the flight controller, RC receiver, GPS/compass, or control-surface servos.
- Servo transients shall not reset the flight controller.
- Rapid throttle changes shall not reset the flight controller.
- Pilot takeover shall remain available without a companion computer or ground-control-station command.
- The aircraft shall remain capable of controlled flight and safe landing with all non-flight-critical equipment absent.

## Verification Implications

Before autonomous waypoint testing, MP-1 shall verify:

1. Manual control
2. Stabilized flight
3. Flight-controller power stability
4. Servo-rail power stability
5. Battery voltage and current sensing
6. Static propulsion current
7. GPS and compass health
8. RC-link-loss failsafe
9. Telemetry-loss behavior
10. Return-to-launch
11. Pilot takeover
12. Mission storage and onboard execution
13. Logging
14. Configuration traceability

## Documentation Implications

This decision requires updates to:

```text
docs/platforms/mp-1/requirements/initial-flight-requirements.md
docs/platforms/mp-1/architecture/electrical-power-architecture.md
docs/platforms/mp-1/procurement/approved-components.md
docs/platforms/mp-1/procurement/procurement-matrix.md
docs/platforms/mp-1/procurement/vendor-notes.md
```

The physical and electrical interface matrix shall be created after the complete initial procurement set is selected.

The interface matrix should reside under:

```text
docs/platforms/mp-1/interfaces/
```

Verification procedures and results should reside under:

```text
docs/platforms/mp-1/verification/
```

## Future Reconsideration Triggers

This decision should be reconsidered when one or more of the following occurs:

- A companion computer becomes necessary for a defined mission requirement.
- A payload requires independent power.
- The integrated ESC BEC fails verification.
- Added servos or avionics exceed the baseline power margin.
- Redundant power becomes a stated safety requirement.
- Autonomous takeoff or landing becomes a formal requirement.
- A future Meadowlark platform has materially different reliability or payload requirements.

A future change shall be recorded in a new EDR rather than rewriting this decision.

## Related Documentation

```text
docs/platforms/mp-1/requirements/initial-flight-requirements.md
docs/platforms/mp-1/architecture/electrical-power-architecture.md
docs/platforms/mp-1/procurement/approved-components.md
docs/platforms/mp-1/procurement/procurement-matrix.md
docs/platforms/mp-1/procurement/vendor-notes.md
docs/program/project-standards.md
```

## Revision History

### Revision 0

- Established the minimal MP-1 initial-flight baseline.
- Required onboard execution of pre-programmed waypoint missions.
- Required return-to-launch and manual pilot takeover.
- Defined manual takeoff and manual landing as the initial operating method.
- Excluded companion computers, payload systems, payload power, and redundant avionics power from the initial configuration.
- Selected the ESC BEC as the baseline servo-power approach subject to verification.
- Established future mission equipment as a separate subsystem that shall not become a dependency of the flight-critical system.
