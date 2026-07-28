# Vendor Notes

## Purpose

This document captures the engineering rationale behind procurement decisions for the MP-1 platform. Unlike the procurement matrix, which compares candidate components, this document records observations about manufacturers, documentation quality, long-term support, and engineering confidence.

Engineering decisions should follow this order:

1. Requirements
2. Manufacturer documentation
3. Original design references (Flightory)
4. Independent engineering testing
5. Community operational experience
6. Engineering evaluation
7. Procurement
8. Verification testing

---

# Source Confidence

| Confidence | Meaning |
|------------|---------|
| Verified | Manufacturer documentation and engineering validation. |
| High | Manufacturer documentation supported by reputable secondary sources. |
| Medium | Multiple independent sources but incomplete manufacturer data. |
| Low | Community evidence only. |

---

# Flight Control Servos

## Corona

### Summary

The Corona DS929MG is the baseline servo because it is the closest documented match to the Flightory LARK reference aircraft.

### Strengths

- Closest Flightory match
- Lightweight
- Metal gears
- Adequate published electrical specifications
- Strong value

### Weaknesses

- Documentation less complete than Hitec.

Documentation Quality: **Good**

Engineering Confidence: **High**

Current Procurement Rank: **Best**

---

## Hitec

### Summary

Hitec represents the documentation benchmark for micro aviation servos.

### Strengths

- Excellent datasheets
- Long-term parts support
- Proven aviation reliability

### Weaknesses

- Higher weight
- Higher cost

Documentation Quality: **Excellent**

Engineering Confidence: **Verified**

Current Procurement Rank: **Better**

---

## EMAX

### Summary

A capable alternative with incomplete electrical characterization.

Documentation Quality: **Fair**

Engineering Confidence: **Medium**

Current Procurement Rank: **Okay**

---

# Brushless Motors

## T-Motor

### Summary

The F90 2806.5 1300KV is the propulsion reference because it is the motor used in the Flightory LARK and has the strongest published engineering data.

### Strengths

- Direct Flightory reference
- Excellent documentation
- Published thrust data
- Strong efficiency

### Weaknesses

- Manufacturer optimizes for 5–6S although Flightory successfully operates on 4S.

Documentation Quality: **Excellent**

Engineering Confidence: **High**

Current Procurement Rank: **Best**

---

## EMAX

Good value alternative with comparable geometry and solid independent testing.

Documentation Quality: **Good**

Engineering Confidence: **Medium**

Current Procurement Rank: **Better**

---

## FlyFishRC

Modern FPV-oriented motor family with promising specifications but limited fixed-wing evidence.

Documentation Quality: **Fair**

Engineering Confidence: **Low–Medium**

Current Procurement Rank: **Okay**

---

# Electronic Speed Controllers

## Hobbywing

### Summary

The Skywalker V2 series is currently the engineering benchmark for MP-1 fixed-wing ESCs.

### Strengths

- Fixed-wing specific
- Excellent documentation
- 50A continuous / 70A peak (50A model)
- 5V / 5A switch-mode BEC
- Active Freewheeling (DEO)
- Search Mode
- Extensive programming
- Comprehensive protection functions
- Same published dimensions for 40A and 50A models

### Weaknesses

- No native telemetry

Documentation Quality: **Excellent**

Engineering Confidence: **High**

Current Procurement Rank: **Best**

Recommendation:

Use the Hobbywing Skywalker 50A V2 as the MP-1 reference ESC.

---

## ZTW

### Summary

Well-established fixed-wing ESC manufacturer with competitive pricing.

### Strengths

- Good reputation
- Adequate documentation
- Fixed-wing product family

### Weaknesses

- 5V / 3A BEC
- Lower burst current
- Fewer advanced features

Documentation Quality: **Good**

Engineering Confidence: **Medium–High**

Current Procurement Rank: **Okay**

---

## T-Motor ESCs

### Summary

The AT series appears technically suitable but currently lacks the level of publicly available documentation required for a reference procurement decision.

Documentation Quality: **Fair**

Engineering Confidence: **Medium**

Current Procurement Rank: **Research**

---

## AM32 / BLHeli ESCs

### Summary

Modern firmware-based ESCs provide telemetry and advanced diagnostics but are primarily optimized for multirotors.

### Strengths

- Telemetry
- RPM feedback
- DShot compatibility
- Excellent future potential

### Weaknesses

- Greater configuration complexity
- Often require external BECs
- Limited advantage for a simple endurance fixed-wing aircraft

Current Procurement Rank: **Future Evaluation**

---

# Upcoming Procurement Categories

- Main Battery
- Flight Controller
- Power Module / External BEC
- GPS / Compass
- RC Receiver
- Telemetry Radio
- Propeller
- Companion Computer

This document should evolve as additional hardware categories are evaluated, preserving the engineering rationale behind every procurement decision.
