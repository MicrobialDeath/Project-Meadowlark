# MP-1 Components

**Status:** Draft

## Purpose

This document defines the hardware selected for Meadowlark Platform 1 (MP-1), records alternatives that were evaluated, identifies remaining procurement and verification work, and tracks recorded project hardware costs.

It answers **what hardware the aircraft uses, what each major component does, and what has been purchased**.

It does **not** describe:

- System architecture (see [design.md](design.md))
- Assembly and configuration (see [build.md](build.md))
- Test procedures (see [testing.md](testing.md))
- Engineering rationale and history (see [decisions.md](decisions.md))

---

## Component Selection Philosophy

MP-1 is intended to establish a reliable, reproducible baseline aircraft.

Components are selected according to the following priorities:

1. Compatibility with ArduPlane
2. Proven reliability
3. Ease of replacement
4. Availability
5. Cost
6. Future expandability

The baseline aircraft favors mature, well-understood hardware over maximum performance.

---

## Current Reference Configuration

| System | Selected Component | Selection Status | Procurement Status |
|---|---|---|---|
| Airframe | Flightory LARK | Reference | In fabrication |
| Flight Controller | Holybro Pixhawk 6C Mini — Model-A revision | Selected | **Purchased** |
| Power Module | Holybro PM02 V3 | Selected | **Purchased** |
| GPS / Compass | Holybro M10 GPS V2 IP67 — u-blox M10, IST8310, Standard 10-pin | Selected | **Purchased** |
| Firmware | ArduPlane | Selected | Software |
| Motor | T-Motor F90 2806.5 1300KV | Baseline | Not recorded here |
| ESC | Hobbywing Skywalker 50A V2 | Baseline | Not recorded here |
| Battery | Tattu G-Tech 4S 5200 mAh | Baseline | Not recorded here |
| Servos | Corona DS929MG | Baseline | Not recorded here |

The remaining systems are still under evaluation or awaiting final interface definition.

---

## Flight Controller

### Selected

**Holybro Pixhawk 6C Mini — Model-A revision**

### What It Does

The flight controller is the aircraft's central autopilot computer. It reads onboard sensors and pilot commands, runs ArduPlane, stabilizes the aircraft, commands the control surfaces and motor output, executes waypoint missions, manages failsafes such as return-to-launch, and records flight data.

### Why We Selected It

- Full ArduPilot support
- Mature Pixhawk ecosystem
- Reliable documentation
- Compact size suitable for the LARK
- Sufficient I/O for the MP-1 baseline and later expansion
- Compatible with the selected Holybro power module and GPS architecture

No companion computer is required for the MP-1 baseline.

### Procurement Status

**Purchased.**

Purchased as a Holybro bundle with the PM02 V3 power module.

Bundle price paid: **$149.98 USD** before shipping.

---

## Power Module

### Selected

**Holybro PM02 V3**

### What It Does

The power module connects between the 4S flight battery and the aircraft power system. It provides regulated power to the Pixhawk and reports battery voltage and current to the flight controller so ArduPlane can monitor electrical load and battery condition.

It does **not** supply the servo rail in the MP-1 architecture. Servo power remains provided by the ESC's integrated BEC.

### Operating Constraint

For MP-1, treat **30 A continuous through the PM02 V3 supplied wiring and connectors as the conservative practical limit** unless the wiring or connector arrangement is deliberately revised and verified.

This constraint must be checked against the final propeller and measured propulsion current before flight.

### Why We Selected It

- Native fit with the Pixhawk 6C Mini ecosystem
- Supports the MP-1 4S battery architecture
- Provides regulated flight-controller power
- Provides battery voltage and current sensing
- Avoids adding a second independent avionics regulator to the baseline aircraft

### Procurement Status

**Purchased.**

Included in the **$149.98 USD Pixhawk 6C Mini + PM02 V3 bundle**.

The individual module cost is not separated in the purchase record.

---

## GPS / Compass

### Selected

**Holybro M10 GPS V2 IP67 — u-blox M10 — IST8310 compass — Standard 10-pin**

### What It Does

The GPS / compass module provides the Pixhawk with position, groundspeed, altitude reference, precise time, and magnetic heading information.

The u-blox M10 GNSS receiver supplies position and navigation data, while the integrated IST8310 compass supplies magnetic heading. Together they support waypoint navigation, return-to-launch, position-aware flight modes, and accurate flight logging.

### Why We Selected It

- Native standard 10-pin Pixhawk GPS1 connection
- Integrated IST8310 compass
- u-blox M10 multi-constellation GNSS receiver
- RF shielding and SAW filtering for improved signal integrity in an electrically noisy aircraft environment
- IP67 environmental protection without adding interface complexity
- Direct fit with the Holybro / Pixhawk ecosystem

### Procurement Status

**Purchased.**

Price paid: **$43.99 USD** before shipping.

---

## Propulsion

### Selected Motor

**T-Motor F90 2806.5 1300KV**

### What It Does

The motor converts electrical power from the flight battery, through the ESC, into propeller rotation and aircraft thrust.

### Alternatives Evaluated

- EMAX ECO II 2807
- FlyFishRC Flash

Motor verification remains part of propulsion testing.

---

## Electronic Speed Controller

### Selected

**Hobbywing Skywalker 50A V2**

### What It Does

The ESC controls electrical power delivered to the brushless motor in response to throttle commands from the flight controller. Its integrated BEC also provides the baseline power source for the MP-1 servo rail.

### Alternatives Evaluated

- Hobbywing Skywalker 40A V2
- ZTW Beatles 40A
- T-Motor AT40A

Selection may be revisited if testing identifies a clear requirement.

---

## Servos

### Selected

**Corona DS929MG**

### What They Do

The three primary servos convert flight-controller commands into mechanical movement of the aircraft control surfaces, providing roll, pitch, and yaw control as required by the LARK configuration.

### Alternatives Evaluated

- Hitec HS-82MG
- EMAX ES08MD II

Servo performance and servo-rail loading will be verified during ground and flight testing.

---

## Battery

### Selected

**Tattu G-Tech 4S 5200 mAh**

### What It Does

The battery is the single removable primary energy source for the MP-1 baseline aircraft. It supplies both propulsion power and, through the PM02 V3 and ESC BEC paths, flight-controller, avionics, and servo power.

### Alternatives Evaluated

- Admiral 5000
- SMC 5200

The baseline aircraft uses one removable 4S battery.

---

## Procurement Cost Ledger

This ledger records confirmed project purchases as they are entered into the repository. The running total represents **only purchases currently recorded here** and should not be interpreted as the complete historical project cost until earlier purchases are backfilled.

### Holybro Order — Flight Controller, Power Module, and GPS

| Item | Price Paid |
|---|---:|
| Pixhawk 6C Mini Model-A revision + PM02 V3 bundle | $149.98 |
| M10 GPS V2 IP67 — M10 / Standard 10-pin | $43.99 |
| Shipping | $42.20 |
| **Order Total** | **$236.17** |

**Recorded MP-1 project spend to date: $236.17 USD**

Future purchases should be appended to this ledger with item cost, shipping or order-level charges where known, and a revised running total.

---

## Remaining Component Selection

The following items remain open:

- Propeller
- RC receiver
- Telemetry radio
- Connectors
- Wiring materials

These items should be selected only after confirming compatibility with the baseline configuration.

---

## Compatibility Requirements

All selected hardware should support:

- ArduPlane
- 4S electrical system
- Pixhawk-compatible interfaces
- Standard PWM servo outputs
- Standard RC protocols
- GPS with integrated compass
- MAVLink telemetry

---

## Procurement Checklist

Before purchasing hardware, verify:

- Model number
- Current manufacturer specifications
- Electrical compatibility
- Physical fit
- Connector compatibility
- Availability of replacement parts
- Documentation availability
- Price paid and shipping cost for the project ledger

Avoid substituting components solely because they appear similar.

---

## Verification Required

Component selection and procurement do not mean a component is flight-proven.

Verification includes:

- Mechanical fit
- Electrical compatibility
- Connector and pinout verification
- Configuration
- Ground operation
- Load testing where applicable
- Flight performance
- Reliability

Verification procedures are defined in [testing.md](testing.md).

---

## Future Hardware

Future hardware may include:

- Companion computer
- Payload systems
- Vision hardware
- Additional sensors
- Redundant power
- Alternative propulsion

These additions should not change the baseline aircraft until the initial platform has been fully validated.

---

## Revision Policy

This document records the current hardware baseline, procurement status, and recorded hardware cost for MP-1.

When hardware changes or new items are purchased:

- Update the selected component and procurement status.
- Add confirmed costs to the procurement cost ledger.
- Move replaced hardware to the alternatives list if still relevant.
- Record significant engineering decisions in [decisions.md](decisions.md).
- Verify the updated configuration using the procedures in [testing.md](testing.md).

Specific build records and test results belong in the future `docs/platforms/mp-1/evidence/` directory once evidence is produced.
