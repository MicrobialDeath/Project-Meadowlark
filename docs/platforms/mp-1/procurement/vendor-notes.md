# Vendor Notes

## Purpose

This document captures engineering observations regarding manufacturers, component families, documentation quality, long-term support, and engineering confidence for hardware evaluated for the MP-1 platform.

Unlike the Approved Components list, this document preserves the rationale behind procurement decisions and records lessons learned during component evaluation.

---

# Source Confidence Levels

Engineering decisions throughout Project Meadowlark should prioritize the highest-quality available evidence.

| Confidence | Definition |
|------------|------------|
| **Verified** | Confirmed through manufacturer documentation and/or direct engineering testing. |
| **High** | Supported by manufacturer documentation and reputable secondary technical sources. |
| **Medium** | Supported by multiple independent sources but lacking complete manufacturer verification. |
| **Low** | Community reports or anecdotal information only. Not suitable for engineering decisions without additional verification. |

---

# Source Classification

References throughout the procurement documentation should be interpreted using the following priority order.

| Priority | Source Type | Typical Examples |
|---------:|-------------|------------------|
| 1 | Manufacturer Documentation | Product pages, datasheets, application notes |
| 2 | Authorized Distributor Documentation | Digi-Key, Mouser, Arrow, Newark |
| 3 | Standards & Regulatory Documents | ASTM, ISO, FAA, IEC, etc. |
| 4 | Original Design References | Flightory LARK documentation, vendor reference designs |
| 5 | Independent Testing | Laboratory testing, thrust stand testing, engineering evaluations |
| 6 | Community Sources | RC Groups, Reddit, forums, blogs, YouTube, build logs |

Community sources should never be used as the sole basis for engineering decisions without corroborating evidence.

---

# Flight Control Servos

## Corona

### Overview

Corona is the manufacturer referenced by the original Flightory LARK documentation and serves as the baseline supplier for the MP-1 reference servo.

### Observations

- Closest known match to the original Flightory LARK servo recommendation.
- Lightweight metal-gear servo appropriate for lightweight fixed-wing aircraft.
- Manufacturer publishes operating voltage, operating current, and mechanical specifications.
- A reputable secondary datasheet provides idle and stall-current measurements suitable for engineering analysis.
- Good value with broad availability through RC distributors.

### Documentation Quality

**Good**

### Engineering Confidence

**High**

### Procurement Assessment

**Current Ranking:** Better

### Recommendation

Recommended as the baseline MP-1 servo due to compatibility with the Flightory reference aircraft and adequate engineering documentation.

### References

| Source | Classification | Purpose |
|---------|----------------|---------|
| https://www.corona-rc.com/Product/120.html | Manufacturer | Product specifications and operating current |
| https://www.digikey.com/htmldatasheets/production/2307323/0/0/1/cor-ds929-mg.html | Authorized Distributor | Archived datasheet including idle and stall-current values |

---

## EMAX (Servos)

### Overview

EMAX manufactures a wide range of RC electronics and servos with a strong reputation within the RC community.

### Observations

- Good reputation within the RC aircraft community.
- Digital control provides improved centering compared with entry-level analog servos.
- Mechanical specifications are widely published.
- Electrical specifications remain inconsistent between vendors.
- Manufacturer documentation lacks complete electrical characterization.

### Documentation Quality

**Fair**

### Engineering Confidence

**Medium**

### Procurement Assessment

**Current Ranking:** Okay

### Recommendation

Suitable alternate component pending additional electrical validation.

### References

| Source | Classification | Purpose |
|---------|----------------|---------|
| Manufacturer documentation | Manufacturer | Mechanical specifications |
| Multiple reseller listings | Secondary | General specifications only |

---

## Hitec

### Overview

Hitec is a long-established manufacturer of RC servos with an excellent reputation in aviation, robotics, and industrial applications.

### Observations

- Extensive manufacturer documentation.
- Complete electrical specifications including idle, operating, and stall current.
- Excellent long-term product support.
- Replacement gear sets readily available.
- Frequently used as a benchmark for premium RC servos.
- Heavier than the Corona reference servo.

### Documentation Quality

**Excellent**

### Engineering Confidence

**Verified**

### Procurement Assessment

**Current Ranking:** Best

### Recommendation

Preferred premium servo where additional weight and cost are acceptable.

### References

| Source | Classification | Purpose |
|---------|----------------|---------|
| https://hitecrcd.com/hs-82mg-standard-metal-gear-micro-servo/ | Manufacturer | Product specifications |
| https://hitecrcd.com/hs-85mg-premium-metal-gear-micro-servo/ | Manufacturer | Comparative electrical specifications |

---

# Brushless Motors

## T-Motor

### Overview

T-Motor is the manufacturer of the F90 2806.5 1300KV motor used as the reference propulsion system in the Flightory LARK.

### Observations

- Direct reference motor used by Flightory.
- Excellent manufacturer documentation.
- Detailed published propeller performance tables.
- Complete dimensional and electrical specifications.
- Excellent reputation within the FPV and endurance UAV community.
- Optimized for high efficiency and lightweight construction.
- Manufacturer recommends 5–6S operation; Flightory successfully operates the motor on 4S.

### Documentation Quality

**Excellent**

### Engineering Confidence

**High**

### Procurement Assessment

**Current Ranking:** Best (Provisional)

### Recommendation

Current leading candidate for MP-1 propulsion pending completion of the motor comparison study.

### References

| Source | Classification | Purpose |
|---------|----------------|---------|
| T-Motor F90 Product Page | Manufacturer | Mechanical and electrical specifications |
| T-Motor F90 Datasheet | Manufacturer | Performance data and propeller testing |
| Flightory LARK Documentation | Original Design Reference | Reference aircraft propulsion configuration |
| Independent thrust testing | Independent Testing | Comparative efficiency and thrust evaluation |

---

## EMAX (Motors)

### Overview

EMAX produces several brushless motor families suitable for endurance aircraft, including the ECO II 2807 series.

### Observations

- Strong value-oriented product line.
- Widely used throughout FPV and fixed-wing communities.
- Comparable geometry to the T-Motor F90.
- Flightory has selected the ECO II 2807 1300KV for related aircraft.
- Documentation is adequate but less comprehensive than T-Motor.

### Documentation Quality

**Good**

### Engineering Confidence

**Medium**

### Procurement Assessment

**Current Ranking:** Better (Provisional)

### Recommendation

Strong alternate candidate offering excellent value with similar operating characteristics.

### References

| Source | Classification | Purpose |
|---------|----------------|---------|
| EMAX ECO II Product Documentation | Manufacturer | Specifications |
| Flightory Documentation | Original Design Reference | Alternate propulsion recommendation |
| Independent thrust testing | Independent Testing | Comparative motor evaluation |

---

## FlyFishRC

### Overview

FlyFishRC manufactures modern FPV propulsion systems and has emerged as a competitive supplier of lightweight brushless motors.

### Observations

- Modern motor designs.
- Competitive pricing.
- Limited fixed-wing endurance data compared with T-Motor.
- Smaller body of published engineering documentation.
- Limited use in documented autonomous aircraft.

### Documentation Quality

**Fair**

### Engineering Confidence

**Low–Medium**

### Procurement Assessment

**Current Ranking:** Okay (Provisional)

### Recommendation

Suitable candidate for further evaluation but currently lacks the evidence supporting the higher-ranked alternatives.

### References

| Source | Classification | Purpose |
|---------|----------------|---------|
| FlyFishRC Product Documentation | Manufacturer | Mechanical specifications |
| Independent reviews | Independent Testing | Comparative observations |
| Community build logs | Community | Long-term operational experience |

---

# Revision Notes

This document is intended to evolve throughout the MP-1 program as additional hardware categories are evaluated.

Future sections are expected for:

- Electronic Speed Controllers (ESC)
- Batteries
- Flight Controllers
- Power Modules / BECs
- GPS / Compass Modules
- RC Receivers
- Telemetry Radios
- Propellers
- Companion Computers
- Payload Systems

Historical observations should be retained where practical to preserve the engineering rationale behind procurement decisions.
