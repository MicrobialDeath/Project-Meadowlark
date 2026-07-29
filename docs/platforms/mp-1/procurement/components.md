# MP-1 Approved Components

**Document ID:** MP1-PROC-APPROVED-COMPONENTS  
**Revision:** 3  
**Status:** Draft  
**Author:** Project Meadowlark  
**Last Updated:** 2026-07-29  

## Purpose

This document identifies the current procurement candidates for the MP-1 platform.

Components are ranked using available engineering evidence collected before procurement. Rankings guide purchasing decisions and remain provisional until the selected hardware is integrated and verified on MP-1.

This document is aligned with the minimal initial-flight baseline defined in:

```text
docs/platforms/mp-1/requirements/initial-flight-requirements.md
docs/platforms/mp-1/edr/edr-0001-initial-flight-baseline.md
```

The initial MP-1 configuration shall support manual takeoff, onboard autonomous waypoint navigation, return-to-launch, pilot takeover, manual landing, telemetry, and flight logging without requiring a companion computer or payload-power system.

## Procurement Classification

### Rank

| Rank | Meaning |
|------|---------|
| Best | Current reference recommendation for MP-1. |
| Better | Strong alternative with minor trade-offs. |
| Okay | Acceptable alternative with reduced capability, weaker evidence, or lower engineering confidence. |

### Status

| Status | Meaning |
|--------|---------|
| Research | Important technical, dimensional, sourcing, or compatibility evidence remains incomplete. |
| Future Evaluation | Candidate is outside the current procurement baseline but may be reconsidered later. |
| Provisional | Research is complete enough to support procurement, but the component has not yet been validated in MP-1. |
| Approved | Component has passed procurement, integration, and verification testing. |
| Rejected | Candidate does not meet the current MP-1 requirements. |

### Design Role

| Design Role | Meaning |
|-------------|---------|
| Reference | Preferred baseline component for the current MP-1 configuration. |
| Alternative | Substitute candidate if the reference component is unavailable or unsuitable. |
| Extended-Capacity Alternative | Optional higher-capacity candidate requiring additional weight, center-of-gravity, and flight validation. |
| Premium Alternative | Higher-cost candidate offering additional redundancy, power-input resilience, or expansion capability. |
| Integrated Alternative | Fixed-wing-oriented candidate that consolidates power distribution and servo power at the cost of reduced modularity. |
| Contingency Alternative | Candidate retained only if the baseline architecture fails verification or later requirements justify the added complexity. |

---

# Initial Flight-Critical Baseline

The initial MP-1 configuration shall include only:

- Main flight battery
- Propulsion motor
- Propeller
- Electronic speed controller
- Flight-controller power module
- Flight controller
- Control-surface servos
- RC receiver
- GPS and compass
- Telemetry radio
- Required flight sensors
- Required wiring, connectors, and mounts

The initial configuration shall not include:

- Companion computer
- Payload computer
- Payload battery
- Payload regulator
- Mission-equipment power distribution
- Redundant flight-controller power
- Redundant servo-power system
- Cameras or mission payloads
- Nonessential experimental sensors

The flight controller shall execute pre-programmed waypoint missions onboard without dependence on a companion computer or active telemetry link.

---

# Flight Control Servos

## Primary Flight Servos

| Rank | Component | Status | Design Role | Notes |
|------|-----------|--------|-------------|-------|
| Best | Corona DS929MG | Provisional | Reference | Closest documented match to the Flightory LARK reference design and appropriate for the minimal three-servo baseline. |
| Better | Hitec HS-82MG | Provisional | Alternative | Strong documentation, established aviation use, and long-term support, but heavier than preferred. |
| Okay | EMAX ES08MD II | Provisional | Alternative | Mechanically suitable digital servo with incomplete published electrical characterization. |

### Engineering Requirements

| Requirement | Target |
|-------------|--------|
| Operating Voltage | 4.8–6.0 V |
| Gear Material | Metal |
| Weight | ≤15 g preferred |
| Torque | ≥2.0 kg·cm at 6 V |
| Stall Current | ≤1.5 A preferred; verify if undocumented |
| Connector | JR/Futaba-compatible |
| Initial Quantity | Three primary flight servos |
| Servo-Power Source | ESC BEC baseline, subject to verification |

---

# Brushless Propulsion Motors

## Propulsion Motor

| Rank | Component | Status | Design Role | Notes |
|------|-----------|--------|-------------|-------|
| Best | T-Motor F90 2806.5 1300KV | Provisional | Reference | Direct Flightory reference motor with the strongest available manufacturer documentation and published performance data. |
| Better | EMAX ECO II 2807 1300KV | Provisional | Alternative | Strong value, suitable geometry, and useful independent test evidence. |
| Okay | FlyFishRC Flash 2806.5 1350KV | Provisional | Alternative | Mechanically suitable, but supported by less fixed-wing-specific evidence. |

### Engineering Requirements

| Requirement | Target |
|-------------|--------|
| Motor Class | 2806.5–2807 |
| KV | 1300–1350KV |
| Battery | 4S required |
| Propeller | 7×4 to 7×6 |
| Weight | 45–55 g preferred |
| ESC Compatibility | 50 A continuous preferred |
| Documentation | Manufacturer specifications required |
| Independent Testing | Strongly preferred |
| Current Verification | Static current shall be measured with the selected propeller |

---

# Electronic Speed Controllers

## Propulsion ESC

| Rank | Component | Status | Design Role | Notes |
|------|-----------|--------|-------------|-------|
| Best | Hobbywing Skywalker 50A V2 | Provisional | Reference | 50 A continuous, 70 A peak, 5 V/5 A switching BEC, fixed-wing programming, and comprehensive protection features. |
| Better | Hobbywing Skywalker 40A V2 | Provisional | Alternative | Same published size and weight as the 50 A model, with reduced current margin. |
| Okay | ZTW Beatles 40A | Provisional | Alternative | Credible fixed-wing ESC with a smaller BEC and lower burst-current capability. |
| Okay | T-Motor AT40A | Research | Alternative | Potentially suitable, but complete manufacturer documentation has not yet been collected. |

### Engineering Requirements

| Requirement | Target |
|-------------|--------|
| Continuous Current | 50 A preferred |
| Peak Current | ≥70 A preferred |
| Battery Compatibility | 4S required |
| BEC | 5 V/5 A switching preferred |
| Aircraft Type | Fixed-wing-specific preferred |
| Control Signal | Standard PWM |
| Programming | Brake, timing, startup, and cutoff configuration |
| Protection | Thermal, overload, low-voltage, and signal-loss protection |
| Telemetry | Desirable but not required |

## Servo-Power Decision

The Hobbywing Skywalker 50A V2 integrated 5 V/5 A switching BEC is the provisional reference servo-power source for the initial MP-1 build.

It shall remain the reference only if bench verification confirms:

- Adequate servo-rail voltage
- Adequate continuous and transient current margin
- No flight-controller reset
- No receiver reset
- No unacceptable control-surface jitter
- No unacceptable noise during throttle transients
- Acceptable ESC and BEC temperature

A dedicated external BEC is not part of the initial baseline.

## Servo-Power Contingency

| Rank | Component | Status | Design Role | Notes |
|------|-----------|--------|-------------|-------|
| Better | Hobbywing UBEC 5A set to 5.0 V | Future Evaluation | Contingency Alternative | Retained only if the ESC BEC fails verification or later flight-critical loads exceed the baseline margin. |

When an external BEC is used, the ESC BEC positive lead shall be isolated so that only one regulated positive source feeds the servo rail.

---

# Main Flight Batteries

## Battery Architecture Decision

MP-1 shall use a removable **4S soft-pack LiPo battery**.

Li-ion endurance packs, 3S packs, 5S packs, hardcase packs, and adapter-dependent battery configurations are outside the current MP-1 baseline.

The battery shall be exchangeable without changing the motor, ESC, propeller, wiring, avionics, or aircraft configuration hardware.

## Flight Battery Candidates

| Rank | Component | Status | Design Role | Notes |
|------|-----------|--------|-------------|-------|
| Best | Tattu G-Tech 4S 5200 mAh 35C LiPo with XT60 | Provisional | Reference | Best current balance of energy, mass, dimensions, documentation, connector compatibility, and discharge capability. |
| Better | Admiral 4S 5000 mAh 40C LiPo with XT60 | Provisional | Alternative | Credible aircraft pack with good retailer support and documentation, but heavier and longer while storing slightly less energy. |
| Okay | SMC HCL-HP 4S 5200 mAh 80C Flight Pack with factory XT60 | Provisional | Alternative | Strong documentation and configurable factory connector, but materially heavier than the reference pack for the same nominal energy. |
| Okay | Ovonic 4S 6000 mAh 120C LiPo with XT60 | Research | Extended-Capacity Alternative | Additional nominal energy, but requires center-of-gravity, launch, landing, and cruise-power validation. |

## Engineering Requirements

| Requirement | Target |
|-------------|--------|
| Chemistry | Conventional LiPo |
| Cell Count | 4S only |
| Nominal Voltage | 14.8 V |
| Fully Charged Voltage | 16.8 V |
| Construction | Soft pack |
| Reference Capacity | Approximately 5,200 mAh |
| Supported Evaluation Range | 5,000–6,000 mAh |
| Preferred Pack Weight | ≤450 g |
| Experimental Pack Weight Ceiling | Approximately 525 g, subject to flight validation |
| Main Connector | XT60 |
| Balance Connector | JST-XH |
| Continuous Current Capability | Must exceed verified propulsion current with engineering margin |
| Mechanical Installation | Common battery tray, straps, and connector location |
| Hardware Changes During Swap | None permitted |
| Adapter Cables | Not permitted for normal operation |
| Charging | Balance charging with a LiPo-specific profile |

## Procurement Recommendation

Purchase the following as the MP-1 reference flight battery:

> **Tattu G-Tech 4S 5200 mAh 35C soft-pack LiPo with XT60**

---

# Flight Controllers

## Flight Controller Architecture Decision

MP-1 requires a current-production H7-class flight controller with full ArduPlane support.

The initial reference controller shall support:

- Onboard execution of pre-programmed waypoint missions
- GPS-guided navigation
- Return-to-launch
- RC pilot takeover
- Manual and stabilized flight
- Battery voltage and current monitoring
- Flight logging
- Telemetry monitoring
- GPS and compass integration
- PWM servo and throttle outputs
- Operation without a companion computer

Companion-computer connectivity is not an initial-flight procurement requirement.

## Flight Controller Candidates

| Rank | Component | Status | Design Role | Notes |
|------|-----------|--------|-------------|-------|
| Best | Holybro Pixhawk 6C Mini | Provisional | Reference | Best balance of H7 processing, redundant and temperature-controlled IMUs, 14 PWM outputs, dual CAN, dual GPS interfaces, compact packaging, and standardized Pixhawk connectors. |
| Better | CubePilot Cube Orange+ with Mini Carrier Board | Provisional | Premium Alternative | Triple IMUs, dual barometers, mature ArduPilot ecosystem, modular carrier architecture, and strong redundancy, but higher cost and integration complexity. |
| Better | Matek H743-WING V3 | Provisional | Integrated Alternative | Fixed-wing-specific H7 board with integrated voltage/current sensing, servo BEC, peripheral BEC, seven UARTs, thirteen PWM outputs, and CAN, but with less sensor redundancy and more solder-dependent integration. |
| Okay | Holybro Pixhawk 6X with Mini Baseboard | Provisional | Premium Alternative | Excellent processing, triple sensor redundancy, Ethernet, dual CAN, dual GPS, and dual power inputs, but larger, heavier, and more capable than MP-1 requires. |
| Okay | SpeedyBee F405 Wing | Rejected | Alternative | Attractive integration and cost, but the F405 processor and firmware-feature limitations do not meet the MP-1 reference-platform objective. |

### Engineering Requirements

| Requirement | Target |
|-------------|--------|
| Firmware | Full ArduPlane support |
| Processor | STM32H7 class |
| Mission Execution | Onboard waypoint mission storage and execution |
| Takeoff / Landing Baseline | Manual |
| Return-to-Launch | Required |
| Pilot Takeover | Required through RC |
| PWM Outputs | ≥8 required; ≥12 preferred |
| IMU Redundancy | At least two IMUs preferred |
| Barometer | At least one |
| Serial Connectivity | GPS, receiver, telemetry, and required sensors |
| CAN | At least one; two preferred |
| GPS / Compass | Dedicated or clearly documented integration path |
| Receiver Support | S.Bus and UART-based receiver support |
| Power Monitoring | Voltage and current sensing required |
| Servo Power | Defined independently from flight-controller logic power |
| Logging | Removable microSD preferred |
| Companion Computer | Not required for initial flight |
| Connector System | Keyed, documented, replaceable harnesses preferred |
| Mechanical Installation | Must fit the LARK avionics area with vibration isolation and service access |
| Lifecycle | Current production hardware |
| Documentation | Manufacturer and ArduPilot documentation required |

## Procurement Recommendation

Purchase the following as the MP-1 reference flight controller:

> **Holybro Pixhawk 6C Mini**

The Pixhawk 6C Mini shall execute the initial pre-programmed waypoint mission onboard.

No companion computer shall be procured for the initial MP-1 flight configuration.

---

# Flight-Controller Power Module

## Architecture Requirement

The Pixhawk 6C Mini requires a compatible external analog power module for:

- Regulated flight-controller logic power
- Main-battery voltage sensing
- Main-battery current sensing
- Battery-consumption estimation
- Flight logging of voltage and current

The power module may be installed in series with the propulsion current path. Its complete current path, including board, connectors, and wire, shall support the verified sustained and burst propulsion current.

## Current Evaluation Status

| Rank | Component | Status | Design Role | Notes |
|------|-----------|--------|-------------|-------|
| Best | Holybro PM02 V3 | Research | Reference | Strong Pixhawk 6C Mini compatibility, compact size, XT60 path, and published analog calibration; final acceptance depends on verified sustained propulsion current and stock harness limits. |
| Better | Holybro PM06 V2 | Research | Alternative | Higher board-level current rating and integrated distribution, but more hardware than the single-motor initial configuration requires. |
| Okay | Holybro PM07 | Research | Alternative | Capable but oversized and unnecessarily distribution-oriented for MP-1. |
| Okay | Mauch 100 A Hall-Effect System | Future Evaluation | Premium Alternative | Strong current-path capability and measurement quality, but requires more integration, connector work, and regulator selection. |
| Okay | Holybro PM02D / PM06D | Rejected | Alternative | Digital power modules are not the correct interface for the Pixhawk 6C Mini analog power input. |

No power module is yet approved for procurement.

The power-module evaluation shall continue against the minimal initial-flight baseline.

---

# GPS / Compass

## Architecture Requirement

GPS and compass are flight-critical for onboard waypoint navigation and return-to-launch.

The selected system shall:

- Support ArduPlane
- Interface directly with the Pixhawk 6C Mini
- Provide reliable position and heading data
- Support home-position establishment
- Support waypoint navigation
- Support return-to-launch
- Use a documented keyed harness where practical
- Fit the LARK airframe with adequate separation from propulsion-current wiring

## Status

GPS and compass evaluation is pending.

---

# RC Receiver

## Architecture Requirement

The RC receiver is flight-critical.

The selected receiver shall support:

- Manual flight
- Stabilized flight
- Flight-mode selection
- Pilot takeover from autonomous mission mode
- Configured link-loss failsafe
- Direct Pixhawk 6C Mini compatibility
- Documented power and signal requirements

## Status

RC receiver evaluation is pending.

---

# Telemetry Radio

## Architecture Requirement

Telemetry is required for engineering test monitoring, mission upload, and parameter review.

Telemetry shall not be required for continued execution of an already loaded onboard mission.

Loss of telemetry shall not remove:

- RC control
- Pilot takeover
- Flight-controller power
- GPS and compass operation
- Servo power
- Onboard mission execution, except where specifically commanded by configured failsafe logic

## Status

Telemetry-radio evaluation is pending.

---

# Deferred Equipment

The following items are outside the initial procurement baseline:

| Item | Status | Reason |
|------|--------|--------|
| Companion Computer | Future Evaluation | Not required for onboard waypoint mission execution |
| Payload Battery | Future Evaluation | No payload system is installed |
| Payload Regulator | Future Evaluation | No payload system is installed |
| Mission-Equipment Power Distribution | Future Evaluation | Deferred until a defined mission requirement exists |
| Redundant Flight-Controller Power | Future Evaluation | Adds complexity without an initial requirement |
| Redundant Servo Power | Future Evaluation | Adds complexity without an initial requirement |
| Camera Payload | Future Evaluation | Not required for initial flight |
| Experimental Mission Sensors | Future Evaluation | Not required for initial flight |
| Autonomous Takeoff Hardware or Logic | Future Evaluation | Manual takeoff is the initial baseline |
| Autonomous Landing Hardware or Logic | Future Evaluation | Manual landing is the initial baseline |

Deferred equipment shall not become a dependency of the flight-critical system.

---

# Initial Procurement Sequence

The remaining MP-1 initial-flight procurement evaluations shall proceed in this order:

1. Flight-controller power module
2. GPS / compass
3. RC receiver
4. Telemetry radio
5. Propeller
6. Airspeed sensor, if required by the initial flight-test plan

Companion-computer and payload-system procurement are not part of the initial sequence.

---

# Revision History

## Revision 3

- Aligned procurement with EDR-0001 and the initial-flight requirements.
- Defined the minimal flight-critical procurement boundary.
- Required onboard waypoint mission execution without a companion computer.
- Removed the companion computer from the initial procurement baseline.
- Removed payload power and redundant avionics power from the initial baseline.
- Established the Skywalker 50A V2 integrated BEC as the provisional baseline servo-power source.
- Retained the Hobbywing UBEC 5A only as a contingency alternative.
- Added the flight-controller power-module evaluation as an unresolved procurement category.
- Defined GPS/compass, RC receiver, and telemetry roles for autonomous waypoint testing.
- Updated the remaining procurement sequence.

## Revision 2

- Added the flight-controller evaluation.
- Selected the Holybro Pixhawk 6C Mini as the provisional reference flight controller.
- Retained Cube Orange+, Matek H743-WING V3, and Pixhawk 6X as alternatives.
- Rejected the SpeedyBee F405 Wing for the MP-1 reference role.

## Revision 1

- Added the 4S LiPo battery architecture.
- Selected the Tattu G-Tech 4S 5200 mAh battery as the provisional reference.
- Retained Admiral, SMC, and Ovonic battery alternatives.

## Revision 0

- Initial servo, motor, and ESC procurement candidates established.
