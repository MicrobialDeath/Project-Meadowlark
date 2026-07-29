# MP-1 Procurement Evaluation Matrix

## Purpose

This document records the engineering comparison of candidate hardware for the MP-1 platform. Rankings are based on published manufacturer documentation, original Flightory references, independent testing, community evidence, and engineering suitability.

All rankings remain provisional until the selected component is procured, integrated, and verified on MP-1.

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

---

# Flight Control Servo Evaluation

| Attribute | Corona DS929MG | Hitec HS-82MG | EMAX ES08MD II |
|----------|----------------|---------------|----------------|
| Rank | Best | Better | Okay |
| Status | Provisional | Provisional | Provisional |
| Design Role | Reference | Alternative | Alternative |
| Voltage | 4.8–6.0 V | 4.8–6.0 V | 4.8–6.0 V |
| Weight | 12.5 g | 19 g | ~12 g |
| Gear Material | Metal | Metal | Metal |
| Torque | 2.2–2.5 kg·cm | 3.4 kg·cm | ~2.4 kg·cm |
| Documentation | Good | Excellent | Fair |
| Engineering Confidence | High | High | Medium |
| Primary Trade-off | Less complete documentation | Higher mass and cost | Incomplete electrical characterization |

## Recommendation

The Corona DS929MG remains the reference servo because it most closely matches the Flightory LARK baseline while meeting the preferred mass and torque envelope.

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
| Peak Current | 45.1 A published test point | To Verify | To Verify |
| Documentation | Excellent | Good | Fair |
| Independent Testing | Available | Available | Limited |
| Fixed-Wing Evidence | Strongest | Moderate | Limited |
| Engineering Confidence | High | Medium | Low–Medium |
| Primary Trade-off | Cost and availability | Weaker documentation | Limited fixed-wing evidence |

## Recommendation

The T-Motor F90 2806.5 1300KV remains the reference propulsion motor because it is the original Flightory selection and has the strongest published engineering evidence.

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

The Hobbywing Skywalker 50A V2 remains the MP-1 reference ESC. It provides the strongest combination of current margin, documentation quality, switching-BEC capability, fixed-wing features, and protection functions.

The 40A V2 remains the strongest direct substitute. The ZTW Beatles 40A is an acceptable lower-margin alternative. The T-Motor AT40A remains under research pending complete manufacturer documentation.

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
| Calculated Specific Energy | ~176 Wh/kg | ~155 Wh/kg | ~149 Wh/kg | ~174 Wh/kg |
| Published Dimensions | 133 × 45 × 33.5 mm | 158 × 46 × 30 mm | 150 × 51 × 30 mm | 155 × 46 × 35 mm |
| Published C-Rating | 35C | 40C | 80C | 120C |
| Theoretical Claimed Continuous Current | 182 A | 200 A | 416 A | 720 A |
| Main Connector | XT60 | XT60 | Factory XT60 option | XT60 |
| Balance Connector | JST-XH-compatible | JST-XH | JST-XH | JST-XH |
| Construction | Soft pack | Soft pack | Soft pack | Soft pack |
| Documentation | Good | Good | Excellent | Fair–Good |
| Availability Confidence | Medium–High | High | Medium–High | Variable |
| Engineering Confidence | High | High | Medium–High | Medium |
| Primary Strength | Best mass and energy balance | Strong support and conventional aircraft use | Strong technical documentation | Highest nominal energy |
| Primary Trade-off | Availability should be confirmed before purchase | Heavier and longer for less energy | Heaviest pack for the same energy | Higher mass and additional CG/flight-validation burden |

## Derived Endurance Comparison

The following values use the Flightory reference estimate of approximately 4 A cruise current and 80% usable battery capacity. They are sizing estimates, not guaranteed flight times.

| Candidate | Usable Capacity at 80% | Calculated Cruise Endurance |
|----------|-------------------------:|----------------------------:|
| Tattu G-Tech 5200 | 4.16 Ah | ~62 minutes |
| Admiral 5000 | 4.00 Ah | ~60 minutes |
| SMC HCL-HP 5200 | 4.16 Ah | ~62 minutes |
| Ovonic 6000 | 4.80 Ah | ~72 minutes |

Actual endurance will depend on launch power, climb duration, propeller selection, all-up weight, wind, maneuvering, avionics load, reserve policy, and measured cruise current.

## Requirements Compliance

| Requirement | Tattu G-Tech 5200 | Admiral 5000 | SMC HCL-HP 5200 | Ovonic 6000 |
|-------------|-------------------|--------------|-------------------|-------------|
| 4S LiPo | Pass | Pass | Pass | Pass |
| Soft Pack | Pass | Pass | Pass | Pass |
| XT60 Without Adapter | Pass | Pass | Pass if ordered with factory XT60 | Pass |
| 5,000–6,000 mAh Range | Pass | Pass | Pass | Pass |
| Preferred Weight ≤450 g | Pass | Fail | Fail | Fail |
| Experimental Weight ≤525 g | Pass | Pass | Pass | Pass |
| Published Dimensions | Pass | Pass | Pass | Pass |
| Adequate Current Capability | Pass | Pass | Pass | Pass |
| Reference-Level Documentation | Pass | Pass | Pass | Partial |
| Baseline Flight Validation Required | Yes | Yes | Yes | Yes |
| Extended-Capacity Validation Required | No | No | No | Yes |

## Recommendation

### Best

**Tattu G-Tech 4S 5200 mAh 35C LiPo with XT60**

This pack provides the strongest overall balance of energy, mass, dimensions, connector compatibility, and discharge capability. Its calculated specific energy is the best in the comparison, and it is the only candidate that meets the preferred 450 g mass target.

### Better

**Admiral 4S 5000 mAh 40C LiPo with XT60**

This is the strongest conventional alternative because of its aircraft-oriented product positioning, retailer support, and complete specifications. Its main disadvantages are greater mass, greater length, and slightly lower stored energy.

### Okay

**SMC HCL-HP 4S 5200 mAh 80C Flight Pack with factory XT60**

This pack has strong technical documentation and factory connector flexibility. It is acceptable for MP-1 but carries substantially more mass than the Tattu while storing the same nominal energy.

### Extended-Capacity Research Option

**Ovonic 4S 6000 mAh 120C LiPo with XT60**

This pack offers the most nominal energy and competitive calculated specific energy, but the added mass requires explicit center-of-gravity, launch, climb, landing, and measured-endurance validation before it can be considered a routine MP-1 battery.

---

# Rejected Battery Architectures

| Architecture | Status | Engineering Rationale |
|--------------|--------|-----------------------|
| 3S LiPo | Rejected | Does not match the selected 4S propulsion baseline and would reduce available propulsion performance. |
| 5S LiPo | Rejected | Exceeds the documented 3S–4S input range of the selected Hobbywing Skywalker 50A V2 and would require ESC and propulsion revalidation. |
| 4S Li-ion | Rejected for MP-1 | Not required for the MP-1 validation mission and introduces pack-design, sourcing, assembly, and protection complexity. |
| Hardcase LiPo | Rejected | Adds unnecessary mass and volume for an aircraft application. |
| Adapter-Dependent Pack | Rejected | Conflicts with the direct, easily exchangeable battery-interface requirement. |
| Pack Above ~525 g | Research Only | May be physically possible, but requires separate airframe, CG, launch, landing, and endurance analysis. |

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

Verification testing occurs after procurement to validate these selections rather than establish whether undocumented hardware is acceptable.

---

# Revision History

- Initial flight-servo comparison completed.
- Brushless propulsion motor comparison completed.
- Electronic speed controller comparison completed.
- Procurement rank, status, and design role standardized as separate fields.
- MP-1 battery architecture standardized on removable 4S soft-pack LiPo batteries.
- Tattu G-Tech 4S 5200 mAh 35C selected as the provisional reference battery.
- Admiral 5000, SMC HCL-HP 5200, and Ovonic 6000 retained as ranked alternatives.
- Rejected battery architectures and compatibility constraints documented.
- Flight controller evaluation pending.
