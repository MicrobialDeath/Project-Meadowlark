# MP-1 Components

**Status:** Draft  
**Last Updated:** 2026-07-29

## Purpose

This document is the authoritative component record for Meadowlark Platform 1 (MP-1).

It combines:

- Selected baseline hardware
- Ranked alternatives
- Open component selections
- Purchase checks
- Known limitations
- Verification still required

A component is not considered fully approved until it has been received, inspected, integrated, and tested on MP-1.

## Status Terms

| Status | Meaning |
|--------|---------|
| Selected | Current baseline choice for MP-1 |
| Alternative | Acceptable substitute with known trade-offs |
| Research | More evidence is required before purchase |
| Deferred | Not part of the initial aircraft |
| Rejected | Not suitable for the current MP-1 baseline |
| Verified | Installed and successfully tested on MP-1 |

---

# Current Baseline

| Function | Selected Component | Status |
|----------|--------------------|--------|
| Flight Servos | Corona DS929MG | Selected |
| Propulsion Motor | T-Motor F90 2806.5 1300KV | Selected |
| Electronic Speed Controller | Hobbywing Skywalker 50A V2 | Selected |
| Servo Power | Skywalker 50A V2 integrated 5 V/5 A BEC | Selected, pending load test |
| Flight Battery | Tattu G-Tech 4S 5200 mAh 35C with XT60 | Selected |
| Flight Controller | Holybro Pixhawk 6C Mini | Selected |
| Flight-Controller Power Module | Holybro PM02 V3 | Research |
| GPS / Compass | Not selected | Open |
| RC Receiver | Not selected | Open |
| Telemetry Radio | Not selected | Open |
| Propeller | Not selected | Open |
| Airspeed Sensor | Not yet required | Deferred pending test plan |

The initial aircraft does not include a companion computer, payload battery, payload regulator, redundant avionics power, or mission payload.

---

# Flight Servos

## Selected: Corona DS929MG

**Status:** Selected, not yet verified

### Why it was selected

- Closest documented match to the Flightory LARK reference design
- Metal gears
- Digital control
- Low mass
- Suitable torque for the expected control surfaces
- Compatible with a 5 V servo rail

### Key specifications

| Item | Value |
|------|-------|
| Operating Voltage | 4.8–6.0 V |
| Published Weight | Approximately 12.5 g |
| Gear Material | Metal |
| Published Torque | Approximately 2.2–2.5 kg·cm |
| Connector | Standard three-wire servo connector |
| Initial Quantity | Three |

### Purchase checks

Confirm:

- Exact model is DS929MG
- Digital, metal-gear version
- Operating voltage is 4.8–6.0 V
- Connector wire order is documented
- Servo arms and mounting hardware are included
- Units are genuine and from the same production type where practical

### Verification still required

- Centering and repeatability
- Direction and travel range
- Gear play
- Current during unloaded movement
- Current under realistic control-surface load
- Simultaneous operation of all servos
- Servo-rail voltage during rapid movement
- Temperature during repeated operation

### Alternatives

#### Hitec HS-82MG

**Status:** Alternative

Strengths:

- Strong manufacturer documentation
- Established aircraft use
- Higher torque
- Mature support

Trade-offs:

- Heavier
- More expensive
- Less consistent with the low-mass Flightory baseline

#### EMAX ES08MD II

**Status:** Alternative

Strengths:

- Low mass
- Metal gears
- Suitable voltage and torque range

Trade-offs:

- Less complete electrical documentation
- Greater uncertainty around transient current

---

# Propulsion Motor

## Selected: T-Motor F90 2806.5 1300KV

**Status:** Selected, not yet verified

### Why it was selected

- Original Flightory reference motor
- Strongest available manufacturer documentation
- Suitable size and KV for the planned 4S system
- Published performance data available
- Appropriate mass for the LARK airframe

### Key specifications

| Item | Value |
|------|-------|
| Motor Class | 2806.5 |
| KV | 1300 |
| Battery | 4S |
| Published Weight | Approximately 46.6 g |
| Candidate Propeller Range | Approximately 7×4 to 7×6 |
| Published High-Load Current Point | Approximately 45.1 A |

The published current point is not automatically the MP-1 operating current. Actual current depends on the selected propeller and installation.

### Purchase checks

Confirm:

- Exact model is F90 2806.5 1300KV
- No higher-KV substitute
- Shaft and bell are undamaged
- Mounting-hole pattern matches the airframe installation
- Supplied screws are not long enough to contact the windings
- Motor-wire length and termination are suitable

### Verification still required

- No-load current
- Rotation direction
- Bearing condition
- Shaft runout
- Vibration
- Static thrust
- Static current with final propeller
- Motor temperature
- Mount and fastener integrity

### Alternatives

#### EMAX ECO II 2807 1300KV

**Status:** Alternative

Strengths:

- Good value
- Suitable size and KV
- Available independent test evidence

Trade-offs:

- Less direct fixed-wing evidence
- Weaker documentation than the T-Motor reference

#### FlyFishRC Flash 2806.5 1350KV

**Status:** Alternative

Strengths:

- Mechanically plausible
- Similar size and KV

Trade-offs:

- Less fixed-wing evidence
- Lower documentation confidence

---

# Electronic Speed Controller

## Selected: Hobbywing Skywalker 50A V2

**Status:** Selected, not yet verified

### Why it was selected

- Fixed-wing-specific product
- 4S compatibility
- 50 A continuous rating
- 70 A peak rating
- Integrated 5 V/5 A switching BEC
- Good programming options
- Strong protection features
- Strong manufacturer documentation

### Key specifications

| Item | Value |
|------|-------|
| Continuous Current | 50 A |
| Peak Current | 70 A |
| Battery Range | 3S–4S LiPo |
| BEC | 5 V/5 A switching |
| Control Signal | Standard PWM |
| Published Weight | Approximately 36 g |
| Telemetry | None |

### Purchase checks

Confirm:

- Exact model is Skywalker 50A V2
- Unit is the fixed-wing version
- Battery range includes 4S
- BEC is 5 V/5 A
- Battery connector and motor connectors are identified
- Included wire lengths and gauges are documented
- Programming instructions are included or archived

### Verification still required

- BEC output voltage
- Motor startup
- Brake behavior
- Throttle calibration
- Static current
- Rapid throttle response
- ESC temperature
- Connector temperature
- Protection behavior where safely testable
- No flight-controller or receiver reset during operation

### Alternatives

#### Hobbywing Skywalker 40A V2

**Status:** Alternative

Trade-off:

- Same general architecture with less current margin

#### ZTW Beatles 40A

**Status:** Alternative

Trade-offs:

- Smaller 5 V/3 A BEC
- Lower peak-current margin
- Weaker documentation

#### T-Motor AT40A

**Status:** Research

Do not purchase until exact current, BEC, voltage, weight, and programming specifications are confirmed from manufacturer documentation.

---

# Servo Power

## Selected: Skywalker 50A V2 Integrated BEC

**Status:** Selected, pending load verification

The ESC’s integrated 5 V/5 A switching BEC is the baseline servo-power source.

It is expected to power:

- Left aileron servo
- Right aileron servo
- Elevator servo
- RC receiver, depending on final receiver wiring

### Why it was selected

- Already included in the selected ESC
- No additional regulator mass
- No extra high-current wiring
- Simplest initial configuration
- Expected to provide substantial margin over normal three-servo operating current

### Required acceptance tests

The integrated BEC remains acceptable only if:

- Servo rail stays above 4.8 V
- All servos can move rapidly at the same time
- No flight-controller reset occurs
- No receiver reset occurs
- No unacceptable servo jitter occurs
- Rapid throttle changes do not disturb the rail
- ESC and BEC temperatures remain acceptable

## Contingency: Hobbywing UBEC 5A

**Status:** Deferred contingency

Use only if:

- Integrated BEC testing fails
- Additional flight-critical loads are added
- A later reliability requirement justifies separate servo power

If used:

- Set output to 5.0 V
- Disconnect or isolate the ESC BEC positive lead
- Keep the ESC signal and ground connected
- Never connect both BEC positive outputs in parallel

---

# Flight Battery

## Selected: Tattu G-Tech 4S 5200 mAh 35C with XT60

**Status:** Selected, not yet verified

### Why it was selected

- Best balance of energy, mass, size, and documentation
- Only evaluated candidate within the preferred 450 g target
- Factory XT60
- Compatible with the selected 4S propulsion system
- No adapter required

### Key specifications

| Item | Value |
|------|-------|
| Chemistry | LiPo |
| Cell Count | 4S |
| Nominal Voltage | 14.8 V |
| Fully Charged Voltage | 16.8 V |
| Capacity | 5,200 mAh |
| Nominal Energy | 76.96 Wh |
| Published Weight | Approximately 436.5 g |
| Published Dimensions | Approximately 133 × 45 × 33.5 mm |
| Main Connector | XT60 |
| Balance Connector | JST-XH compatible |

### Purchase checks

Confirm:

- Exact 4S 5200 mAh 35C model
- Soft-pack construction
- Factory XT60
- JST-XH-compatible balance connector
- Published mass and dimensions
- No damaged cells or packaging
- Cell voltages are balanced on arrival

### Verification still required

- Battery-bay fit
- Restraint
- Center of gravity
- Voltage sag
- Temperature
- Measured usable capacity
- Cruise current
- Flight endurance
- Landing behavior at expected mass

### Alternatives

#### Admiral 4S 5000 mAh 40C with XT60

**Status:** Alternative

Trade-offs:

- Heavier
- Longer
- Slightly less energy

#### SMC HCL-HP 4S 5200 mAh 80C with Factory XT60

**Status:** Alternative

Trade-offs:

- Significantly heavier
- Same nominal energy as the reference
- Factory XT60 must be selected correctly

#### Ovonic 4S 6000 mAh 120C with XT60

**Status:** Research

Potential benefit:

- Higher nominal energy

Additional risks:

- Higher mass
- More center-of-gravity influence
- Increased landing energy
- Requires separate flight validation

## Rejected Battery Types

| Type | Reason |
|------|--------|
| 3S LiPo | Does not match the selected propulsion baseline |
| 5S LiPo | Exceeds the selected ESC input range |
| 4S Li-ion | Adds unnecessary pack and integration complexity |
| Hardcase LiPo | Adds unnecessary mass and volume |
| Adapter-dependent packs | Conflicts with the direct XT60 interface |
| Packs above approximately 525 g | Outside the current mass envelope |

---

# Flight Controller

## Selected: Holybro Pixhawk 6C Mini

**Status:** Selected, not yet verified

### Why it was selected

- Full ArduPlane support
- STM32H743 processor
- Onboard waypoint mission execution
- Dual IMUs
- Temperature-controlled sensors
- Fourteen PWM outputs
- Dual CAN
- Two GPS interfaces
- Removable microSD logging
- Compact size
- Standard Pixhawk connector ecosystem

### Initial role

The Pixhawk 6C Mini will provide:

- Manual and stabilized modes
- Onboard mission storage
- Waypoint navigation
- Return-to-launch
- RC pilot takeover
- Geofence behavior
- Failsafe behavior
- Battery monitoring
- Flight logging
- Telemetry communication

A companion computer is not required.

### Purchase checks

Confirm:

- Exact Pixhawk 6C Mini model
- Hardware revision
- Included harness set
- Included power cable
- Included microSD card, if any
- Dimensions and mass
- Mounting hardware
- Current ArduPlane support
- Analog power-input compatibility

### Verification still required

- Firmware installation
- Boot behavior
- microSD operation
- IMU and barometer detection
- PWM outputs
- Receiver input
- GPS and compass
- Telemetry
- Battery monitoring
- Failsafes
- Return-to-launch
- Pilot takeover
- Autonomous waypoint mission
- Log completeness

### Alternatives

#### CubePilot Cube Orange+ with Mini Carrier Board

**Status:** Alternative

Strengths:

- Triple IMUs
- Dual barometers
- Mature ecosystem
- Strong redundancy

Trade-offs:

- Higher cost
- Larger installed volume
- Carrier-board-dependent interfaces
- More integration complexity

#### Matek H743-WING V3

**Status:** Alternative

Strengths:

- Integrated fixed-wing power functions
- Direct battery input
- Integrated sensing and servo BEC
- Many UARTs and PWM outputs

Trade-offs:

- More soldering
- Less modular replacement
- More functions concentrated on one board
- Lower sensor redundancy

#### Holybro Pixhawk 6X with Mini Baseboard

**Status:** Alternative

Strengths:

- Triple sensors
- Dual power inputs
- Ethernet
- High expansion capacity

Trade-offs:

- Larger
- Heavier
- More expensive
- More capability than MP-1 currently needs

#### SpeedyBee F405 Wing

**Status:** Rejected

Reason:

- F405 processor and memory constraints
- Reduced redundancy
- Less suitable as the long-term reference autopilot

---

# Flight-Controller Power Module

## Leading Candidate: Holybro PM02 V3

**Status:** Research

### Why it is the leading candidate

- Direct analog compatibility with the Pixhawk 6C Mini
- Compact
- XT60 power path
- Keyed Pixhawk harness
- Voltage and current monitoring
- Published analog calibration values
- No unnecessary distribution hardware

### Main unresolved issue

The complete stock current path may have a lower continuous-current limit than the power-module circuit board or current sensor.

The final decision must consider:

- PCB current rating
- Connector current rating
- Wire-gauge rating
- Sustained propulsion current
- Takeoff and climb duration
- Voltage drop
- Temperature

The PM02 V3 cannot move from Research to Selected until the final propeller is chosen and static current is measured or otherwise bounded with adequate confidence.

### Purchase checks

Confirm:

- Exact PM02 V3 model
- Analog version, not PM02D
- Included six-pin Pixhawk harness
- XT60 connector orientation and gender
- Wire gauge and length
- Board dimensions and mass
- Published voltage range
- Published current-sensor range
- Calibration values
- Current-production status

### Alternatives

#### Holybro PM06 V2

**Status:** Research

Trade-off:

- Adds power-distribution hardware that MP-1 does not need

#### Holybro PM07

**Status:** Research

Trade-offs:

- Larger
- Heavier
- More distribution-oriented than required

#### Mauch 100 A Hall-Effect System

**Status:** Deferred alternative

Strengths:

- Higher current capability
- Strong current measurement

Trade-offs:

- Separate regulator required
- More connector and harness work
- Higher integration complexity

#### Holybro PM02D / PM06D

**Status:** Rejected

Reason:

- Digital interface does not match the Pixhawk 6C Mini analog power input

---

# GPS and Compass

**Status:** Open

The selected unit must support:

- ArduPlane
- Pixhawk 6C Mini
- GPS position
- Compass heading
- Home-position establishment
- Waypoint navigation
- Return-to-launch
- Geofence behavior
- Documented keyed connection
- Adequate separation from propulsion wiring

### Purchase checks

Confirm:

- Exact GNSS receiver
- Compass inclusion
- Connector type
- Cable length
- Protocol
- Mounting hardware
- Current ArduPlane support
- Current production status

---

# RC Receiver

**Status:** Open

The receiver must support:

- Manual control
- Stabilized control
- Flight-mode selection
- Entry into autonomous mode
- Exit from autonomous mode
- Pilot takeover
- Link-loss failsafe
- Direct Pixhawk-compatible output
- No dependency on the ground telemetry radio

### Purchase checks

Confirm:

- Frequency and regional compatibility
- Transmitter compatibility
- Signal protocol
- Voltage range
- Failsafe behavior
- Antenna arrangement
- Required harness

---

# Telemetry Radio

**Status:** Open

Telemetry is required for test operations, but it is not a flight-control dependency.

The selected system must support:

- Mission upload
- Parameter review
- Ground monitoring
- Flight-mode reporting
- Position and altitude reporting
- Battery reporting
- Pixhawk serial connection
- Legal operation in the intended region

An already loaded mission must continue without the telemetry link.

### Purchase checks

Confirm:

- Frequency band
- Regional legality
- Air and ground radio pair
- Antennas
- Cables
- Connector pinout
- Power requirements
- Ground-station compatibility

---

# Propeller

**Status:** Open

The propeller is a critical unresolved item because it determines the actual propulsion load.

The selected propeller must match:

- Motor
- 4S battery
- ESC
- Shaft or adapter
- Airframe clearance
- Required thrust
- Acceptable current

### Purchase checks

Confirm:

- Diameter
- Pitch
- Rotation direction
- Hub bore
- Hub thickness
- Material
- Manufacturer limits
- Required adapter

### Verification still required

- Balance
- Static thrust
- Static current
- Motor temperature
- ESC temperature
- Vibration
- Airframe clearance

---

# Airspeed Sensor

**Status:** Deferred pending test plan

An airspeed sensor will be selected only if the initial test plan shows that it is required.

The first MP-1 waypoint tests may be conducted without one if ArduPlane configuration, environmental conditions, and test risk support that choice.

---

# Deferred Equipment

The following are outside the initial build:

| Item | Status |
|------|--------|
| Companion Computer | Deferred |
| Payload Computer | Deferred |
| Payload Battery | Deferred |
| Payload Regulator | Deferred |
| Mission-Equipment Power Distribution | Deferred |
| Redundant Flight-Controller Power | Deferred |
| Redundant Servo Power | Deferred |
| Camera Payload | Deferred |
| Experimental Mission Sensors | Deferred |
| Autonomous Takeoff | Deferred |
| Autonomous Landing | Deferred |

---

# Purchase Record

For every purchased component, record:

| Field | Required Information |
|------|----------------------|
| Category | Component function |
| Manufacturer | Exact manufacturer |
| Model | Exact model and variant |
| Revision | Hardware or product revision |
| Vendor | Seller or distributor |
| Product Reference | Product page or archived source |
| Quantity | Number ordered |
| Unit Price | Price at purchase |
| Order Date | Date ordered |
| Order Number | Vendor identifier |
| Received Date | Date received |
| Condition | New, used, or new-old stock |
| Included Items | Cables, connectors, mounts, antennas, manuals |
| Measured Mass | Received mass |
| Discrepancies | Listing versus received hardware |
| Inspection Record | Link or path |
| Test Record | Link or path |
| Final Status | Selected, Verified, Rejected, or Returned |

---

# Remaining Selection Order

Complete the remaining component work in this order:

1. Propeller
2. Flight-controller power module
3. GPS and compass
4. RC receiver
5. Telemetry radio
6. Airspeed sensor decision

The propeller now comes first because it determines the propulsion current and therefore affects the power-module decision.

---

# Related Documents

```text
docs/platforms/mp-1/README.md
docs/platforms/mp-1/design.md
docs/platforms/mp-1/build.md
docs/platforms/mp-1/testing.md
docs/platforms/mp-1/decisions.md
```

---

# Change History

## 2026-07-29

- Consolidated the former component-selection, procurement-matrix, and vendor-notes content.
- Simplified procurement terminology.
- Preserved selected hardware, alternatives, purchase checks, and remaining verification.
- Moved the propeller ahead of the power module in the remaining selection order because propulsion current determines the required current path.
