# MP-1 Components

**Status:** Active — procurement and integration

## Purpose

This document is the authoritative hardware-selection and procurement-status record for Meadowlark Platform 1 (MP-1).

Design intent is documented in `design.md`.

Assembly procedures belong in `build.md`.

Verification procedures belong in `testing.md`, with actual verification evidence stored under `evidence/`.

---

# Component Lifecycle

MP-1 uses the following component lifecycle:

1. **Selected** — chosen for the MP-1 baseline, but not yet ordered.
2. **Ordered** — purchase confirmed; component not yet physically received and verified.
3. **Received** — component physically received and inspected for identity and condition.
4. **Verified** — component has passed the applicable integration and test requirements.

A purchase does not constitute verification.

---

# Component Status

| Category | Selected Component | Qty | Status |
|---|---|---:|---|
| Airframe | Flightory LARK | 1 | In fabrication |
| Flight Controller | Holybro Pixhawk 6C Mini | 1 | Received |
| Flight-Controller Power Module | Holybro PM02 V3 | 1 | Received |
| GPS / Compass | Holybro M10 GPS Module Standard (SKU 12040) | 1 | Received |
| Battery | Spektrum SPMX54S50H5 Smart G2 LiPo, 5000 mAh 4S 50C IC5 | 1 | Received |
| Motor | T-Motor F90 2806.5 1300KV | 1 | Received |
| ESC | Hobbywing Skywalker 50A V2 | 1 | Received |
| Servos | EMAX ES3059MD 12 g Digital Metal Gear | 4 received / 3 planned for installation | Received |
| RC Receiver | RadioMaster RP4TD ExpressLRS 2.4 GHz | 1 | Received |
| Propeller | HQProp 7×4.5 2-blade | 1 set / 4 props | Received |
| Telemetry Radio | Holybro SiK Telemetry Radio V3, 915 MHz | 1 air/ground system | Received |
| Remote ID | Ruko R111S Broadcast Remote ID Module | 1 | Received |
| RC Transmitter | RadioMaster TX16S MK3 ELRS | 1 | Received |
| RC Transmitter Battery | RadioMaster 21700 5000 mAh 2S Li-ion Battery | 1 | Received |

---

# Selected Components

## Airframe

**Selected:** Flightory LARK

**Status:** In fabrication

Reason:

- Proven fixed-wing reference platform
- Modular construction
- Appropriate for the MP-1 baseline objective

The LARK is a third-party design and its proprietary design files are not redistributed by Project Meadowlark.

---

## Flight Controller

**Selected:** Holybro Pixhawk 6C Mini

**Status:** Received

Reason:

- Mature ArduPlane support
- Suitable fixed-wing navigation and autonomous-flight capability
- Well-documented Pixhawk ecosystem

Verification remains required after installation and configuration.

---

## Flight-Controller Power Module

**Selected:** Holybro PM02 V3

**Status:** Received

Role:

- Powers the Pixhawk flight-controller domain
- Provides flight-battery voltage/current measurement

The servo rail remains powered separately by the electronic speed controller (ESC) battery eliminator circuit (BEC).

---

## GPS / Compass

**Selected:** Holybro M10 GPS Module Standard

**SKU:** 12040

**Status:** Received

Procurement note:

- The originally ordered Holybro M10 GPS V2 Standard (SKU 12086) became unavailable with an estimated four-week delay.
- The supplier offered the in-stock Holybro M10 GPS Module Standard (SKU 12040) as a replacement.
- The substitution was accepted for MP-1.

Role:

- Global Navigation Satellite System (GNSS) position
- Navigation timing
- Heading/navigation support as provided by the selected module and final integration

Final mounting location and interference verification remain required.

---

## Flight Battery

**Selected:** Spektrum SPMX54S50H5 Smart G2 LiPo

**Status:** Received

Baseline specifications:

- 5000 mAh
- 4S
- 14.8 V nominal
- 50C
- IC5 connector
- Spektrum Smart G2 battery integration
- G2 balance-data communication through the Smart connector; no separate external balance lead is required for charging

Procurement:

- Source: Summit Racing
- Quantity: 1
- Ordered: September 4, 2026
- Received: September 6, 2026
- Final product, handling, tax, and delivered total should be recorded only when confirmed from the completed order record

Charging:

- Intended charger: Spektrum S2100 Smart Charger, model SPMXC1010
- S2100 charger firmware updated to OS 1.1.0.17 on September 4, 2026
- The updated S2100 supports charging and balancing Spektrum Smart G2 batteries
- The existing Smart IC5-to-IC3 adapter remains part of the charging path
- Battery was recognized normally by the S2100 after receipt
- Initial charge completed successfully to full charge on September 6, 2026

Replacement note:

- The previous MP-1 baseline battery was the Spektrum SPMX50004S50H5 Smart G1 LiPo, 5000 mAh 4S 50C IC5.
- The original battery and a same-model replacement both failed bench acceptance because the S2100 did not recognize them as connected batteries.
- The SPMX50004S50H5 is therefore removed from the MP-1 baseline and replaced by the current SPMX54S50H5 Smart G2 battery.

**Evaluated alternative:** Tattu G-Tech 5200 mAh 4S 35C XT60

The Tattu remains a technically suitable lighter alternative but is no longer the selected MP-1 baseline battery.

Receipt/charging checks completed:

- Exact SPMX54S50H5 model received
- Smart G2 recognition by the S2100 confirmed
- Successful charge and balance operation on the S2100 confirmed
- Battery fully charged and available for MP-1 electrical integration testing

Verification remaining:

- Physical dimensions and fit
- Aircraft connector integration
- Battery mass
- Center-of-gravity effect
- Voltage under load
- Capacity/condition under operational use

---

## Motor

**Selected:** T-Motor F90 2806.5 Long Range Motor

**Variant:** 1300KV

**Status:** Received

Procurement:

- Quantity: 1
- Product cost: $29.90
- Shipping: $6.90
- Tax: $0.00
- Total paid: $36.80

Selection criteria:

- 4S compatibility
- Suitable performance for the LARK/MP-1 propulsion architecture
- Efficient fixed-wing operation

Verification required:

- Confirm exact 1300KV variant
- Mounting fit
- Rotation direction
- Propeller compatibility
- Static current
- Temperature
- Vibration
- Throttle response

---

## Electronic Speed Controller

**Selected:** Hobbywing Skywalker 50A V2

**Status:** Received

Procurement source: Amazon

Known purchase price:

- Product: $26.80

Baseline characteristics:

- 50 A electronic speed controller (ESC)
- Fixed-wing application
- Integrated 5 V / 5 A battery eliminator circuit (BEC) for the servo rail

Verification required:

- Confirm exact received model
- Connector/polarity inspection
- BEC output voltage
- Servo-load performance
- Motor operation
- Temperature
- Full-throttle current margin

---

## Servos

**Selected:** EMAX ES3059MD 12 g Digital Metal Gear Servo

**Status:** Received

Configuration:

- Quantity received: 4
- Quantity planned for aircraft: 3
- Spare: 1

Procurement:

- Merchandise: $27.96
- Shipping: $8.99
- Estimated tax: $2.96
- Total paid: $39.91

Selection criteria:

- Digital control
- Metal-gear construction
- Approximately 12 g class
- Suitable torque and speed for the LARK control surfaces
- 4.8–6.0 V-class servo operation
- Suitable physical envelope for the LARK installation

**Original Flightory reference:** Corona DS929MG

The Corona DS929MG is retained only as the original reference/comparison servo and is no longer the selected MP-1 servo.

Verification required before flight:

- Exact model inspection
- Dimensions and mounting fit
- Connector type and polarity
- Centering
- Direction and travel
- Gear play
- Current draw
- Simultaneous three-servo load
- Servo-rail voltage stability
- Temperature under load

---

## RC Receiver

**Selected:** RadioMaster RP4TD ExpressLRS 2.4 GHz Receiver with Antennas

**Status:** Received

GetFPV:

- SKU: 21602
- Quantity: 1
- Product cost: $32.49

Role:

- Aircraft-side manual radio-control receiver
- Interfaces the pilot-control link with the Pixhawk
- Pairs with the selected RadioMaster TX16S MK3 ELRS transmitter for the MP-1 pilot-control link

Verification required:

- Receiver identity and condition
- Antenna installation
- Pixhawk interface
- Binding
- Channel mapping
- Failsafe behavior
- Link-quality testing

---

## Propeller

**Selected:** HQProp 7×4.5 2-Blade Propeller

**Status:** Received

GetFPV:

- SKU: 17871
- Quantity purchased: 1 set
- Set quantity: 4 propellers
- Product cost: $5.49

This is the initial MP-1 test propeller, not a permanently approved propulsion configuration.

Verification required:

- Hub/motor compatibility
- Correct orientation
- Balance and condition
- Static current
- Thrust behavior
- Motor and ESC temperature
- Vibration

Do not approve the propulsion combination until bench testing is complete.

---

## Telemetry Radio

**Selected:** Holybro SiK Telemetry Radio V3

**Frequency:** 915 MHz United States configuration

**Status:** Received

Role:

- MAVLink data connection between Pixhawk and ground station
- Mission/configuration support
- Live aircraft status and telemetry

Telemetry is not the primary manual flight-control link.

Verification required:

- Confirm air/ground radio pair identity and condition
- Confirm 915 MHz configuration
- Aircraft-side Pixhawk interface
- Ground-station connectivity
- MAVLink communication
- Link-quality/range testing
- Expected aircraft behavior when telemetry is lost

---

## Remote ID

**Selected:** Ruko R111S Broadcast Remote ID Module

**Status:** Received

Procurement source: Amazon

Role:

- Provides the standalone Broadcast Remote Identification (Remote ID) capability selected for MP-1 United States compliance
- Operates independently of the Pixhawk flight-control system
- Uses its own Global Navigation Satellite System (GNSS) receiver and internal battery
- Includes a recovery buzzer

Baseline integration intent:

- Mount inside the upper portion of the fuselage where practical
- Keep the module's GNSS antenna oriented toward the sky
- Avoid placing carbon-fiber reinforcement directly over or around the module
- Keep reasonable separation from high-current motor/ESC wiring and other radio-frequency equipment
- No Pixhawk serial connection is required for the baseline installation

Verification required after receipt and before flight:

- Confirm exact Ruko R111S model and physical condition
- Record the module Remote ID serial number before discarding packaging
- Confirm the serial number is accepted by the FAA DroneZone registration workflow for the applicable Broadcast Module Declaration of Compliance
- Confirm charging and battery operation
- Confirm GNSS position acquisition from the intended internal mounting location
- Confirm Remote ID broadcast can be detected outside the fully assembled fuselage
- Confirm the module remains securely mounted throughout expected flight loads
- Confirm final installed mass and center-of-gravity effect

FAA registration and Remote ID serial-number association are required before applicable flight operations.

---

## RC Transmitter

**Selected:** RadioMaster TX16S MK3 ELRS

**Status:** Received

Procurement source: Buddy RC

Role:

- Primary pilot-side manual radio-control transmitter
- Native ExpressLRS control link to the RadioMaster RP4TD receiver
- Supports MP-1 manual flight, flight-mode selection, Return-to-Launch command, failsafe testing, and immediate pilot takeover
- Provides a reusable transmitter platform for future Project Meadowlark aircraft and receiver configurations

Baseline characteristics:

- EdgeTX operating system
- Native 2.4 GHz ExpressLRS support for the existing RP4TD receiver
- Sub-G 900 MHz ExpressLRS capability for future compatible receivers
- Up to 16 control channels
- 5-inch touchscreen
- External module expansion capability

Verification required:

- Confirm exact received model and configuration
- Confirm Mode 2 control layout
- Confirm correct United States/FCC radio configuration
- Charge and verify transmitter battery operation
- Update and record approved EdgeTX and ExpressLRS firmware versions as needed
- Bind to the RP4TD receiver
- Calibrate sticks and controls
- Configure MP-1 model profile
- Verify channel mapping, switches, flight modes, and failsafe behavior
- Perform link-quality and range testing before flight

---

## RC Transmitter Battery

**Selected:** RadioMaster 21700 5000 mAh 2S Li-ion Battery

**Status:** Received

Procurement source: Buddy RC

Baseline specifications:

- 21700 lithium-ion cell format
- 5000 mAh
- 2S
- 7.4 V nominal
- Intended for RadioMaster TX16S-series transmitters

Known product cost:

- $18.19

Role:

- Primary operating battery for the RadioMaster TX16S MK3 ELRS transmitter
- Charged through the transmitter's supported charging system during normal use

Verification required:

- Confirm physical fit in transmitter battery compartment
- Confirm connector compatibility and polarity
- Confirm normal charge behavior
- Confirm transmitter runtime and low-voltage warning behavior

---

# Wiring and Integration Materials

The following supporting materials have been received for MP-1 integration.

## GetFPV Order

| Item | SKU | Quantity | Cost |
|---|---:|---:|---:|
| XT60 Power Connectors | 1100 | 5 pairs | $5.99 |
| Silicone Wire 12 AWG — Black | 2619 | 1 m | $4.49 |
| Silicone Wire 12 AWG — Red | 2618 | 1 m | $4.49 |
| Silicone Wire 22 AWG — Black | 2607 | 1 m | $2.49 |
| Silicone Wire 22 AWG — Red | 2606 | 1 m | $2.49 |
| Male-to-Female Servo Extension Cable, twisted 22 AWG, JR style, 30 cm | 1611 | 5 | $9.49 |

GetFPV order totals, including the RP4TD receiver and HQProp propellers:

- Merchandise subtotal: $67.42
- Shipping and handling: $6.99
- Tax: $5.93
- Grand total: $80.34

## Amazon Order

**BOJACK 26 AWG Flexible Silicone Wire Kit**

**Status:** Received

Contents include:

- Five wire colors
- 26 American Wire Gauge (AWG) silicone wire
- Heat-shrink tubing
- Mini wire stripper

Product cost: $15.99

The Amazon order also included the Hobbywing Skywalker 50A V2 electronic speed controller (ESC).

Known merchandise subtotal for the two Amazon items: **$42.79**.

Final delivered Amazon total is not recorded here unless confirmed from the completed order.

The Ruko R111S Remote ID module was ordered separately through Amazon and has now been received. Purchase price and completed-order totals should be recorded only when confirmed from the order record.

---

# Deferred Components

No major RC-control component remains intentionally deferred for the MP-1 baseline.

Future capability additions remain deferred until the baseline aircraft has been verified, including companion computing, vision systems, mission payloads, and optional additional sensors.

---

# Evaluated but Not Selected

| Component | Disposition |
|---|---|
| Corona DS929MG servo | Original Flightory reference; replaced by EMAX ES3059MD for MP-1 procurement |
| Tattu G-Tech 5200 mAh 4S 35C XT60 | Suitable alternative battery; not selected for the MP-1 baseline |
| Spektrum SPMX50004S50H5 Smart G1 5000 mAh 4S 50C IC5 | Previous MP-1 baseline; original and same-model replacement failed bench acceptance and were replaced by SPMX54S50H5 Smart G2 |
| Spektrum 5000 mAh 4S 30C Smart G2 hardcase | Evaluated; heavier than preferred |
| Tattu 7000 mAh 4S 25C | Evaluated; additional mass and packaging disadvantage for MP-1 |

---

# Remaining Procurement

No additional major electronic hardware is required to **begin physical assembly** or to complete the current baseline component set.

Remaining purchases should be limited to integration hardware established by the physical build, such as:

- Battery connector adapter or harness hardware
- Motor/ESC connector hardware if the received components do not already mate
- Mounting hardware
- Fasteners
- Control linkages
- Cable-management materials

Additional small connectors, adapters, fasteners, or harness materials should be purchased only after the physical wiring and installation layout establishes a need.

An airspeed sensor remains optional and should not be procured until the test program establishes a requirement.

---

# Compatibility Requirements

All selected MP-1 hardware should support:

- One 4S flight-battery architecture
- ArduPlane
- Holybro Pixhawk 6C Mini
- Manual flight
- Stabilized flight
- Autonomous waypoint navigation
- Return-to-launch
- Immediate pilot takeover
- Manual landing
- Reliable flight logging
- Required Remote ID compliance for applicable United States operations

---

# Purchase Checklist

Before purchasing any additional component, confirm:

- Correct manufacturer and model number
- Required variant
- Connector compatibility
- Voltage compatibility
- Current capacity
- Physical fit
- Mass impact
- Manufacturer documentation
- Availability of replacement parts
- Compatibility with the existing MP-1 baseline

Do not substitute a component solely because it is available.

---

# Verification Required

Selection or purchase alone does not approve a component.

Each installed component must pass the applicable verification defined in `testing.md`.

Verification may include:

- Physical inspection
- Correct installation
- Connector and polarity checks
- Functional operation
- Electrical measurements
- Integration with adjacent systems
- Ground testing
- Flight validation where applicable

Actual measurements and test results belong under `evidence/`, not in this document.

---

# Configuration Control

Whenever a selected component changes:

1. Update this document.
2. Record the reason in `decisions.md` when the change is significant.
3. Update `build.md` if installation or wiring changes.
4. Update `testing.md` if verification requirements change.
5. Re-test affected systems.
6. Preserve evidence for the tested configuration.

---

# Relationship to Other Documents

| Document | Purpose |
|---|---|
| `design.md` | System architecture and requirements |
| `components.md` | Hardware selection and procurement status |
| `build.md` | Installation and configuration |
| `testing.md` | Verification procedures |
| `decisions.md` | Engineering rationale |
| `evidence/` | Actual inspections, measurements, configurations, logs, and test results |

This document is the authoritative source for the MP-1 hardware baseline and component procurement status.