# MP-1 Procurement Evaluation Matrix

**Document ID:** MP1-PROC-EVALUATION-MATRIX  
**Revision:** 3  
**Status:** Draft  
**Author:** Project Meadowlark  
**Last Updated:** 2026-07-29  

## Purpose

This document records the engineering comparison of candidate hardware for the MP-1 platform.

Rankings are based on:

1. Engineering requirements
2. Manufacturer documentation
3. Original Flightory references
4. Independent testing
5. Community operational experience
6. Engineering evaluation
7. Procurement suitability
8. Verification planning

All rankings remain provisional until the selected component is procured, integrated, and verified on MP-1.

This matrix is aligned with:

```text
docs/platforms/mp-1/requirements/initial-flight-requirements.md
docs/platforms/mp-1/edr/edr-0001-initial-flight-baseline.md
docs/platforms/mp-1/architecture/electrical-power-architecture.md
```

The initial MP-1 configuration shall support manual takeoff, onboard waypoint navigation, return-to-launch, RC pilot takeover, manual landing, telemetry, and flight logging without requiring a companion computer or payload-power system.

---

# Procurement Classification

## Rank

| Rank | Meaning |
|------|---------|
| Best | Current reference recommendation for MP-1. |
| Better | Strong alternative with minor trade-offs. |
| Okay | Acceptable alternative with reduced capability, weaker evidence, or lower engineering confidence. |

## Status

| Status | Meaning |
|--------|---------|
| Research | Important technical, dimensional, sourcing, or compatibility evidence remains incomplete. |
| Future Evaluation | Candidate is outside the current procurement baseline but may be reconsidered later. |
| Provisional | Research is complete enough to support procurement, but MP-1 validation is pending. |
| Approved | Component has passed procurement, integration, and verification testing. |
| Rejected | Candidate does not meet the current MP-1 requirements. |

## Design Role

| Design Role | Meaning |
|-------------|---------|
| Reference | Preferred baseline component for the current MP-1 configuration. |
| Alternative | Substitute candidate if the reference component is unavailable or unsuitable. |
| Extended-Capacity Alternative | Optional higher-capacity candidate requiring additional mass, center-of-gravity, and flight validation. |
| Premium Alternative | Higher-cost candidate offering additional redundancy, power-input resilience, or expansion capability. |
| Integrated Alternative | Fixed-wing-oriented candidate that consolidates power distribution and servo power at the cost of reduced modularity. |
| Contingency Alternative | Candidate retained only if the baseline architecture fails verification or later requirements justify the added complexity. |

---

# Initial Flight-Critical Evaluation Boundary

The initial procurement baseline includes only:

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

The following are outside the initial procurement baseline:

- Companion computer
- Payload computer
- Payload battery
- Payload regulator
- Mission-equipment power distribution
- Redundant flight-controller power
- Redundant servo-power system
- Camera payload
- Experimental mission sensors
- Autonomous takeoff hardware or logic
- Autonomous landing hardware or logic

---

# Flight Control Servo Evaluation

| Attribute | Corona DS929MG | Hitec HS-82MG | EMAX ES08MD II |
|----------|----------------|---------------|----------------|
| Rank | Best | Better | Okay |
| Status | Provisional | Provisional | Provisional |
| Design Role | Reference | Alternative | Alternative |
| Voltage | 4.8–6.0 V | 4.8–6.0 V | 4.8–6.0 V |
| Weight | 12.5 g | 19 g | Approximately 12 g |
| Gear Material | Metal | Metal | Metal |
| Torque | 2.2–2.5 kg·cm | 3.4 kg·cm | Approximately 2.4 kg·cm |
| Documentation | Good | Excellent | Fair |
| Electrical Characterization | Normal current published; stall current not confirmed | Better documented | Incomplete |
| Baseline Quantity | Three | Three | Three |
| Engineering Confidence | High | High | Medium |
| Primary Trade-off | Stall current not published | Higher mass and cost | Incomplete electrical characterization |

## Recommendation

The Corona DS929MG remains the reference servo because it most closely matches the Flightory LARK baseline while meeting the preferred mass and torque envelope.

The servo selection remains provisional until simultaneous loaded-servo testing confirms stable operation from the selected servo-power source.

---

# Brushless Motor Evaluation

| Attribute | T-Motor F90 2806.5 1300KV | EMAX ECO II 2807 1300KV | FlyFishRC Flash 2806.5 1350KV |
|----------|-----------------------------|--------------------------|--------------------------------|
| Rank | Best | Better | Okay |
| Status | Provisional | Provisional | Provisional |
| Design Role | Reference | Alternative | Alternative |
| Motor Class | 2806.5 | 2807 | 2806.5 |
| KV | 1300 | 1300 | 1350 |
| MP-1 Voltage | 4S | 4S | 4S |
| Weight | 46.6 g | To Verify | To Verify |
| Published Current Evidence | 45.1 A test point | To Verify | To Verify |
| Documentation | Excellent | Good | Fair |
| Independent Testing | Available | Available | Limited |
| Fixed-Wing Evidence | Strongest | Moderate | Limited |
| Engineering Confidence | High | Medium | Low–Medium |
| Primary Trade-off | Cost and availability | Weaker documentation | Limited fixed-wing evidence |

## Recommendation

The T-Motor F90 2806.5 1300KV remains the reference motor because it is the original Flightory selection and has the strongest published engineering evidence.

Static propulsion current shall be measured with the final propeller before the power-module current path is approved.

---

# Electronic Speed Controller Evaluation

| Attribute | Hobbywing Skywalker 50A V2 | Hobbywing Skywalker 40A V2 | ZTW Beatles 40A | T-Motor AT40A |
|----------|-----------------------------|-----------------------------|-----------------|---------------|
| Rank | Best | Better | Okay | Okay |
| Status | Provisional | Provisional | Provisional | Research |
| Design Role | Reference | Alternative | Alternative | Alternative |
| Continuous Current | 50 A | 40 A | 40 A | 40 A nominal |
| Peak Current | 70 A | 60 A | 50 A | To Verify |
| Battery Compatibility | 3–4S LiPo | 3–4S LiPo | 2–4S LiPo | 2–4S reported |
| BEC | 5 V/5 A switching | 5 V/5 A switching | 5 V/3 A | To Verify |
| Published Weight | 36 g | 36 g | 36 g | To Verify |
| Programming | Extensive | Extensive | Standard | Unknown |
| Active Freewheeling | Yes | Yes | Not identified | Unknown |
| Search Mode | Yes | Yes | No | Unknown |
| Protection | Comprehensive | Comprehensive | Standard | Unknown |
| Telemetry | No | No | No | Unknown |
| Documentation | Excellent | Excellent | Good | Fair |
| Engineering Confidence | High | High | Medium–High | Medium |
| Primary Trade-off | No telemetry | Reduced current margin | Smaller BEC and lower peak margin | Incomplete documentation |

## Recommendation

The Hobbywing Skywalker 50A V2 remains the MP-1 reference ESC.

Its integrated 5 V/5 A switching BEC is the baseline servo-power source for the initial configuration, subject to loaded bench verification.

---

# Servo-Power Architecture Evaluation

## Candidate Comparison

| Attribute | Skywalker 50A V2 Integrated BEC | Hobbywing UBEC 5A at 5.0 V |
|----------|----------------------------------|-----------------------------|
| Rank | Best | Better |
| Status | Provisional | Future Evaluation |
| Design Role | Reference | Contingency Alternative |
| Output Voltage | 5.0 V | Selectable; use 5.0 V |
| Continuous Current | 5 A | 5 A |
| Published Transient Current | Not separately specified | 15 A instantaneous |
| Added Mass | None beyond selected ESC | Approximately 21 g |
| Added Wiring | None beyond baseline | Yes |
| Fault Separation from ESC | No | Yes |
| Baseline Simplicity | Best | Reduced |
| Parallel-Source Risk | None when used alone | ESC positive lead must be isolated |
| Engineering Confidence | Medium–High pending test | High as a contingency |
| Primary Trade-off | Shared ESC and servo-power failure domain | Added mass and wiring |

## Baseline Decision

Use the Skywalker 50A V2 integrated BEC for the initial MP-1 configuration.

The baseline remains provisional until testing confirms:

- Servo rail remains above 4.8 V during simultaneous rapid movement
- No flight-controller reset
- No receiver reset
- No unacceptable control-surface jitter
- No unacceptable throttle-induced voltage sag or noise
- Acceptable ESC and BEC temperature

## Contingency Decision

The Hobbywing UBEC 5A shall remain outside the initial build.

It may be introduced only if:

- The integrated ESC BEC fails verification
- Additional servos increase the load
- Later flight-critical equipment requires greater current
- Formal fault-separation requirements are added

---

# Main Flight Battery Evaluation

## Battery Architecture

The MP-1 battery baseline is:

- Conventional 4S LiPo chemistry
- 14.8 V nominal
- 16.8 V fully charged
- Soft-pack construction
- XT60 main connector
- JST-XH balance connector
- Approximately 5,000–6,000 mAh
- Direct interchangeability without changing propulsion, wiring, avionics, or aircraft hardware

Li-ion, 3S LiPo, 5S LiPo, hardcase LiPo, and adapter-dependent configurations are outside the MP-1 baseline.

## Candidate Comparison

| Attribute | Tattu G-Tech 5200 35C | Admiral 5000 40C | SMC HCL-HP 5200 80C | Ovonic 6000 120C |
|----------|------------------------|------------------|------------------------|-------------------|
| Rank | Best | Better | Okay | Okay |
| Status | Provisional | Provisional | Provisional | Research |
| Design Role | Reference | Alternative | Alternative | Extended-Capacity Alternative |
| Chemistry | LiPo | LiPo | LiPo | LiPo |
| Cell Count | 4S | 4S | 4S | 4S |
| Nominal Voltage | 14.8 V | 14.8 V | 14.8 V | 14.8 V |
| Fully Charged Voltage | 16.8 V | 16.8 V | 16.8 V | 16.8 V |
| Capacity | 5,200 mAh | 5,000 mAh | 5,200 mAh | 6,000 mAh |
| Nominal Energy | 76.96 Wh | 74.0 Wh | 76.96 Wh | 88.8 Wh |
| Published Weight | 436.5 g | 476 g | 517 g | 510 g |
| Calculated Specific Energy | Approximately 176 Wh/kg | Approximately 155 Wh/kg | Approximately 149 Wh/kg | Approximately 174 Wh/kg |
| Published Dimensions | 133 × 45 × 33.5 mm | 158 × 46 × 30 mm | 150 × 51 × 30 mm | 155 × 46 × 35 mm |
| Published C-Rating | 35C | 40C | 80C | 120C |
| Main Connector | XT60 | XT60 | Factory XT60 option | XT60 |
| Balance Connector | JST-XH-compatible | JST-XH | JST-XH | JST-XH |
| Construction | Soft pack | Soft pack | Soft pack | Soft pack |
| Documentation | Good | Good | Excellent | Fair–Good |
| Availability Confidence | Medium–High | High | Medium–High | Variable |
| Engineering Confidence | High | High | Medium–High | Medium |
| Primary Strength | Best mass and energy balance | Strong support and conventional aircraft use | Strong documentation | Highest nominal energy |
| Primary Trade-off | Availability should be confirmed | Heavier and longer for less energy | Heaviest for the same energy | Additional CG and flight-validation burden |

## Derived Endurance Comparison

The following values use an estimated 4 A cruise current and 80% usable battery capacity.

| Candidate | Usable Capacity at 80% | Calculated Cruise Endurance |
|----------|-------------------------:|----------------------------:|
| Tattu G-Tech 5200 | 4.16 Ah | Approximately 62 minutes |
| Admiral 5000 | 4.00 Ah | Approximately 60 minutes |
| SMC HCL-HP 5200 | 4.16 Ah | Approximately 62 minutes |
| Ovonic 6000 | 4.80 Ah | Approximately 72 minutes |

These are sizing estimates, not guaranteed flight times.

## Recommendation

### Best

**Tattu G-Tech 4S 5200 mAh 35C LiPo with XT60**

This pack provides the strongest balance of energy, mass, dimensions, connector compatibility, and discharge capability.

### Better

**Admiral 4S 5000 mAh 40C LiPo with XT60**

This is the strongest conventional alternative.

### Okay

**SMC HCL-HP 4S 5200 mAh 80C with factory XT60**

This pack is acceptable but carries substantially more mass than the reference for the same nominal energy.

### Extended-Capacity Research Option

**Ovonic 4S 6000 mAh 120C LiPo with XT60**

This pack requires explicit center-of-gravity, launch, climb, landing, and endurance validation.

---

# Flight Controller Evaluation

## Initial Flight Controller Requirements

The flight controller shall support the initial autonomous fixed-wing architecture without requiring a companion computer.

| Requirement | Target |
|-------------|--------|
| Firmware | Full ArduPlane support |
| Processor | STM32H7 class |
| Onboard Mission Execution | Required |
| Waypoint Navigation | Required |
| Return-to-Launch | Required |
| RC Pilot Takeover | Required |
| Manual Takeoff | Required |
| Manual Landing | Required |
| PWM Outputs | At least 8 required; at least 12 preferred |
| IMU Redundancy | At least two IMUs preferred |
| Barometer | At least one |
| Serial Connectivity | GPS, receiver, telemetry, and required sensors |
| CAN | At least one; two preferred |
| GPS / Compass | Dedicated or clearly documented integration path |
| Airspeed Sensor | I²C or CAN support if used |
| Receiver Support | S.Bus and UART-based receiver support |
| Power Monitoring | Voltage and current sensing required |
| Servo Power | Defined independently from flight-controller logic power |
| Logging | Removable microSD preferred |
| Companion Computer | Not required for initial flight |
| Connector System | Keyed, documented, replaceable harnesses preferred |
| Mechanical Installation | Must fit the LARK avionics area |
| Lifecycle | Current production hardware |
| Documentation | Manufacturer and ArduPilot documentation required |

## Candidate Comparison

| Attribute | Holybro Pixhawk 6C Mini | CubePilot Cube Orange+ with Mini Carrier | Matek H743-WING V3 | Holybro Pixhawk 6X with Mini Baseboard | SpeedyBee F405 Wing |
|----------|--------------------------|------------------------------------------|----------------------|------------------------------------------|----------------------|
| Rank | Best | Better | Better | Okay | Okay |
| Status | Provisional | Provisional | Provisional | Provisional | Rejected |
| Design Role | Reference | Premium Alternative | Integrated Alternative | Premium Alternative | Alternative |
| Processor | STM32H743 | STM32H757 | STM32H743 | STM32H753 | STM32F405 |
| IMUs | 2 | 3 | 2 | 3 | 1 primary architecture |
| Barometers | 1 | 2 | 1 | 2 | 1 |
| Sensor Temperature Control | Yes | Yes | Not documented as active control | Yes | No |
| PWM Outputs | 14 | Up to 14 | 13 | 16 | 12 |
| Serial Interfaces | Dedicated GPS/RC plus general serial ports | Multiple carrier-board interfaces | 7 UARTs | Dedicated GPS/RC plus 4 general serial ports | Multiple UARTs |
| CAN | 2 | 2 | 1 | 2 | 1 |
| GPS Integration | Strong | Strong | Strong | Strong | Strong |
| Onboard Waypoint Mission | Pass | Pass | Pass | Pass | Pass with reduced feature headroom |
| Return-to-Launch | Pass | Pass | Pass | Pass | Pass |
| RC Pilot Takeover | Pass | Pass | Pass | Pass | Pass |
| Companion Computer Required | No | No | No | No | No |
| Servo Power | External rail required | External rail required | Integrated selectable BEC | External rail required | Integrated wing power board |
| Current Monitoring | External analog module | External compatible module | Integrated sensor | External digital module | Integrated sensor |
| Logging | microSD | microSD | microSD | microSD | microSD |
| Connector Style | JST-GH plus PWM headers | Carrier-board connectors | Mixed connectors and solder pads | JST-GH/baseboard connectors | Mixed connectors and solder pads |
| Documentation | Excellent | Excellent | Good | Excellent | Good |
| Engineering Confidence | High | High | Medium–High | High | Medium |
| Primary Strength | Best balance of capability, redundancy, size, and standardized integration | Highest mature redundancy | Lowest external power-distribution burden | Maximum expansion | Low cost and compact integration |
| Primary Trade-off | External power module and servo-power design required | Cost, size, and complexity | More soldering and concentrated functions | Larger, heavier, and excessive | Processor and firmware limitations |

## Functional Compliance

| Requirement | Pixhawk 6C Mini | Cube Orange+ Mini | Matek H743-WING V3 | Pixhawk 6X Mini | SpeedyBee F405 Wing |
|-------------|-----------------|-------------------|----------------------|-----------------|----------------------|
| Full ArduPlane Support | Pass | Pass | Pass | Pass | Partial |
| H7-Class Processor | Pass | Pass | Pass | Pass | Fail |
| Onboard Waypoint Execution | Pass | Pass | Pass | Pass | Pass |
| Return-to-Launch | Pass | Pass | Pass | Pass | Pass |
| RC Pilot Takeover | Pass | Pass | Pass | Pass | Pass |
| At Least 8 PWM Outputs | Pass | Pass | Pass | Pass | Pass |
| Redundant IMUs | Pass | Pass | Pass | Pass | Fail |
| CAN Support | Pass | Pass | Pass | Pass | Pass |
| GPS / Compass Integration | Pass | Pass | Pass | Pass | Pass |
| Receiver Integration | Pass | Pass | Pass | Pass | Pass |
| Telemetry Integration | Pass | Pass | Pass | Pass | Pass |
| Removable Logging Media | Pass | Pass | Pass | Pass | Pass |
| Companion Computer Required | No | No | No | No | No |
| External Power Module Required | Yes | Yes | No | Yes | No |
| Separate Servo-Power Design Required | Yes | Yes | No | Yes | No |
| Appropriate for Initial MP-1 Baseline | Pass | Pass with complexity penalty | Pass with integration penalty | Pass with overcapacity concern | Fail |

## Recommendation

Purchase:

> **Holybro Pixhawk 6C Mini**

The Pixhawk 6C Mini provides the best balance for the initial MP-1 configuration and can store and execute the waypoint mission onboard without a companion computer.

---

# Flight-Controller Power Module Evaluation

## Requirements

| Requirement | Target |
|-------------|--------|
| Pixhawk Interface | Analog power interface compatible with Pixhawk 6C Mini |
| Battery Voltage | Must include 4S LiPo maximum of 16.8 V |
| Current Sensing | Must include verified peak propulsion current |
| Continuous Current Path | Must exceed verified sustained current |
| Burst Current Path | Must exceed verified takeoff and climb current |
| Connector System | XT60 preferred |
| Harness | Keyed flight-controller cable preferred |
| Calibration | Manufacturer values or approved procedure |
| Installed Mass | Minimized |
| Added Distribution | Avoid unless required |

## Candidate Comparison

| Attribute | Holybro PM02 V3 | Holybro PM06 V2 | Holybro PM07 | Mauch 100 A Hall System | Holybro PM02D / PM06D |
|----------|------------------|-----------------|--------------|-------------------------|-------------------------|
| Rank | Best | Better | Okay | Okay | Okay |
| Status | Research | Research | Research | Future Evaluation | Rejected |
| Design Role | Reference | Alternative | Alternative | Premium Alternative | Alternative |
| Pixhawk 6C Mini Interface | Compatible analog interface | Compatible analog interface | Compatible analog interface | Requires integration | Incompatible digital architecture |
| Battery Range | Suitable for 4S | Suitable for 4S | Suitable for 4S | Suitable, configuration dependent | Electrically broad but wrong interface |
| Board-Level Current Capability | Adequate in principle | Higher | Higher | High | Not relevant |
| Stock Harness Concern | Must be reconciled with sustained current | Must be verified | Must be verified | User-installed path | Not applicable |
| Current Sensing Range | Adequate | Adequate | Adequate | 100 A class | Not applicable |
| Built-In Distribution | No | Yes | Yes | No | Varies |
| Added Mass / Complexity | Lowest | Moderate | Highest | High | Not suitable |
| Documentation | Strong | Strong | Strong | Strong | Strong |
| Engineering Confidence | Medium pending current-path verification | Medium | Medium | Medium–High | High rejection confidence |
| Primary Trade-off | Stock harness may limit continuous current | Added distribution unnecessary | Oversized | More integration work | Wrong interface |

## Current Recommendation

The Holybro PM02 V3 remains the leading candidate because it is the cleanest match to the Pixhawk 6C Mini and minimal initial-flight architecture.

It shall not advance from Research to Provisional until static propulsion testing confirms that the complete stock current path is adequate for the verified sustained and burst load.

---

# GPS / Compass Evaluation Basis

GPS and compass are flight-critical because MP-1 must execute onboard waypoint missions and return-to-launch.

## Requirements

| Requirement | Target |
|-------------|--------|
| ArduPlane Support | Required |
| Pixhawk 6C Mini Interface | Direct and documented |
| GPS Position | Required |
| Compass Heading | Required |
| Home Position | Required |
| Waypoint Navigation | Required |
| Return-to-Launch | Required |
| Connector | Keyed harness preferred |
| Placement | Adequate separation from propulsion-current wiring |
| Lifecycle | Current production preferred |

Status: **Evaluation Pending**

---

# RC Receiver Evaluation Basis

The RC receiver is flight-critical because manual flight and pilot takeover are required.

## Requirements

| Requirement | Target |
|-------------|--------|
| Manual Control | Required |
| Stabilized Flight Control | Required |
| Flight-Mode Selection | Required |
| Autonomous-Mode Exit | Required |
| Pilot Takeover | Required |
| Link-Loss Failsafe | Required |
| Pixhawk Compatibility | Direct and documented |
| Power Requirement | Compatible with selected rail |
| Telemetry Dependency | None |

Status: **Evaluation Pending**

---

# Telemetry Radio Evaluation Basis

Telemetry is required for engineering monitoring and configuration, but not for onboard mission execution.

## Requirements

| Requirement | Target |
|-------------|--------|
| Mission Upload | Required before flight |
| Parameter Review | Required |
| Ground Monitoring | Required |
| Flight-Mode Reporting | Required |
| Position Reporting | Required |
| Battery Reporting | Required |
| Mission Continuation after Link Loss | Required |
| RC Pilot Takeover after Link Loss | Required |
| Pixhawk Compatibility | Direct and documented |

Status: **Evaluation Pending**

---

# Deferred Equipment Evaluation

| Item | Status | Initial-Baseline Decision |
|------|--------|---------------------------|
| Companion Computer | Future Evaluation | Do not procure |
| Payload Battery | Future Evaluation | Do not procure |
| Payload Regulator | Future Evaluation | Do not procure |
| Mission-Equipment Power Distribution | Future Evaluation | Do not procure |
| Redundant Flight-Controller Power | Future Evaluation | Do not procure |
| Redundant Servo Power | Future Evaluation | Do not procure |
| Camera Payload | Future Evaluation | Do not procure |
| Experimental Mission Sensors | Future Evaluation | Do not procure |
| Autonomous Takeoff Capability | Future Evaluation | Manual takeoff baseline |
| Autonomous Landing Capability | Future Evaluation | Manual landing baseline |

---

# Rejected Battery Architectures

| Architecture | Status | Engineering Rationale |
|--------------|--------|-----------------------|
| 3S LiPo | Rejected | Does not match the selected 4S propulsion baseline. |
| 5S LiPo | Rejected | Exceeds the selected ESC input range and requires propulsion revalidation. |
| 4S Li-ion | Rejected for MP-1 | Adds pack-design and integration complexity without sufficient benefit to the initial mission. |
| Hardcase LiPo | Rejected | Adds unnecessary mass and volume. |
| Adapter-Dependent Pack | Rejected | Conflicts with the direct battery-interface requirement. |
| Pack Above Approximately 525 g | Research Only | Requires separate airframe, CG, launch, landing, and endurance analysis. |

---

# Procurement Philosophy

Component rankings are determined using the following order of evidence:

1. Engineering requirements
2. Published manufacturer specifications
3. Original Flightory design references
4. Independent engineering testing
5. Community operational experience
6. Engineering evaluation
7. Procurement
8. Verification testing

Verification validates the selected hardware after procurement. It shall not be used to excuse unsupported or undocumented hardware selection.

---

# Remaining Initial Procurement Evaluations

The remaining initial-flight procurement evaluations shall proceed in this order:

1. Flight-controller power module
2. GPS / compass
3. RC receiver
4. Telemetry radio
5. Propeller
6. Airspeed sensor, if required by the flight-test plan

The physical and electrical interface matrix shall be created after the full initial procurement set is selected.

---

# Revision History

## Revision 3

- Aligned the evaluation matrix with EDR-0001 and the initial-flight requirements.
- Defined the minimal flight-critical procurement boundary.
- Required onboard waypoint mission execution without a companion computer.
- Removed companion-computer capability from initial selection scoring.
- Removed payload power and redundant avionics power from the initial baseline.
- Added the servo-power architecture evaluation.
- Established the Skywalker integrated BEC as the provisional baseline.
- Retained the Hobbywing UBEC 5A as a future contingency.
- Added the flight-controller power-module evaluation.
- Added GPS/compass, RC receiver, and telemetry evaluation bases.
- Updated the remaining procurement order.

## Revision 2

- Added the flight-controller evaluation.
- Selected the Pixhawk 6C Mini as the provisional reference.
- Retained Cube Orange+, Matek H743-WING V3, and Pixhawk 6X as alternatives.
- Rejected SpeedyBee F405 Wing for the reference role.

## Revision 1

- Added the 4S LiPo battery evaluation.
- Selected the Tattu G-Tech 5200 mAh battery as the provisional reference.
- Added battery-interface and rejected-architecture decisions.

## Revision 0

- Initial servo, motor, and ESC evaluations completed.
