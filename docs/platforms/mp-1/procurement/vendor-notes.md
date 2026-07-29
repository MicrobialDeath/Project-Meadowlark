# Vendor Notes

## Purpose

This document records the engineering rationale behind MP-1 procurement decisions. It complements the procurement matrix by documenting manufacturer quality, source confidence, product-family observations, long-term support considerations, and unresolved risks.

Engineering decisions follow this order:

1. Requirements
2. Manufacturer documentation
3. Original Flightory design references
4. Independent engineering testing
5. Community operational experience
6. Engineering evaluation
7. Procurement
8. Verification testing

Verification testing is used to validate procurement decisions after purchase, not to discover whether an undocumented component is acceptable.

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

---

# Source Confidence

| Confidence | Meaning |
|------------|---------|
| Verified | Manufacturer documentation and MP-1 engineering validation are both available. |
| High | Strong manufacturer documentation supported by reputable independent evidence. |
| Medium | Useful evidence exists, but manufacturer data or independent validation is incomplete. |
| Low | Evidence is primarily community-based, indirect, or insufficiently documented. |

---

# Flight Control Servos

## Corona DS929MG

### Summary

The Corona DS929MG is the current MP-1 reference servo because it is the closest documented match to the Flightory LARK baseline while remaining within the preferred weight and torque envelope.

### Strengths

- Closest match to the Flightory reference configuration
- Lightweight
- Metal gears
- Suitable operating voltage
- Adequate torque for the current airframe class
- Strong value

### Weaknesses

- Manufacturer documentation is less complete than Hitec documentation
- Long-term product availability should be monitored
- Published stall-current data should be confirmed during verification testing

Documentation Quality: **Good**

Engineering Confidence: **High**

Procurement Rank: **Best**

Status: **Provisional**

Design Role: **Reference**

---

## Hitec HS-82MG

### Summary

The Hitec HS-82MG is the documentation and support benchmark among the evaluated micro aviation servos. It offers strong torque and established aviation use, but its higher mass is a meaningful MP-1 trade-off.

### Strengths

- Excellent manufacturer documentation
- Established aviation use
- Strong torque
- Metal gears
- Long-term product and replacement support

### Weaknesses

- Heavier than the preferred MP-1 servo target
- Higher cost than the Corona reference candidate

Documentation Quality: **Excellent**

Engineering Confidence: **High**

Procurement Rank: **Better**

Status: **Provisional**

Design Role: **Alternative**

---

## EMAX ES08MD II

### Summary

The EMAX ES08MD II is a mechanically suitable digital-servo alternative, but incomplete electrical characterization limits confidence relative to the Corona and Hitec candidates.

### Strengths

- Lightweight
- Metal gears
- Digital control
- Competitive price

### Weaknesses

- Incomplete published current data
- Less complete aviation-specific documentation
- Long-term consistency between production revisions should be verified

Documentation Quality: **Fair**

Engineering Confidence: **Medium**

Procurement Rank: **Okay**

Status: **Provisional**

Design Role: **Alternative**

---

# Brushless Propulsion Motors

## T-Motor F90 2806.5 1300KV

### Summary

The T-Motor F90 2806.5 1300KV is the current MP-1 propulsion reference because it is the motor used in the Flightory LARK and has the strongest available published engineering data.

### Strengths

- Direct Flightory reference
- Excellent manufacturer documentation
- Published thrust and current data
- Suitable geometry for the MP-1 airframe
- Strong efficiency and build quality

### Weaknesses

- Manufacturer material emphasizes higher-voltage operation even though the Flightory configuration uses 4S
- Final propeller and current limits must be validated on the MP-1 installation
- Availability and price may be less favorable than the EMAX alternative

Documentation Quality: **Excellent**

Engineering Confidence: **High**

Procurement Rank: **Best**

Status: **Provisional**

Design Role: **Reference**

---

## EMAX ECO II 2807 1300KV

### Summary

The EMAX ECO II 2807 1300KV is the strongest value-oriented alternative. Its geometry and KV are suitable, and useful independent testing exists, but the total evidence set remains weaker than for the T-Motor reference.

### Strengths

- Competitive price
- Suitable motor class and KV
- Good community availability
- Useful independent test evidence
- Broad replacement availability

### Weaknesses

- Manufacturer data is less complete than T-Motor documentation
- Exact MP-1 propeller and current behavior requires validation
- Production revisions should be checked before purchase

Documentation Quality: **Good**

Engineering Confidence: **Medium**

Procurement Rank: **Better**

Status: **Provisional**

Design Role: **Alternative**

---

## FlyFishRC Flash 2806.5 1350KV

### Summary

The FlyFishRC Flash 2806.5 1350KV is mechanically plausible for MP-1 but is supported by less fixed-wing-specific evidence than the preferred candidates.

### Strengths

- Suitable motor geometry
- KV close to the MP-1 target
- Modern construction
- Competitive mass

### Weaknesses

- Primarily marketed toward FPV and multirotor use
- Limited fixed-wing endurance evidence
- Less complete independent data for the intended MP-1 propeller range

Documentation Quality: **Fair**

Engineering Confidence: **Low–Medium**

Procurement Rank: **Okay**

Status: **Provisional**

Design Role: **Alternative**

---

# Electronic Speed Controllers

## Hobbywing Skywalker 50A V2

### Summary

The Hobbywing Skywalker 50A V2 is the current MP-1 reference ESC. It provides the strongest combination of current margin, fixed-wing-specific firmware, BEC capability, documentation quality, and protection features.

### Strengths

- Fixed-wing-specific product family
- 50 A continuous current rating
- 70 A peak current rating
- 5 V/5 A switching BEC
- Active Freewheeling / DEO
- Search Mode
- Configurable brake, timing, startup, and low-voltage behavior
- Comprehensive thermal, overload, low-voltage, and signal-loss protection
- Excellent documentation
- Same published dimensions and mass as the 40 A model

### Weaknesses

- No native telemetry
- Final thermal margin depends on installation airflow
- BEC loading must still be verified with the complete avionics suite
- Battery-input connector must be installed during aircraft assembly
- Motor connector compatibility must be confirmed during harness design

Documentation Quality: **Excellent**

Engineering Confidence: **High**

Procurement Rank: **Best**

Status: **Provisional**

Design Role: **Reference**

Recommendation:

Use the Hobbywing Skywalker 50A V2 as the MP-1 reference ESC.

---

## Hobbywing Skywalker 40A V2

### Summary

The Skywalker 40A V2 is a strong lower-current alternative. It retains the same product-family features and BEC capability as the 50 A model but provides less propulsion-current margin.

### Strengths

- Fixed-wing-specific firmware
- 5 V/5 A switching BEC
- Excellent documentation
- Active Freewheeling / DEO
- Search Mode
- Comprehensive protection features
- Same published dimensions and mass as the 50 A model

### Weaknesses

- Reduced continuous-current margin
- Reduced peak-current margin
- Less tolerant of aggressive propeller or motor combinations

Documentation Quality: **Excellent**

Engineering Confidence: **High**

Procurement Rank: **Better**

Status: **Provisional**

Design Role: **Alternative**

---

## ZTW Beatles 40A

### Summary

The ZTW Beatles 40A is a credible budget-oriented fixed-wing ESC. It is acceptable for MP-1 but provides less BEC capability, lower burst-current margin, and fewer advanced features than the Hobbywing reference.

### Strengths

- Established fixed-wing product family
- Competitive pricing
- Adequate manufacturer documentation
- Standard fixed-wing programming functions

### Weaknesses

- 5 V/3 A BEC
- Lower peak-current capability
- Fewer advanced firmware features
- Reduced engineering margin relative to the Hobbywing 50 A reference

Documentation Quality: **Good**

Engineering Confidence: **Medium–High**

Procurement Rank: **Okay**

Status: **Provisional**

Design Role: **Alternative**

---

## T-Motor AT40A

### Summary

The T-Motor AT40A appears technically suitable as a conventional fixed-wing ESC, but the available manufacturer documentation is not yet complete enough to support a provisional procurement recommendation.

### Strengths

- Established aviation manufacturer
- Plausible current class for MP-1
- Fixed-wing product positioning

### Weaknesses

- Incomplete public technical documentation
- BEC specifications require confirmation
- Peak-current, protection, programming, dimensions, and mass require confirmation
- No clear advantage over the documented Hobbywing candidates

Documentation Quality: **Fair**

Engineering Confidence: **Medium**

Procurement Rank: **Okay**

Status: **Research**

Design Role: **Alternative**

---

## AM32 / BLHeli32 ESCs

### Summary

Modern firmware-based ESCs offer telemetry, RPM feedback, and advanced diagnostics. They remain outside the current MP-1 baseline because most are optimized for multirotors and often require additional power-system integration.

### Strengths

- Digital throttle protocols
- RPM feedback
- Telemetry
- Advanced configuration and diagnostics
- Strong future potential for closed-loop propulsion monitoring

### Weaknesses

- Greater integration complexity
- Often lack an integrated aviation-grade BEC
- Product documentation varies substantially by hardware vendor
- Limited benefit for the current simple endurance fixed-wing architecture
- Greater firmware and configuration-management burden

Documentation Quality: **Variable**

Engineering Confidence: **Medium**

Procurement Rank: **Okay**

Status: **Future Evaluation**

Design Role: **Alternative**

---

# Main Flight Batteries

## Battery Architecture Decision

MP-1 will use a removable 4S soft-pack LiPo battery as the baseline energy-storage system.

The selected battery must be directly exchangeable without changing:

- Motor
- ESC
- Propeller
- Wiring
- Avionics
- Connectors
- Mounting hardware
- Aircraft configuration

The aircraft-side interface is standardized on XT60 for the main power connection and JST-XH for balance charging.

The current battery evaluation range is 5,000–6,000 mAh. The preferred pack mass is no more than 450 g, with heavier packs up to approximately 525 g treated as experimental or alternative configurations requiring additional flight validation.

---

## Tattu G-Tech 4S 5200 mAh 35C with XT60

### Summary

The Tattu G-Tech 4S 5200 mAh 35C pack is the current MP-1 reference battery. It offers the strongest balance of stored energy, pack mass, physical dimensions, connector compatibility, and published specifications among the evaluated candidates.

### Strengths

- 4S LiPo architecture directly matches the selected propulsion baseline
- 5,200 mAh capacity
- 76.96 Wh nominal energy
- 436.5 g published mass
- Approximately 176 Wh/kg calculated specific energy
- Compact 133 × 45 × 33.5 mm published dimensions
- Factory XT60 main connector
- JST-XH-compatible balance connection
- Claimed current capability substantially exceeds MP-1 requirements
- Only evaluated candidate that meets the preferred 450 g mass target

### Weaknesses

- Availability should be confirmed before purchase
- Claimed C-rating is not independently treated as a primary decision metric
- Actual installed endurance, voltage sag, and thermal behavior require verification testing

Documentation Quality: **Good**

Engineering Confidence: **High**

Procurement Rank: **Best**

Status: **Provisional**

Design Role: **Reference**

Recommendation:

Use the Tattu G-Tech 4S 5200 mAh 35C soft-pack LiPo with XT60 as the MP-1 reference flight battery.

---

## Admiral 4S 5000 mAh 40C with XT60

### Summary

The Admiral 4S 5000 mAh 40C pack is the strongest conventional alternative. It is a credible aircraft-oriented product with useful retailer support and complete published specifications.

### Strengths

- Aircraft-oriented product positioning
- Factory XT60 connector
- 5,000 mAh capacity
- Strong retailer support and availability
- Complete published mass and dimensional data
- Adequate current capability for MP-1

### Weaknesses

- 476 g published mass
- Heavier than the Tattu reference
- Longer physical footprint
- Slightly lower stored energy at 74 Wh
- Lower calculated specific energy at approximately 155 Wh/kg

Documentation Quality: **Good**

Engineering Confidence: **High**

Procurement Rank: **Better**

Status: **Provisional**

Design Role: **Alternative**

---

## SMC HCL-HP 4S 5200 mAh 80C Flight Pack with Factory XT60

### Summary

The SMC HCL-HP 4S 5200 mAh pack is a technically well-documented alternative with configurable factory connectors. It is acceptable for MP-1 but carries a substantial mass penalty for the same nominal energy as the Tattu reference.

### Strengths

- Strong technical documentation
- Factory XT60 option
- Published construction and dimensional information
- 5,200 mAh capacity
- High claimed current capability
- Competitive procurement cost

### Weaknesses

- 517 g published mass
- Approximately 80.5 g heavier than the Tattu reference
- Same nominal energy as the Tattu
- Lower calculated specific energy at approximately 149 Wh/kg
- High C-rating provides little practical benefit for the MP-1 endurance mission

Documentation Quality: **Excellent**

Engineering Confidence: **Medium–High**

Procurement Rank: **Okay**

Status: **Provisional**

Design Role: **Alternative**

---

## Ovonic 4S 6000 mAh 120C with XT60

### Summary

The Ovonic 4S 6000 mAh pack is the extended-capacity research candidate. It provides the highest nominal energy among the evaluated packs while retaining competitive calculated specific energy.

### Strengths

- 6,000 mAh capacity
- 88.8 Wh nominal energy
- Approximately 174 Wh/kg calculated specific energy
- Factory XT60 connector
- Soft-pack construction
- Approximately ten additional calculated cruise minutes relative to the 5,200 mAh reference under the same sizing assumptions

### Weaknesses

- 510 g published mass
- Greater center-of-gravity influence
- Increased wing loading and landing energy
- Larger physical dimensions
- Documentation quality is weaker than Tattu, Admiral, or SMC
- Availability may be inconsistent
- Requires dedicated launch, climb, cruise-current, CG, landing, and endurance validation

Documentation Quality: **Fair–Good**

Engineering Confidence: **Medium**

Procurement Rank: **Okay**

Status: **Research**

Design Role: **Extended-Capacity Alternative**

---

## Rejected Battery Architectures

### 3S LiPo

Status: **Rejected**

Reason:

Does not match the selected 4S propulsion baseline and would reduce available propulsion performance.

### 5S LiPo

Status: **Rejected**

Reason:

Exceeds the documented 3S–4S input range of the selected Hobbywing Skywalker 50A V2 and would require ESC replacement and propulsion revalidation.

### 4S Li-ion

Status: **Rejected for MP-1**

Reason:

Not required for the MP-1 validation mission and introduces pack-design, sourcing, assembly, protection, and charging complexity without sufficient project benefit.

### Hardcase LiPo

Status: **Rejected**

Reason:

Adds unnecessary mass and volume for an aircraft application.

### Adapter-Dependent Battery Packs

Status: **Rejected**

Reason:

Conflicts with the requirement for direct battery interchangeability using a standardized aircraft-side connector.

### Packs Above Approximately 525 g

Status: **Research Only**

Reason:

May be physically possible within the LARK airframe, but require separate center-of-gravity, launch, landing, structural, and endurance analysis.

---

# Flight Controllers

## Flight Controller Architecture Decision

MP-1 requires a current-production H7-class flight controller with full ArduPlane support.

The reference architecture prioritizes:

- Mature ArduPilot support
- Redundant inertial sensing
- Compact fixed-wing packaging
- Standardized and replaceable harnesses
- Sufficient PWM, serial, CAN, GPS, receiver, telemetry, and sensor interfaces
- Removable flight logging
- Separation between flight-controller logic power and servo power
- A modular external power-monitoring path
- Future companion-computer integration through MAVLink

The final physical and electrical interface matrix will be created after the complete procurement set is selected.

---

## Holybro Pixhawk 6C Mini

### Summary

The Holybro Pixhawk 6C Mini is the current MP-1 reference flight controller. It provides the best overall balance of H7 processing, sensor redundancy, interface capacity, connector standardization, compact packaging, and ecosystem maturity.

### Strengths

- STM32H743 processor
- Full ArduPlane support
- Dual IMUs
- Temperature-controlled inertial sensors
- Fourteen PWM outputs
- Dual CAN buses
- Two dedicated GPS interfaces
- Dedicated receiver input
- Sufficient serial connectivity for GPS, telemetry, receiver, and companion-computer integration
- Removable microSD logging
- Standardized JST-GH Pixhawk connector ecosystem
- Compact installation compared with full-size Pixhawk or Cube systems
- Conventional modular architecture that separates the autopilot from the power module

### Weaknesses

- Requires a separate compatible power module
- Requires a separately defined servo-power bus
- Only one primary analog power input
- No Ethernet
- Current documentation lists more than one physical hardware revision, so the exact model revision, dimensions, mass, and harness package must be confirmed before ordering
- JST-GH avionics harnesses are not directly interchangeable with ordinary servo plugs

Documentation Quality: **Excellent**

Engineering Confidence: **High**

Procurement Rank: **Best**

Status: **Provisional**

Design Role: **Reference**

Recommendation:

Use the Holybro Pixhawk 6C Mini as the MP-1 reference flight controller.

---

## CubePilot Cube Orange+ with Mini Carrier Board

### Summary

The Cube Orange+ with a Mini Carrier Board is the strongest premium redundancy alternative. It offers a mature ArduPilot ecosystem, triple IMUs, dual barometers, modular carrier-board architecture, and strong environmental management.

### Strengths

- STM32H757 processor
- Triple IMUs
- Dual barometers
- Temperature-controlled sensors
- Mature and widely supported ArduPilot platform
- Modular flight module and carrier-board architecture
- Multiple serial and CAN interfaces
- Up to fourteen PWM outputs depending on carrier configuration
- Removable microSD logging
- Strong replacement and expansion flexibility
- Carrier-board options can support redundant power paths

### Weaknesses

- Higher procurement cost
- Larger installed assembly than the Pixhawk 6C Mini
- Carrier-board selection becomes part of the procurement baseline
- External power module and servo-power architecture still required
- Wiring and mechanical integration are more complex
- Some interface details depend on the specific carrier board rather than the flight module alone

Documentation Quality: **Excellent**

Engineering Confidence: **High**

Procurement Rank: **Better**

Status: **Provisional**

Design Role: **Premium Alternative**

---

## Matek H743-WING V3

### Summary

The Matek H743-WING V3 is the strongest integrated fixed-wing alternative. It combines the flight controller, battery input, voltage/current sensing, peripheral regulation, and servo-power regulation on a single fixed-wing-oriented board.

### Strengths

- STM32H743 processor
- Full ArduPlane support
- Fixed-wing-specific layout
- Direct 9–36 V battery input
- Integrated voltage and current sensing
- Integrated peripheral BEC
- Integrated selectable servo BEC
- Thirteen PWM outputs
- Seven UARTs
- CAN support
- Removable microSD logging
- Reduced requirement for a separate power module or servo-power regulator
- Potentially lower total installed mass and wiring count

### Weaknesses

- Less sensor redundancy than Pixhawk 6C Mini, Cube Orange+, or Pixhawk 6X
- More solder pads and mixed connector types
- Replacement may require desoldering or harness reconstruction
- More electrical functions are concentrated on one board
- Integrated current sensing can be sensitive to switching noise and installation practices
- Less standardized field-replacement ecosystem than Pixhawk hardware

Documentation Quality: **Good**

Engineering Confidence: **Medium–High**

Procurement Rank: **Better**

Status: **Provisional**

Design Role: **Integrated Alternative**

---

## Holybro Pixhawk 6X with Mini Baseboard

### Summary

The Pixhawk 6X with Mini Baseboard is a technically excellent but oversized premium alternative. It exceeds the current MP-1 requirements and is better suited to a future platform that needs Ethernet, dual primary power inputs, or additional sensor redundancy.

### Strengths

- STM32H753 processor
- Triple isolated IMU domains
- Dual barometers
- Temperature-controlled sensors
- Sixteen PWM outputs
- Dual CAN buses
- Two GPS interfaces
- Dual primary power inputs
- Ethernet
- Removable microSD logging
- Excellent ArduPilot and PX4 ecosystem support
- Strong expansion capability

### Weaknesses

- Higher cost
- Larger installed volume
- Greater mass
- More capability than MP-1 currently needs
- Requires an external compatible power module
- Requires a separately defined servo-power system
- Power-module choices may be constrained by the digital power-input architecture

Documentation Quality: **Excellent**

Engineering Confidence: **High**

Procurement Rank: **Okay**

Status: **Provisional**

Design Role: **Premium Alternative**

---

## SpeedyBee F405 Wing

### Summary

The SpeedyBee F405 Wing is a compact and economical fixed-wing integration package, but it does not meet the MP-1 reference-platform objective.

### Strengths

- Low cost
- Compact fixed-wing form factor
- Integrated power distribution
- Integrated current sensing
- Integrated servo and peripheral power functions
- Multiple PWM and serial interfaces
- CAN support
- Convenient configuration features

### Weaknesses

- STM32F405 processor rather than an H7-class processor
- ArduPilot omits some features because of flash-memory limitations
- Reduced long-term expansion headroom
- Less sensor redundancy
- Less appropriate as the durable autopilot foundation for Meadowlark autonomous-flight development

Documentation Quality: **Good**

Engineering Confidence: **Medium**

Procurement Rank: **Okay**

Status: **Rejected**

Design Role: **Alternative**

Reason for Rejection:

The controller is capable of useful fixed-wing operation, but its processor, memory constraints, and reduced redundancy conflict with the MP-1 goal of establishing a durable autonomous-flight reference architecture.

---

# Flight Controller Integration Consequences

Selecting the Pixhawk 6C Mini creates the following requirements for the remaining procurement evaluations:

1. Select a compatible external power module.
2. Define a separate servo-power bus.
3. Determine whether the ESC BEC, an external BEC, or a dedicated servo regulator will power the servo rail.
4. Confirm power-module voltage and current range for the 4S propulsion system.
5. Confirm GPS and compass connector compatibility.
6. Confirm receiver protocol and cable compatibility.
7. Confirm telemetry-radio interface and power requirements.
8. Confirm airspeed-sensor interface.
9. Reserve at least one MAVLink serial interface for a future companion computer.
10. Confirm exact Pixhawk 6C Mini hardware revision and supplied harness kit before purchase.
11. Define vibration isolation, orientation, cooling, and service access.
12. Complete the physical and electrical interface matrix after the full procurement set is selected.

---

# Flight Controller Verification Requirements

The reference flight controller must complete the following verification steps after procurement:

1. Confirm exact model and hardware revision.
2. Confirm physical dimensions and mass.
3. Confirm supplied cable and accessory set.
4. Inspect connector keying and pin assignments.
5. Load the approved ArduPlane firmware.
6. Confirm boot, logging, and microSD operation.
7. Confirm both IMUs and the barometer are detected.
8. Confirm PWM output operation.
9. Confirm receiver input.
10. Confirm GPS and compass communication.
11. Confirm telemetry communication.
12. Confirm CAN communication.
13. Confirm voltage and current monitoring with the selected power module.
14. Confirm servo-rail isolation and voltage.
15. Confirm failsafe behavior.
16. Confirm vibration levels during propulsion ground testing.
17. Confirm flight-controller temperature during operation.
18. Perform manual stabilized flight testing.
19. Perform return-to-launch and autonomous-mode verification.
20. Archive parameters, logs, firmware version, and verification evidence.

---

# Upcoming Procurement Categories

The remaining MP-1 procurement evaluations should proceed in this order:

1. Power Module / External BEC
2. GPS / Compass
3. RC Receiver
4. Telemetry Radio
5. Propeller
6. Companion Computer

---

# Revision History

- Initial servo vendor assessments completed.
- Brushless propulsion motor vendor assessments completed.
- Electronic speed controller vendor assessments completed.
- Procurement rank, status, and design role standardized as separate fields.
- MP-1 battery architecture standardized on removable 4S soft-pack LiPo batteries.
- Tattu G-Tech 4S 5200 mAh 35C with XT60 selected as the provisional reference battery.
- Admiral 5000, SMC HCL-HP 5200, and Ovonic 6000 retained as ranked alternatives.
- Rejected battery architectures and common-interface requirements documented.
- Holybro Pixhawk 6C Mini selected as the provisional reference flight controller.
- Cube Orange+, Matek H743-WING V3, and Pixhawk 6X retained as ranked alternatives.
- SpeedyBee F405 Wing rejected for the MP-1 reference role.
- Flight-controller integration and verification requirements added.
- Power module / external BEC evaluation pending.
