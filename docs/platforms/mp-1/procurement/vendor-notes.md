# MP-1 Vendor Notes

**Document ID:** MP1-PROC-VENDOR-NOTES  
**Revision:** 3  
**Status:** Draft  
**Author:** Project Meadowlark  
**Last Updated:** 2026-07-29  

## Purpose

This document records procurement-oriented vendor notes for the MP-1 initial-flight configuration.

It supplements:

```text
docs/platforms/mp-1/procurement/approved-components.md
docs/platforms/mp-1/procurement/procurement-matrix.md
```

This document does not replace manufacturer documentation, purchase records, incoming inspection records, interface definitions, or verification evidence.

The initial MP-1 configuration is governed by:

```text
docs/platforms/mp-1/requirements/initial-flight-requirements.md
docs/platforms/mp-1/edr/edr-0001-initial-flight-baseline.md
docs/platforms/mp-1/architecture/electrical-power-architecture.md
```

The initial build shall support manual takeoff, onboard waypoint navigation, return-to-launch, RC pilot takeover, manual landing, telemetry, and flight logging without requiring a companion computer or payload-power system.

---

# Procurement Practice

For each purchased component:

1. Confirm the exact manufacturer and model.
2. Confirm the hardware revision.
3. Confirm the advertised voltage and current ratings.
4. Confirm physical dimensions and mass.
5. Confirm connector type, gender, polarity, and pinout.
6. Confirm included cables and accessories.
7. Confirm firmware or programming compatibility.
8. Record the vendor, product page, order date, quantity, price, and order identifier.
9. Save a copy of the applicable manufacturer documentation.
10. Photograph the received component and packaging.
11. Record any discrepancy between the listing and received hardware.
12. Do not move a component from Provisional to Approved until integration and verification are complete.

Marketplace titles, reseller descriptions, and search-result snippets shall not override manufacturer documentation.

Where vendor listings conflict, the most conservative technically credible value shall be used until the exact received hardware is inspected.

---

# Initial Flight-Critical Procurement Boundary

The initial procurement baseline includes:

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

The following shall not be procured for the initial build unless a later approved decision changes the baseline:

- Companion computer
- Payload computer
- Payload battery
- Payload regulator
- Mission-equipment power distribution
- Redundant flight-controller power
- Redundant servo-power system
- Camera payload
- Experimental mission sensors
- Autonomous takeoff hardware
- Autonomous landing hardware

---

# Flight Control Servos

## Corona DS929MG

### Summary

The Corona DS929MG is the current MP-1 reference servo because it most closely matches the Flightory LARK baseline while remaining within the preferred mass and torque range.

### Procurement Requirements

Confirm before ordering:

- Exact model: DS929MG
- Digital operation
- Metal gears
- Operating voltage: 4.8–6.0 V
- Published mass near 12.5 g
- JR/Futaba-compatible three-wire connector
- Quantity sufficient for the intended control-surface layout
- No substitute plastic-gear variant
- No similarly named analog or high-voltage variant

### Vendor Risks

- Some listings omit the exact operating-current data.
- Stall current may not be published.
- Older stock or rebranded stock may use different packaging.
- Servo lead length may vary.
- Connector housing style may vary while remaining electrically compatible.
- Counterfeit or relabeled micro servos are possible on general marketplaces.

### Incoming Inspection

Record:

- Mass
- Case dimensions
- Connector type
- Wire order
- Lead length
- Centering behavior
- Direction of travel
- Gear play
- Current under no-load movement
- Current under controlled mechanical loading
- Temperature during repeated movement

### Verification Consequence

Because published stall current is incomplete, the selected servo-power architecture shall be accepted through loaded simultaneous-servo testing rather than an unsupported calculated stall-current total.

Procurement Rank: **Best**  
Status: **Provisional**  
Design Role: **Reference**

---

## Hitec HS-82MG

### Summary

The Hitec HS-82MG is the strongest well-documented alternative.

### Procurement Requirements

Confirm:

- Exact HS-82MG metal-gear model
- Operating voltage compatible with 5 V servo power
- Authentic Hitec packaging
- Published dimensions and mass
- Standard three-wire servo connector
- Included servo arms and mounting hardware

### Vendor Risks

- Heavier than the preferred MP-1 servo target
- Higher cost
- Listings may mix HS-82MG and HS-82MG+ nomenclature
- Hardware and packaging may differ by production period

Procurement Rank: **Better**  
Status: **Provisional**  
Design Role: **Alternative**

---

## EMAX ES08MD II

### Summary

The EMAX ES08MD II is a lower-cost alternative with incomplete electrical characterization.

### Procurement Requirements

Confirm:

- Exact ES08MD II model
- Digital operation
- Metal gears
- 4.8–6.0 V compatibility
- Connector and lead length
- Published mass and dimensions

### Vendor Risks

- Listings may confuse ES08MD, ES08MD II, and other ES08-series variants.
- Electrical specifications may be incomplete or inconsistent.
- Packaging and included hardware may vary.

Procurement Rank: **Okay**  
Status: **Provisional**  
Design Role: **Alternative**

---

# Brushless Propulsion Motors

## T-Motor F90 2806.5 1300KV

### Summary

The T-Motor F90 2806.5 1300KV is the MP-1 reference propulsion motor and the strongest documented match to the original Flightory design.

### Procurement Requirements

Confirm:

- Exact manufacturer: T-Motor
- Exact model: F90 2806.5
- Exact winding: 1300KV
- Current-production or verifiable new-old-stock condition
- Shaft condition
- Mounting-hole pattern
- Included screws
- Motor-wire length
- Connector condition
- Published mass near the expected value
- No higher-KV substitute

### Vendor Risks

- F90 product listings may include multiple KV variants.
- Some listings may be old or discontinued stock.
- Mounting screws may be too long for the motor windings.
- Motor-wire termination may differ.
- Resellers may omit complete test data.
- Marketplace listings may use photographs from a different KV version.

### Incoming Inspection

Record:

- Mass
- KV label
- Bell and bearing condition
- Shaft runout
- Phase resistance consistency
- Mounting-hole geometry
- Wire length and termination
- No-load current
- Rotation direction
- Vibration during low-power operation

### Verification Consequence

Static current shall be measured with the selected 4S battery, ESC, and final propeller before approving the power-module current path.

Procurement Rank: **Best**  
Status: **Provisional**  
Design Role: **Reference**

---

## EMAX ECO II 2807 1300KV

### Summary

The EMAX ECO II 2807 1300KV is the strongest value-oriented motor alternative.

### Procurement Requirements

Confirm:

- Exact 2807 size
- Exact 1300KV winding
- Mounting pattern
- Shaft geometry
- Included hardware
- Wire length and termination

### Vendor Risks

- The ECO II line includes many sizes and KV values.
- Product titles may truncate important variant information.
- Published fixed-wing performance evidence is weaker than for the reference motor.

Procurement Rank: **Better**  
Status: **Provisional**  
Design Role: **Alternative**

---

## FlyFishRC Flash 2806.5 1350KV

### Summary

The FlyFishRC Flash 2806.5 1350KV is a mechanically plausible alternative with less fixed-wing evidence.

### Procurement Requirements

Confirm:

- Exact 2806.5 size
- Exact 1350KV winding
- Mounting-hole pattern
- Shaft and propeller attachment
- Included hardware
- Wire length and termination

### Vendor Risks

- Product listings may emphasize multirotor use.
- Fixed-wing propeller data may be limited.
- Similar model names may exist across production revisions.

Procurement Rank: **Okay**  
Status: **Provisional**  
Design Role: **Alternative**

---

# Electronic Speed Controllers

## Hobbywing Skywalker 50A V2

### Summary

The Hobbywing Skywalker 50A V2 is the MP-1 reference ESC.

It is selected for its fixed-wing firmware, 4S compatibility, current margin, 5 V/5 A switching BEC, and strong manufacturer documentation.

### Procurement Requirements

Confirm:

- Exact model: Skywalker 50A V2
- Fixed-wing product, not a surface or multirotor ESC
- 3S–4S LiPo compatibility
- 50 A continuous rating
- 70 A peak rating
- Integrated 5 V/5 A switching BEC
- Standard PWM throttle input
- Included motor and battery leads
- Connector type supplied by the vendor
- Programming instructions
- Current-production packaging where possible

### Vendor Risks

- Listings may mix V1 and V2 hardware.
- Connector installation may vary by vendor.
- Some units may be sold without battery or motor connectors.
- The supplied battery connector may not be XT60.
- Product images may show a different current rating.
- Resellers may omit the firmware-feature distinction.

### Incoming Inspection

Record:

- Exact label and revision
- Mass
- Battery-wire gauge
- Battery-wire length
- Motor-wire gauge and length
- Installed connector type
- Servo lead wire order
- BEC output voltage
- Programming response
- Motor startup behavior
- Brake behavior
- Temperature during static propulsion testing

### Servo-Power Role

The integrated 5 V/5 A BEC is the baseline MP-1 servo-power source.

It shall not be treated as Approved until loaded testing confirms:

- Stable servo-rail voltage
- No flight-controller reset
- No receiver reset
- No unacceptable jitter
- Acceptable temperature
- Acceptable performance during rapid throttle changes

Procurement Rank: **Best**  
Status: **Provisional**  
Design Role: **Reference**

---

## Hobbywing Skywalker 40A V2

### Summary

The Skywalker 40A V2 is the strongest direct ESC alternative.

### Procurement Requirements

Confirm:

- Exact 40A V2 model
- 3S–4S compatibility
- Integrated 5 V/5 A switching BEC
- Fixed-wing programming support
- Connector configuration

### Vendor Risks

- Same physical appearance as the 50A model
- Reduced propulsion-current margin
- Listings may confuse the 40A and 50A variants

Procurement Rank: **Better**  
Status: **Provisional**  
Design Role: **Alternative**

---

## ZTW Beatles 40A

### Summary

The ZTW Beatles 40A is a credible lower-margin fixed-wing ESC alternative.

### Procurement Requirements

Confirm:

- Exact 40A model
- 4S compatibility
- 5 V/3 A BEC
- PWM control
- Brake and cutoff programming
- Connector configuration

### Vendor Risks

- Product revisions may differ.
- Documentation may be less complete than Hobbywing.
- The smaller BEC provides less servo-power margin.
- Burst-current capability is lower.

Procurement Rank: **Okay**  
Status: **Provisional**  
Design Role: **Alternative**

---

## T-Motor AT40A

### Summary

The T-Motor AT40A remains under research.

### Procurement Hold

Do not procure until the following are confirmed from authoritative documentation:

- Exact battery-voltage range
- Continuous and peak current
- BEC voltage and current
- Programming features
- Weight
- Dimensions
- Connector configuration
- Current lifecycle status

Procurement Rank: **Okay**  
Status: **Research**  
Design Role: **Alternative**

---

# Servo-Power Contingency

## Hobbywing UBEC 5A

### Summary

The Hobbywing UBEC 5A is the retained contingency if the Skywalker integrated BEC fails verification or later flight-critical loads exceed the baseline margin.

### Procurement Position

Do not procure for the initial build unless bench testing or a later approved requirement justifies it.

### Required Configuration

If introduced:

- Set output to 5.0 V
- Isolate the ESC BEC positive lead
- Retain ESC throttle signal and ground
- Connect only one positive BEC source to the servo rail
- Verify reverse-current and backfeed behavior
- Document the revised wiring architecture

### Vendor Risks

- Listings may show older or different UBEC versions.
- Output-voltage jumper or switch arrangements may vary.
- Similar 10 A or surface-vehicle products may be listed nearby.
- Some products use output voltages unsuitable for the current servo baseline.

Procurement Rank: **Better**  
Status: **Future Evaluation**  
Design Role: **Contingency Alternative**

---

# Main Flight Batteries

## Battery Procurement Rules

All routine MP-1 flight batteries shall:

- Be 4S conventional LiPo
- Be soft-pack construction
- Use XT60 as the main connector
- Use JST-XH-compatible balance connection
- Fit the common battery tray
- Use the common restraint system
- Require no adapter cable
- Remain within the defined mass envelope
- Include published dimensions and mass
- Be balance-charged with an approved LiPo profile

Record a unique battery identifier for each pack.

For each received battery, record:

- Manufacturer
- Model
- Capacity
- Cell count
- Connector
- Balance connector
- Mass
- Dimensions
- Initial cell voltages
- Internal resistance, if the charger supports measurement
- Purchase date
- Cycle count
- Storage condition
- Retirement reason

---

## Tattu G-Tech 4S 5200 mAh 35C with XT60

### Summary

This is the MP-1 reference battery.

### Procurement Requirements

Confirm:

- 4S
- 5200 mAh
- 35C
- Soft-pack construction
- Factory XT60
- JST-XH-compatible balance lead
- Published mass near 436.5 g
- Published dimensions near 133 × 45 × 33.5 mm

### Vendor Risks

- Availability may vary.
- G-Tech product listings may include smart-identification features that do not affect aircraft compatibility.
- Connector options may vary.
- Product dimensions or mass may change with revision.

Procurement Rank: **Best**  
Status: **Provisional**  
Design Role: **Reference**

Recommendation:

> Use the Tattu G-Tech 4S 5200 mAh 35C soft-pack LiPo with XT60 as the MP-1 reference flight battery.

---

## Admiral 4S 5000 mAh 40C with XT60

### Summary

This is the strongest conventional battery alternative.

### Vendor Risks

- Heavier and longer than the reference pack
- Slightly lower nominal energy
- Retailer-specific availability

Procurement Rank: **Better**  
Status: **Provisional**  
Design Role: **Alternative**

---

## SMC HCL-HP 4S 5200 mAh 80C with Factory XT60

### Summary

This is a well-documented but heavy alternative.

### Procurement Requirements

Order only with a factory XT60.

### Vendor Risks

- Connector must be selected correctly at order time.
- Mass is substantially higher than the reference pack.
- High advertised C-rating provides little benefit to the MP-1 mission.

Procurement Rank: **Okay**  
Status: **Provisional**  
Design Role: **Alternative**

---

## Ovonic 4S 6000 mAh 120C with XT60

### Summary

This is an extended-capacity research candidate.

### Procurement Hold

Do not treat as a routine flight battery until the aircraft has completed baseline testing with the reference pack.

### Additional Verification

Required:

- Battery-bay fit
- Center of gravity
- Restraint
- Launch handling
- Climb performance
- Cruise current
- Landing speed and energy
- Endurance
- Thermal behavior

Procurement Rank: **Okay**  
Status: **Research**  
Design Role: **Extended-Capacity Alternative**

---

# Flight Controllers

## Holybro Pixhawk 6C Mini

### Summary

The Holybro Pixhawk 6C Mini is the MP-1 reference flight controller.

It supports onboard ArduPlane waypoint mission execution and does not require a companion computer for the initial autonomous-flight objective.

### Procurement Requirements

Confirm:

- Exact product: Pixhawk 6C Mini
- Current hardware revision
- STM32H743 processor
- Included cable set
- Included power cable
- Included GPS cables, if any
- Included telemetry cables, if any
- Included microSD card, if any
- Mounting hardware
- Published dimensions
- Published mass
- Connector layout
- Analog power-input compatibility
- Current-production status
- ArduPlane support for the exact board target

### Vendor Risks

- Holybro documentation may describe more than one physical revision.
- Dimensions and mass may differ by revision.
- Accessory bundles may vary.
- Some listings may show the full-size Pixhawk 6C rather than the Mini.
- Some bundles may include a digital power module intended for a different controller.
- Cables shown in photographs may not be included.

### Incoming Inspection

Record:

- Exact model
- Hardware revision
- Serial number
- Mass
- Dimensions
- Connector labels
- Included harnesses
- microSD presence
- Boot behavior
- Firmware target
- Detected IMUs
- Detected barometer
- PWM output operation
- Power-input behavior
- Logging behavior

### Initial Autonomous Role

The Pixhawk 6C Mini shall provide:

- Mission storage
- Waypoint sequencing
- GPS-guided navigation
- Return-to-launch
- Flight-mode control
- RC pilot takeover
- Failsafe logic
- Flight logging

A companion computer shall not be procured for the initial configuration.

Procurement Rank: **Best**  
Status: **Provisional**  
Design Role: **Reference**

---

## CubePilot Cube Orange+ with Mini Carrier Board

### Summary

This is the strongest premium redundancy alternative.

### Procurement Requirements

The exact carrier board shall be part of the purchase decision.

Confirm:

- Authentic Cube Orange+
- Exact Mini Carrier Board
- Included cables
- Power-input architecture
- PWM output availability
- Mounting hardware
- Accessory set

### Vendor Risks

- Counterfeit Cube hardware is a known general procurement concern.
- Carrier-board details materially affect the interface architecture.
- Bundles may omit required cables.
- Cost and installed volume are higher.

Procurement Rank: **Better**  
Status: **Provisional**  
Design Role: **Premium Alternative**

---

## Matek H743-WING V3

### Summary

This is the strongest integrated fixed-wing alternative.

### Vendor Risks

- Board revisions may change pad layouts or ratings.
- Integration requires soldering.
- Replacement may require harness reconstruction.
- More functions are concentrated on one board.
- Documentation must match the exact V3 revision.

Procurement Rank: **Better**  
Status: **Provisional**  
Design Role: **Integrated Alternative**

---

## Holybro Pixhawk 6X with Mini Baseboard

### Summary

This is a technically strong but excessive premium alternative for MP-1.

### Vendor Risks

- Higher cost
- Higher mass
- Larger installed volume
- Digital power-module requirements
- Accessory bundle variability

Procurement Rank: **Okay**  
Status: **Provisional**  
Design Role: **Premium Alternative**

---

## SpeedyBee F405 Wing

### Summary

This controller is not approved for the MP-1 reference role.

### Reason for Rejection

The processor, memory limitations, reduced redundancy, and firmware-feature constraints do not meet the durable autonomous-flight reference-platform objective.

Procurement Rank: **Okay**  
Status: **Rejected**  
Design Role: **Alternative**

---

# Flight-Controller Power Modules

## Holybro PM02 V3

### Summary

The Holybro PM02 V3 is the leading power-module candidate for the Pixhawk 6C Mini.

It offers the cleanest physical and electrical integration for the minimal initial-flight architecture.

### Procurement Hold

Do not procure until the complete stock current path is reconciled with measured propulsion current.

The evaluation shall distinguish between:

- Current-sensor measurement range
- PCB current capability
- Connector current capability
- Wire current capability
- Sustained operating current
- Short-duration takeoff and climb current

### Procurement Requirements

Confirm:

- Exact PM02 V3 model
- Analog output
- Pixhawk 6C Mini compatibility
- Included six-pin JST-GH harness
- XT60 connector orientation
- Wire gauge
- Wire length
- Board dimensions
- Installed mass
- Voltage range
- Current-sensor range
- Published calibration values
- Current production status

### Vendor Risks

- Listings may confuse PM02, PM02 V3, and PM02D.
- Digital PM02D hardware is not suitable for the Pixhawk 6C Mini analog input.
- Product pages may emphasize PCB current rating while the stock harness has a lower practical continuous rating.
- Connector gender and cable orientation may be unclear.
- Accessory cable inclusion may vary.

### Incoming Inspection

Record:

- Exact label and revision
- Connector gender
- Wire gauge
- Wire length
- Harness pinout
- Mass
- Dimensions
- Output voltage
- Voltage-sense calibration
- Current-sense calibration
- Voltage drop under load
- Connector and wire temperature under load

Procurement Rank: **Best**  
Status: **Research**  
Design Role: **Reference**

---

## Holybro PM06 V2

### Summary

The PM06 V2 is a technically compatible alternative with integrated power distribution.

### Procurement Concern

Its distribution features are unnecessary for the single-motor initial MP-1 architecture and add hardware beyond the baseline need.

### Vendor Risks

- Listings may confuse PM06 V2 and PM06D.
- The complete stock current path still requires verification.
- Distribution outputs may encourage unnecessary wiring complexity.

Procurement Rank: **Better**  
Status: **Research**  
Design Role: **Alternative**

---

## Holybro PM07

### Summary

The PM07 is capable but oversized for MP-1.

### Procurement Concern

It adds distribution and PWM-header functions that are not needed for the minimal initial configuration.

Procurement Rank: **Okay**  
Status: **Research**  
Design Role: **Alternative**

---

## Mauch 100 A Hall-Effect System

### Summary

The Mauch system is retained as a premium higher-current alternative.

### Procurement Concern

It requires:

- Separate regulator selection
- Connector installation
- Harness adaptation
- Calibration
- Greater installation effort
- More detailed interface documentation

Procurement Rank: **Okay**  
Status: **Future Evaluation**  
Design Role: **Premium Alternative**

---

## Holybro PM02D and PM06D

### Reason for Rejection

These digital power modules are intended for a different flight-controller power-interface architecture and are not the correct baseline for the Pixhawk 6C Mini analog input.

Procurement Rank: **Okay**  
Status: **Rejected**  
Design Role: **Alternative**

---

# GPS and Compass

## Procurement Role

GPS and compass are flight-critical for:

- Home-position establishment
- Waypoint navigation
- Return-to-launch
- Geofence operation
- Navigation logging

### Evaluation Requirements

The selected unit shall have:

- Current ArduPlane support
- Direct Pixhawk 6C Mini compatibility
- Documented GPS and compass interfaces
- Appropriate update rate
- Adequate cable length
- Keyed connectors where practical
- Suitable mounting provisions
- Adequate electromagnetic separation from propulsion wiring
- Current-production availability

### Vendor Risks

- Similar enclosures may contain different GNSS modules.
- Compass inclusion may vary.
- Connector type may vary by bundle.
- Cable length may vary.
- Some products may require CAN rather than serial integration.
- Product revisions may change internal GNSS receivers.

Status: **Evaluation Pending**

---

# RC Receiver

## Procurement Role

The RC receiver is flight-critical for:

- Manual control
- Stabilized control
- Flight-mode selection
- Pilot takeover
- Link-loss failsafe

### Evaluation Requirements

The selected receiver shall have:

- Direct Pixhawk-compatible signal protocol
- Documented voltage range
- Documented failsafe behavior
- Adequate range
- Antenna diversity where appropriate
- Suitable telemetry behavior
- No dependence on the ground telemetry radio
- Current-production support

### Vendor Risks

- Regional frequency variants may differ.
- Binding compatibility depends on the transmitter ecosystem.
- Firmware versions may change protocol support.
- Failsafe behavior may require receiver-specific configuration.
- Connector pinout may not match Pixhawk harnesses directly.

Status: **Evaluation Pending**

---

# Telemetry Radio

## Procurement Role

Telemetry supports:

- Mission upload
- Parameter review
- Ground monitoring
- Flight status
- Battery status
- Test observation

Telemetry is not required for the flight controller to continue an already loaded onboard mission.

### Evaluation Requirements

Confirm:

- Frequency band legal for the operating region
- Pixhawk-compatible serial interface
- Air and ground radio pair
- Antennas
- Power requirements
- Connector type
- Cable inclusion
- Ground-station compatibility
- Expected operating range
- Current-production status

### Vendor Risks

- Regional frequency restrictions apply.
- Air and ground units may be sold separately.
- Antennas may be omitted.
- Firmware compatibility may vary.
- Connector pinouts may vary by vendor or revision.

Status: **Evaluation Pending**

---

# Propeller

## Procurement Role

The propeller completes the propulsion load and determines the actual motor, ESC, battery, and power-module current requirement.

### Procurement Requirements

Confirm:

- Diameter
- Pitch
- Hub thickness
- Shaft or adapter compatibility
- Rotation direction
- Material
- Balance quality
- Manufacturer limits
- Suitability for the selected motor and 4S battery

### Vendor Risks

- Nominal size may not reflect actual geometry.
- Propeller direction may be mislabeled.
- Hub bore and adapter requirements may vary.
- Different materials can produce materially different current.
- Folding and fixed propellers are not interchangeable without additional hardware.

### Verification Consequence

No power-module current-path decision shall be finalized until static current is measured with the selected propeller.

Status: **Evaluation Pending**

---

# Airspeed Sensor

## Procurement Position

An airspeed sensor shall be procured only if required by the initial flight-test plan or by the selected autonomous-flight configuration.

It is not automatically required merely because the flight controller supports it.

### Evaluation Requirements

If selected, confirm:

- ArduPlane support
- Pixhawk interface
- Voltage range
- Sensor range
- Pitot-tube compatibility
- Tubing
- Mounting location
- Calibration procedure
- Moisture and blockage considerations

Status: **Pending Test-Plan Decision**

---

# Deferred Equipment

## Companion Computer

Status: **Future Evaluation**

Do not procure for the initial MP-1 build.

ArduPlane onboard mission execution is sufficient for the initial waypoint-navigation requirement.

## Payload Battery

Status: **Future Evaluation**

Do not procure for the initial build.

## Payload Regulator

Status: **Future Evaluation**

Do not procure for the initial build.

## Mission-Equipment Power Distribution

Status: **Future Evaluation**

Do not procure for the initial build.

## Redundant Flight-Controller Power

Status: **Future Evaluation**

Do not procure for the initial build.

## Redundant Servo Power

Status: **Future Evaluation**

Do not procure for the initial build.

## Camera and Experimental Payload Sensors

Status: **Future Evaluation**

Do not procure for the initial build.

---

# Required Purchase Record

For each procurement transaction, record:

| Field | Required Entry |
|------|----------------|
| Component Category | Servo, motor, ESC, battery, flight controller, power module, GPS, receiver, telemetry, propeller, or sensor |
| Manufacturer | Exact legal or marketed manufacturer name |
| Model | Exact model and variant |
| Hardware Revision | If identified |
| Vendor | Seller or distributor |
| Product Page | Archived reference or recorded URL |
| Quantity | Number ordered |
| Unit Price | Price at purchase |
| Shipping and Tax | Recorded separately where practical |
| Order Date | Date ordered |
| Order Identifier | Vendor order number |
| Expected Delivery | Date or range |
| Received Date | Actual receipt date |
| Condition | New, used, or new-old stock |
| Included Accessories | Cables, connectors, mounts, antennas, manuals |
| Discrepancies | Any mismatch from listing |
| Incoming Inspection Record | Repository path or identifier |
| Verification Record | Repository path or identifier |
| Final Status | Provisional, Approved, Rejected, or returned |

---

# Initial Procurement Order

The remaining initial-flight evaluations and purchases shall proceed in this order:

1. Flight-controller power module
2. GPS and compass
3. RC receiver
4. Telemetry radio
5. Propeller
6. Airspeed sensor, only if required by the test plan

Companion-computer and payload-system procurement shall not be added to this sequence without a new approved decision.

---

# Revision History

## Revision 3

- Aligned vendor notes with EDR-0001 and the initial-flight requirements.
- Defined the minimal flight-critical procurement boundary.
- Removed companion-computer procurement from the initial build.
- Removed payload power and redundant avionics power from the initial build.
- Established the Skywalker integrated BEC as the baseline servo-power source subject to verification.
- Retained the Hobbywing UBEC 5A only as a contingency.
- Added detailed power-module vendor risks and procurement holds.
- Added GPS/compass, RC receiver, telemetry, propeller, and airspeed-sensor procurement guidance.
- Added required purchase-record fields.
- Updated the remaining procurement order.

## Revision 2

- Added flight-controller vendor assessments.
- Selected the Holybro Pixhawk 6C Mini as the reference controller.
- Added integration and incoming-inspection notes for controller alternatives.

## Revision 1

- Added battery vendor assessments.
- Selected the Tattu G-Tech 4S 5200 mAh battery as the reference.
- Added battery procurement and inspection rules.

## Revision 0

- Initial servo, motor, and ESC vendor notes established.
