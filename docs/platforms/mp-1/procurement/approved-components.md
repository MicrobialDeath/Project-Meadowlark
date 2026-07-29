# MP-1 Approved Components

## Purpose

This document identifies the current procurement candidates for the MP-1 platform. Components are ranked using the available engineering evidence collected before procurement. Rankings guide purchasing decisions and remain provisional until the selected hardware is validated through MP-1 integration and verification testing.

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

---

# Flight Control Servos

## Primary Flight Servos

| Rank | Component | Status | Design Role | Notes |
|------|-----------|--------|-------------|-------|
| Best | Corona DS929MG | Provisional | Reference | Closest documented match to the Flightory LARK reference design. |
| Better | Hitec HS-82MG | Provisional | Alternative | Strong documentation, established aviation use, and long-term manufacturer support, but heavier than preferred. |
| Okay | EMAX ES08MD II | Provisional | Alternative | Mechanically suitable digital servo with incomplete published electrical characterization. |

### Engineering Requirements

| Requirement | Target |
|-------------|--------|
| Operating Voltage | 4.8–6.0 V |
| Gear Material | Metal |
| Weight | ≤15 g preferred |
| Torque | ≥2.0 kg·cm at 6 V |
| Stall Current | ≤1.5 A preferred |
| Connector | JR/Futaba-compatible |

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

---

# Electronic Speed Controllers

## Propulsion ESC

| Rank | Component | Status | Design Role | Notes |
|------|-----------|--------|-------------|-------|
| Best | Hobbywing Skywalker 50A V2 | Provisional | Reference | 50 A continuous, 70 A peak, 5 V/5 A switching BEC, fixed-wing programming, and comprehensive protection features. |
| Better | Hobbywing Skywalker 40A V2 | Provisional | Alternative | Same published size and weight as the 50 A model, with reduced continuous and peak current margin. |
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

---

# Main Flight Batteries

## Battery Architecture Decision

MP-1 will use a removable **4S soft-pack LiPo battery**. Li-ion endurance packs and 5S LiPo packs are outside the current MP-1 procurement baseline.

The battery must be exchangeable without changing the motor, ESC, propeller, wiring, avionics, or aircraft configuration hardware.

## Flight Battery Candidates

| Rank | Component | Status | Design Role | Notes |
|------|-----------|--------|-------------|-------|
| Best | Tattu G-Tech 4S 5200 mAh 35C LiPo with XT60 | Provisional | Reference | Best current balance of energy, mass, dimensions, documentation, connector compatibility, and discharge capability. |
| Better | Admiral 4S 5000 mAh 40C LiPo with XT60 | Provisional | Alternative | Credible aircraft pack with good retailer support and documentation, but heavier and longer while storing slightly less energy. |
| Okay | SMC HCL-HP 4S 5200 mAh 80C Flight Pack with factory XT60 | Provisional | Alternative | Strong documentation and configurable factory connector, but materially heavier than the reference pack for the same nominal energy. |
| Okay | Ovonic 4S 6000 mAh 120C LiPo with XT60 | Research | Extended-Capacity Alternative | Provides additional nominal energy with competitive specific energy, but requires center-of-gravity, launch, landing, and cruise-power validation. |

## Candidate Comparison

| Attribute | Tattu G-Tech 5200 35C | Admiral 5000 40C | SMC HCL-HP 5200 80C | Ovonic 6000 120C |
|----------|------------------------|------------------|------------------------|-------------------|
| Nominal Voltage | 14.8 V | 14.8 V | 14.8 V | 14.8 V |
| Capacity | 5,200 mAh | 5,000 mAh | 5,200 mAh | 6,000 mAh |
| Nominal Energy | 76.96 Wh | 74.0 Wh | 76.96 Wh | 88.8 Wh |
| Published Weight | 436.5 g | 476 g | 517 g | 510 g |
| Calculated Specific Energy | ~176 Wh/kg | ~155 Wh/kg | ~149 Wh/kg | ~174 Wh/kg |
| Published Dimensions | 133 × 45 × 33.5 mm | 158 × 46 × 30 mm | 150 × 51 × 30 mm | 155 × 46 × 35 mm |
| Main Connector | XT60 | XT60 | Factory XT60 option | XT60 |
| Balance Connector | JST-XH-compatible | JST-XH | JST-XH | JST-XH |
| Documentation Confidence | High | High | High | Medium |
| MP-1 Assessment | Reference | Conventional alternative | Heavier high-power alternative | Extended-capacity research candidate |

## Engineering Requirements

| Requirement | Target |
|-------------|--------|
| Chemistry | Conventional LiPo, 4.20 V maximum per cell |
| Cell Count | 4S only |
| Nominal Voltage | 14.8 V |
| Fully Charged Voltage | 16.8 V |
| Construction | Soft pack; hardcase packs rejected |
| Reference Capacity | Approximately 5,200 mAh |
| Supported Evaluation Range | 5,000–6,000 mAh |
| Preferred Pack Weight | ≤450 g |
| Experimental Pack Weight Ceiling | Approximately 525 g, subject to flight validation |
| Main Connector | XT60 |
| Balance Connector | JST-XH |
| Continuous Current Capability | Must exceed the verified propulsion current with engineering margin |
| Mechanical Installation | Common battery tray, straps, and connector location |
| Hardware Changes During Swap | None permitted |
| Adapter Cables | Not permitted for normal operation |
| Charging | Balance charging with a LiPo-specific charge profile |
| Documentation | Published mass, dimensions, capacity, voltage, connector, and discharge specifications required |

## Rejected Battery Architectures

| Architecture | Status | Reason |
|--------------|--------|--------|
| 3S LiPo | Rejected | Does not match the selected 4S propulsion baseline. |
| 5S LiPo | Rejected | Exceeds the documented 3S–4S input range of the selected Hobbywing Skywalker 50A V2 and would require propulsion revalidation. |
| 4S Li-ion | Rejected for MP-1 | Not required for the MP-1 validation mission and adds pack-design, sourcing, and integration complexity. |
| Hardcase LiPo | Rejected | Adds unnecessary mass and volume for an aircraft application. |
| Packs requiring connector adapters | Rejected | Conflicts with the common, directly exchangeable battery interface requirement. |

## Procurement Recommendation

Purchase the following as the MP-1 reference flight battery:

> **Tattu G-Tech 4S 5200 mAh 35C soft-pack LiPo with XT60**

The Ovonic 4S 6000 mAh pack may be evaluated later as an extended-capacity option after the aircraft has completed baseline flight testing with the reference battery.

---

## Revision History

- Initial flight-servo evaluation completed.
- Brushless propulsion motor evaluation completed.
- Electronic speed controller evaluation completed.
- Procurement terminology standardized so rank, status, and design role are distinct fields.
- MP-1 battery architecture standardized on removable 4S soft-pack LiPo batteries.
- Tattu G-Tech 4S 5200 mAh 35C with XT60 selected as the provisional reference battery.
- Admiral 5000, SMC HCL-HP 5200, and Ovonic 6000 retained as alternatives with defined trade-offs.
- 3S, 5S, Li-ion, hardcase, and adapter-dependent battery configurations rejected for the MP-1 baseline.
- Flight controller evaluation pending.
