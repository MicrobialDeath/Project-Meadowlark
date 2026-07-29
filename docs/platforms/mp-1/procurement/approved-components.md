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
| Premium Alternative | Higher-cost candidate offering additional redundancy, power-input resilience, or expansion capability. |
| Integrated Alternative | Fixed-wing-oriented candidate that consolidates power distribution and servo power at the cost of reduced modularity. |

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

# Flight Controllers

## Flight Controller Architecture Decision

MP-1 requires an H7-class flight controller with full ArduPlane support, redundant inertial sensing, removable logging media, sufficient serial and CAN interfaces, and conventional PWM servo outputs.

The selected flight controller must support:

- Autonomous fixed-wing operation using ArduPlane
- At least eight PWM outputs
- At least four usable serial interfaces when dedicated GPS and receiver ports are included
- At least one CAN bus, with two preferred
- External GPS and compass integration
- Airspeed sensor integration through I²C or CAN
- Voltage and current monitoring through a compatible power module
- Receiver input through S.Bus and/or a UART-based protocol
- Telemetry radio integration
- MAVLink connection to a future companion computer
- Replaceable, documented cable harnesses
- A removable microSD card or equivalent high-capacity flight logging

## Flight Controller Candidates

| Rank | Component | Status | Design Role | Notes |
|------|-----------|--------|-------------|-------|
| Best | Holybro Pixhawk 6C Mini | Provisional | Reference | Best balance of H7 processing, redundant and temperature-controlled IMUs, 14 PWM outputs, dual CAN, dual GPS interfaces, compact packaging, and standardized Pixhawk connectors. |
| Better | CubePilot Cube Orange+ with Mini Carrier Board | Provisional | Premium Alternative | Triple IMUs, dual barometers, mature ArduPilot ecosystem, modular carrier architecture, and strong redundancy, but higher cost and integration complexity. |
| Better | Matek H743-WING V3 | Provisional | Integrated Alternative | Fixed-wing-specific H7 board with integrated voltage/current sensing, servo BEC, peripheral BEC, seven UARTs, thirteen PWM outputs, and CAN, but with less sensor redundancy and more solder-dependent integration. |
| Okay | Holybro Pixhawk 6X with Mini Baseboard | Provisional | Premium Alternative | Excellent processing, triple sensor redundancy, Ethernet, dual CAN, dual GPS, and dual power inputs, but larger, heavier, and more capable than MP-1 currently requires. |
| Okay | SpeedyBee F405 Wing | Rejected | Alternative | Attractive fixed-wing integration and cost, but the F405 processor and firmware-feature limitations do not meet the MP-1 reference-platform objective. |

## Candidate Comparison

| Attribute | Pixhawk 6C Mini | Cube Orange+ with Mini Carrier | Matek H743-WING V3 | Pixhawk 6X with Mini Baseboard |
|----------|------------------|-------------------------------|----------------------|----------------------------------|
| Processor | STM32H743 | STM32H757 | STM32H743 | STM32H753 |
| IMUs | 2 | 3 | 2 | 3 |
| Barometers | 1 | 2 | 1 | 2 |
| Temperature-Controlled Sensors | Yes | Yes | No documented active temperature control | Yes |
| PWM Outputs | 14 | Up to 14 | 13 | 16 |
| General Serial Interfaces | 2 general-purpose plus dedicated GPS/RC interfaces | 5 general-purpose | 7 UARTs | 4 general-purpose plus dedicated GPS/RC interfaces |
| CAN | 2 | 2 | 1 | 2 |
| GPS Interfaces | 2 | Carrier-dependent; multiple serial/I²C options | UART/I²C through board interfaces | 2 |
| Power Inputs | 1 analog power input | Carrier-dependent; mini carrier backup from servo rail | Direct 9–36 V input with integrated sensing | 2 SMBus power inputs |
| Servo Power | External servo rail supply required | Carrier-dependent external servo rail supply | Integrated selectable 5/6/7.2 V servo BEC | External servo rail supply required |
| Current Monitoring | External compatible power module | External compatible power module | Integrated 132 A current sensor | External SMBus-compatible power module |
| Logging | microSD | microSD | microSD | microSD |
| Ethernet | No | No | No | Yes |
| Wiring Style | JST-GH plus integrated PWM headers | Carrier-board connectors and PWM headers | Mixed connectors and solder pads | JST-GH/baseboard connectors and PWM headers |
| Primary Strength | Best overall balance | Highest mature redundancy | Clean fixed-wing integration | Maximum expansion capability |
| Primary Trade-off | Single primary power input and fewer general ports than full-size Pixhawk | Cost, size, and carrier-board complexity | Reduced modularity and more soldering | Cost, size, mass, and unnecessary capability |

## Engineering Requirements

| Requirement | Target |
|-------------|--------|
| Firmware | Full ArduPlane support |
| Processor | STM32H7 class |
| PWM Outputs | ≥8 required; ≥12 preferred |
| IMU Redundancy | At least two IMUs preferred |
| Barometer | At least one; redundant barometers desirable |
| Serial Connectivity | Sufficient for GPS, receiver, telemetry, companion computer, and expansion |
| CAN | At least one; two preferred |
| GPS/Compass | Dedicated or clearly documented integration path |
| Airspeed Sensor | I²C or CAN support |
| Receiver Support | S.Bus and UART-based receiver support |
| Power Monitoring | Voltage and current sensing required |
| Servo Power | Defined independently from flight-controller logic power |
| Logging | Removable microSD preferred |
| Companion Computer | MAVLink serial required; Ethernet desirable but not required |
| Connector System | Keyed, documented, replaceable harnesses preferred |
| Mechanical Installation | Must fit the LARK avionics area with suitable vibration isolation and service access |
| Lifecycle | Current production hardware |
| Documentation | Manufacturer and ArduPilot documentation required |

## Procurement Recommendation

Purchase the following as the MP-1 reference flight controller:

> **Holybro Pixhawk 6C Mini**

The exact hardware revision or model variant must be confirmed at purchase because current Holybro documentation lists multiple physical revisions with different dimensions and mass.

The Cube Orange+ with Mini Carrier Board should remain the premium redundancy alternative. The Matek H743-WING V3 should remain the integrated fixed-wing alternative where reduced wiring and integrated power functions outweigh modularity and sensor-redundancy priorities.

The Pixhawk 6X with Mini Baseboard is technically acceptable but should be deferred to a future platform requiring Ethernet, dual primary power inputs, or greater sensor redundancy.

The physical and electrical interface matrix will be created after the complete MP-1 procurement set is selected.

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
- Holybro Pixhawk 6C Mini selected as the provisional reference flight controller.
- Cube Orange+, Matek H743-WING V3, and Pixhawk 6X retained as ranked alternatives.
- SpeedyBee F405 Wing rejected for the MP-1 reference role.
- Power module / external BEC evaluation pending.
