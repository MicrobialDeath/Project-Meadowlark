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
| Flight Controller | Holybro Pixhawk 6C Mini | 1 | Purchased |
| Flight-Controller Power Module | Holybro PM02 V3 | 1 | Purchased |
| GPS / Compass | Holybro M10 GPS V2 with IST8310 compass | 1 | Purchased |
| Battery | Spektrum SPMX50004S50H5 Smart LiPo, 5000 mAh 4S 50C IC5 | 1 | Ordered |
| Motor | T-Motor F90 2806.5 1300KV | 1 | Ordered |
| ESC | Hobbywing Skywalker 50A V2 | 1 | Ordered |
| Servos | EMAX ES3059MD 12 g Digital Metal Gear | 4 purchased / 3 installed | Ordered |
| RC Receiver | RadioMaster RP4TD ExpressLRS 2.4 GHz | 1 | Ordered |
| Propeller | HQProp 7×4.5 2-blade | 1 set / 4 props | Ordered |
| Telemetry Radio | Holybro SiK 915 MHz system or equivalent | — | Deferred / not selected |
| RC Transmitter | RadioMaster ExpressLRS-compatible handheld transmitter | — | Deferred / not selected |

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

**Status:** Purchased

Reason:

- Mature ArduPlane support
- Suitable fixed-wing navigation and autonomous-flight capability
- Well-documented Pixhawk ecosystem

Verification remains required after installation and configuration.

---

## Flight-Controller Power Module

**Selected:** Holybro PM02 V3

**Status:** Purchased

Role:

- Powers the Pixhawk flight-controller domain
- Provides flight-battery voltage/current measurement

The servo rail remains powered separately by the electronic speed controller (ESC) battery eliminator circuit (BEC).

---

## GPS / Compass

**Selected:** Holybro M10 GPS V2 with IST8310 compass

**Status:** Purchased

Role:

- Global Navigation Satellite System (GNSS) position
- Navigation timing
- Magnetic heading reference

Final mounting location and magnetic-interference verification remain required.

---

## Flight Battery

**Selected:** Spektrum SPMX50004S50H5 Smart LiPo

**Status:** Ordered

Baseline specifications:

- 5000 mAh
- 4S
- 14.8 V nominal
- 50C
- IC5 connector
- Spektrum Smart battery integration

Procurement:

- Quantity: 1
- Product cost: $71.99
- Handling: $12.99
- Tax: $5.74
- Total paid: $90.72

Charging:

- Intended charger: Spektrum S2100 Smart Charger, model SPMXC1010
- The Spektrum Smart battery/charger combination is the MP-1 baseline charging arrangement.

**Evaluated alternative:** Tattu G-Tech 5200 mAh 4S 35C XT60

The Tattu remains a technically suitable lighter alternative but is no longer the selected MP-1 baseline battery.

Verification required:

- Confirm exact received model
- Physical dimensions and fit
- Aircraft connector integration
- Battery mass
- Center-of-gravity effect
- Voltage under load
- Capacity/condition
- Smart-charger operation

---

## Motor

**Selected:** T-Motor F90 2806.5 Long Range Motor

**Variant:** 1300KV

**Status:** Ordered

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

**Status:** Ordered

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

**Status:** Ordered

Configuration:

- Quantity purchased: 4
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

**Status:** Ordered

GetFPV:

- SKU: 21602
- Quantity: 1
- Product cost: $32.49

Role:

- Aircraft-side manual radio-control receiver
- Interfaces the pilot-control link with the Pixhawk

The matching handheld ExpressLRS (ELRS) transmitter is intentionally deferred until later in the build.

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

**Status:** Ordered

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

# Wiring and Integration Materials

The following supporting materials have been purchased for MP-1 integration.

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

**Status:** Ordered

Contents include:

- Five wire colors
- 26 American Wire Gauge (AWG) silicone wire
- Heat-shrink tubing
- Mini wire stripper

Product cost: $15.99

The Amazon order also included the Hobbywing Skywalker 50A V2 electronic speed controller (ESC).

Known merchandise subtotal for the two Amazon items: **$42.79**.

Final delivered Amazon total is not recorded here unless confirmed from the completed order.

---

# Deferred Components

The following components are intentionally **not required to begin physical assembly**.

## RC Transmitter

**Status:** Deferred / not selected

Required before manual flight operations.

Target class:

- RadioMaster handheld transmitter
- Native 2.4 GHz ExpressLRS (ELRS)
- Compatible with the purchased RP4TD receiver
- Sufficient switches and controls for MP-1 flight modes and pilot takeover

The transmitter is the pilot's primary manual-control interface.

---

## Telemetry Radio

**Status:** Deferred / not selected

Required later for ground-station data connectivity and test monitoring, but not required to begin airframe assembly.

Current candidate:

- Holybro SiK Telemetry Radio V3
- 915 MHz United States configuration
- Approximately 100 mW class
- Air/ground radio pair

Role:

- MAVLink data connection between Pixhawk and ground station
- Mission/configuration support
- Live aircraft status and telemetry

Telemetry is not the primary manual flight-control link.

Final model and procurement source remain open.

---

# Evaluated but Not Selected

| Component | Disposition |
|---|---|
| Corona DS929MG servo | Original Flightory reference; replaced by EMAX ES3059MD for MP-1 procurement |
| Tattu G-Tech 5200 mAh 4S 35C XT60 | Suitable alternative battery; replaced as baseline by Spektrum SPMX50004S50H5 |
| Spektrum 5000 mAh 4S 30C Smart G2 hardcase | Evaluated; heavier than preferred |
| Tattu 7000 mAh 4S 25C | Evaluated; additional mass and packaging disadvantage for MP-1 |

---

# Remaining Procurement

No additional major hardware is required to **begin physical assembly**.

The following items remain intentionally deferred:

1. RadioMaster ExpressLRS-compatible handheld transmitter — required before manual flight.
2. Holybro SiK 915 MHz telemetry radio system or equivalent — required before telemetry-dependent setup/test operations.

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
