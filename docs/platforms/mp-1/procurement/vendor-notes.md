# Vendor Notes

## Purpose

This document captures observations about manufacturers, component families, documentation quality, and engineering confidence for products evaluated for the MP-1 platform.

Unlike the Approved Components list, this document is intended to preserve engineering knowledge gathered during component evaluation. Vendor notes may include observations regarding documentation quality, long-term product support, replacement part availability, specification consistency, and other procurement considerations.

---

# Corona

## Overview

Corona is the manufacturer referenced by the original Flightory LARK documentation and serves as the baseline supplier for the MP-1 reference servo.

## Observations

- Closest known match to the original Flightory LARK servo recommendation.
- Lightweight metal-gear servo appropriate for lightweight fixed-wing aircraft.
- Manufacturer publishes operating voltage, operating current, and mechanical specifications.
- A reputable secondary datasheet provides idle and stall-current measurements suitable for engineering analysis.
- Good value with broad availability through RC distributors.

## Documentation Quality

**Good**

## Engineering Confidence

**High**

## Recommendation

Use as the MP-1 reference servo unless mission requirements justify a higher-performance alternative.

### References

| Source | Classification | Purpose |
|---------|----------------|---------|
| https://www.corona-rc.com/Product/120.html | Manufacturer | Product specifications and operating current |
| https://www.digikey.com/htmldatasheets/production/2307323/0/0/1/cor-ds929-mg.html | Authorized Distributor | Archived datasheet including idle and stall-current values |

---

# EMAX

## Overview

EMAX manufactures a wide range of RC electronics and servos with a strong reputation within the RC community. Their digital micro servos are considered viable alternatives for MP-1.

## Observations

- Good reputation within the RC aircraft community.
- Digital control provides improved centering compared with entry-level analog servos.
- Mechanical specifications are widely published.
- Electrical specifications, particularly operating and stall current, are inconsistent between vendors.
- No authoritative manufacturer documentation has yet been identified that fully supports power-budget engineering.

## Documentation Quality

**Fair**

## Engineering Confidence

**Medium**

## Recommendation

Approved as an alternate component pending validation through manufacturer documentation or bench testing.

### References

| Source | Classification | Purpose |
|---------|----------------|---------|
| Manufacturer product documentation (pending identification) | Manufacturer | Mechanical specifications |
| Multiple reseller listings | Secondary | General specifications only (not used for engineering values) |

---

# Hitec

## Overview

Hitec is a long-established manufacturer of RC servos with an excellent reputation in aviation, robotics, and industrial applications.

## Observations

- Extensive manufacturer documentation.
- Complete published electrical specifications including idle, operating, and stall current.
- Excellent long-term product support.
- Replacement gear sets and service parts readily available.
- Frequently used as a benchmark for high-quality RC servos.
- Increased weight compared with the Corona reference servo.

## Documentation Quality

**Excellent**

## Engineering Confidence

**Verified**

## Recommendation

Preferred premium supplier where increased weight and cost are acceptable in exchange for superior documentation, long-term support, and proven reliability.

### References

| Source | Classification | Purpose |
|---------|----------------|---------|
| https://hitecrcd.com/hs-82mg-standard-metal-gear-micro-servo/ | Manufacturer | Product specifications and electrical characteristics |
| https://hitecrcd.com/hs-85mg-premium-metal-gear-micro-servo/ | Manufacturer | Comparative electrical characteristics |

---

# Source Confidence Levels

Engineering decisions throughout Project Meadowlark should prioritize the highest-quality available evidence.

| Confidence | Definition |
|------------|------------|
| **Verified** | Confirmed through manufacturer documentation and/or direct engineering testing. |
| **High** | Supported by manufacturer documentation and reputable secondary technical sources. |
| **Medium** | Supported by multiple independent sources but lacking complete manufacturer verification. |
| **Low** | Community reports or anecdotal information only. Not suitable for engineering decisions without validation. |

---

# Source Classification

References throughout the procurement documentation should be interpreted using the following priority order.

| Priority | Source Type | Typical Examples |
|---------:|-------------|------------------|
| 1 | Manufacturer Documentation | Product pages, datasheets, application notes |
| 2 | Authorized Distributor Documentation | Digi-Key, Mouser, Arrow, Newark |
| 3 | Standards & Regulatory Documents | ASTM, ISO, FAA, IEC, etc. |
| 4 | Original Design References | Flightory LARK documentation, vendor reference designs |
| 5 | Independent Testing | Engineering evaluations, laboratory testing, verified reviews |
| 6 | Community Sources | Forums, blogs, hobbyist websites, videos |

Community sources should not be used as the sole basis for engineering decisions without independent verification.

---

# Revision Notes

This document is intended to evolve throughout the MP-1 program as additional manufacturers are evaluated. Historical observations should be retained where practical to preserve engineering rationale behind procurement decisions.