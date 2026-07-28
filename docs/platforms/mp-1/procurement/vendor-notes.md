# Vendor Notes

## Purpose

This document records the engineering rationale behind MP-1 procurement decisions. It complements the procurement matrix by documenting manufacturer quality, source confidence, product-family observations, long-term support considerations, and unresolved risks.

Engineering decisions follow this order:

1. Requirements
2. Manufacturer documentation
3. Original Flightory design references
4. Independent engineering testing
5. Community operational experience
6. Engineering evaluation
7. Procurement
8. Verification testing

Verification testing is used to validate procurement decisions after purchase, not to discover whether an undocumented component is acceptable.

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
| Research | Important technical or sourcing evidence remains incomplete. |
| Future Evaluation | Candidate is outside the current procurement baseline but may be reconsidered later. |
| Provisional | Research is complete enough to support procurement, but MP-1 validation is pending. |
| Approved | Component has passed procurement, integration, and verification testing. |

## Design Role

| Design Role | Meaning |
|-------------|---------|
| Reference | Preferred baseline component for the current MP-1 configuration. |
| Alternative | Substitute candidate if the reference component is unavailable or unsuitable. |

---

# Source Confidence

| Confidence | Meaning |
|------------|---------|
| Verified | Manufacturer documentation and MP-1 engineering validation are both available. |
| High | Strong manufacturer documentation supported by reputable independent evidence. |
| Medium | Useful evidence exists, but manufacturer data or independent validation is incomplete. |
| Low | Evidence is primarily community-based, indirect, or insufficiently documented. |

---

# Flight Control Servos

## Corona DS929MG

### Summary

The Corona DS929MG is the current MP-1 reference servo because it is the closest documented match to the Flightory LARK baseline while remaining within the preferred weight and torque envelope.

### Strengths

- Closest match to the Flightory reference configuration
- Lightweight
- Metal gears
- Suitable operating voltage
- Adequate torque for the current airframe class
- Strong value

### Weaknesses

- Manufacturer documentation is less complete than Hitec documentation
- Long-term product availability should be monitored
- Published stall-current data should be confirmed during verification testing

Documentation Quality: **Good**

Engineering Confidence: **High**

Procurement Rank: **Best**

Status: **Provisional**

Design Role: **Reference**

---

## Hitec HS-82MG

### Summary

The Hitec HS-82MG is the documentation and support benchmark among the evaluated micro aviation servos. It offers strong torque and established aviation use, but its higher mass is a meaningful MP-1 trade-off.

### Strengths

- Excellent manufacturer documentation
- Established aviation use
- Strong torque
- Metal gears
- Long-term product and replacement support

### Weaknesses

- Heavier than the preferred MP-1 servo target
- Higher cost than the Corona reference candidate

Documentation Quality: **Excellent**

Engineering Confidence: **High**

Procurement Rank: **Better**

Status: **Provisional**

Design Role: **Alternative**

---

## EMAX ES08MD II

### Summary

The EMAX ES08MD II is a mechanically suitable digital-servo alternative, but incomplete electrical characterization limits confidence relative to the Corona and Hitec candidates.

### Strengths

- Lightweight
- Metal gears
- Digital control
- Competitive price

### Weaknesses

- Incomplete published current data
- Less complete aviation-specific documentation
- Long-term consistency between production revisions should be verified

Documentation Quality: **Fair**

Engineering Confidence: **Medium**

Procurement Rank: **Okay**

Status: **Provisional**

Design Role: **Alternative**

---

# Brushless Propulsion Motors

## T-Motor F90 2806.5 1300KV

### Summary

The T-Motor F90 2806.5 1300KV is the current MP-1 propulsion reference because it is the motor used in the Flightory LARK and has the strongest available published engineering data.

### Strengths

- Direct Flightory reference
- Excellent manufacturer documentation
- Published thrust and current data
- Suitable geometry for the MP-1 airframe
- Strong efficiency and build quality

### Weaknesses

- Manufacturer material emphasizes higher-voltage operation even though the Flightory configuration uses 4S
- Final propeller and current limits must be validated on the MP-1 installation
- Availability and price may be less favorable than the EMAX alternative

Documentation Quality: **Excellent**

Engineering Confidence: **High**

Procurement Rank: **Best**

Status: **Provisional**

Design Role: **Reference**

---

## EMAX ECO II 2807 1300KV

### Summary

The EMAX ECO II 2807 1300KV is the strongest value-oriented alternative. Its geometry and KV are suitable, and useful independent testing exists, but the total evidence set remains weaker than for the T-Motor reference.

### Strengths

- Competitive price
- Suitable motor class and KV
- Good community availability
- Useful independent test evidence
- Broad replacement availability

### Weaknesses

- Manufacturer data is less complete than T-Motor documentation
- Exact MP-1 propeller and current behavior requires validation
- Production revisions should be checked before purchase

Documentation Quality: **Good**

Engineering Confidence: **Medium**

Procurement Rank: **Better**

Status: **Provisional**

Design Role: **Alternative**

---

## FlyFishRC Flash 2806.5 1350KV

### Summary

The FlyFishRC Flash 2806.5 1350KV is mechanically plausible for MP-1 but is supported by less fixed-wing-specific evidence than the preferred candidates.

### Strengths

- Suitable motor geometry
- KV close to the MP-1 target
- Modern construction
- Competitive mass

### Weaknesses

- Primarily marketed toward FPV and multirotor use
- Limited fixed-wing endurance evidence
- Less complete independent data for the intended MP-1 propeller range

Documentation Quality: **Fair**

Engineering Confidence: **Low–Medium**

Procurement Rank: **Okay**

Status: **Provisional**

Design Role: **Alternative**

---

# Electronic Speed Controllers

## Hobbywing Skywalker 50A V2

### Summary

The Hobbywing Skywalker 50A V2 is the current MP-1 reference ESC. It provides the strongest combination of current margin, fixed-wing-specific firmware, BEC capability, documentation quality, and protection features.

### Strengths

- Fixed-wing-specific product family
- 50 A continuous current rating
- 70 A peak current rating
- 5 V/5 A switching BEC
- Active Freewheeling / DEO
- Search Mode
- Configurable brake, timing, startup, and low-voltage behavior
- Comprehensive thermal, overload, low-voltage, and signal-loss protection
- Excellent documentation
- Same published dimensions and mass as the 40 A model

### Weaknesses

- No native telemetry
- Final thermal margin depends on installation airflow
- BEC loading must still be verified with the complete avionics suite

Documentation Quality: **Excellent**

Engineering Confidence: **High**

Procurement Rank: **Best**

Status: **Provisional**

Design Role: **Reference**

Recommendation:

Use the Hobbywing Skywalker 50A V2 as the MP-1 reference ESC.

---

## Hobbywing Skywalker 40A V2

### Summary

The Skywalker 40A V2 is a strong lower-current alternative. It retains the same product-family features and BEC capability as the 50 A model but provides less propulsion-current margin.

### Strengths

- Fixed-wing-specific firmware
- 5 V/5 A switching BEC
- Excellent documentation
- Active Freewheeling / DEO
- Search Mode
- Comprehensive protection features
- Same published dimensions and mass as the 50 A model

### Weaknesses

- Reduced continuous-current margin
- Reduced peak-current margin
- Less tolerant of aggressive propeller or motor combinations

Documentation Quality: **Excellent**

Engineering Confidence: **High**

Procurement Rank: **Better**

Status: **Provisional**

Design Role: **Alternative**

---

## ZTW Beatles 40A

### Summary

The ZTW Beatles 40A is a credible budget-oriented fixed-wing ESC. It is acceptable for MP-1 but provides less BEC capability, lower burst-current margin, and fewer advanced features than the Hobbywing reference.

### Strengths

- Established fixed-wing product family
- Competitive pricing
- Adequate manufacturer documentation
- Standard fixed-wing programming functions

### Weaknesses

- 5 V/3 A BEC
- Lower peak-current capability
- Fewer advanced firmware features
- Reduced engineering margin relative to the Hobbywing 50 A reference

Documentation Quality: **Good**

Engineering Confidence: **Medium–High**

Procurement Rank: **Okay**

Status: **Provisional**

Design Role: **Alternative**

---

## T-Motor AT40A

### Summary

The T-Motor AT40A appears technically suitable as a conventional fixed-wing ESC, but the available manufacturer documentation is not yet complete enough to support a provisional procurement recommendation.

### Strengths

- Established aviation manufacturer
- Plausible current class for MP-1
- Fixed-wing product positioning

### Weaknesses

- Incomplete public technical documentation
- BEC specifications require confirmation
- Peak-current, protection, programming, dimensions, and mass require confirmation
- No clear advantage over the documented Hobbywing candidates

Documentation Quality: **Fair**

Engineering Confidence: **Medium**

Procurement Rank: **Okay**

Status: **Research**

Design Role: **Alternative**

---

## AM32 / BLHeli32 ESCs

### Summary

Modern firmware-based ESCs offer telemetry, RPM feedback, and advanced diagnostics. They remain outside the current MP-1 baseline because most are optimized for multirotors and often require additional power-system integration.

### Strengths

- Digital throttle protocols
- RPM feedback
- Telemetry
- Advanced configuration and diagnostics
- Strong future potential for closed-loop propulsion monitoring

### Weaknesses

- Greater integration complexity
- Often lack an integrated aviation-grade BEC
- Product documentation varies substantially by hardware vendor
- Limited benefit for the current simple endurance fixed-wing architecture
- Greater firmware and configuration-management burden

Documentation Quality: **Variable**

Engineering Confidence: **Medium**

Procurement Rank: **Okay**

Status: **Future Evaluation**

Design Role: **Alternative**

---

# Upcoming Procurement Categories

The remaining MP-1 procurement evaluations should proceed in this order:

1. Main Battery
2. Flight Controller
3. Power Module / External BEC
4. GPS / Compass
5. RC Receiver
6. Telemetry Radio
7. Propeller
8. Companion Computer

---

# Revision History

- Initial servo vendor assessments completed.
- Brushless motor vendor assessments completed.
- Electronic speed controller vendor assessments completed.
- Procurement rank, status, and design role standardized as separate fields.
- T-Motor AT40A classified as Rank **Okay**, Status **Research**.
- AM32 / BLHeli32 ESCs classified as Rank **Okay**, Status **Future Evaluation**.
- Main battery evaluation pending.
