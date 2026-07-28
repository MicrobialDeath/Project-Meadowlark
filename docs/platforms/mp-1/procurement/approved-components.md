# MP-1 Approved Components

## Purpose

This document identifies the current procurement candidates for the MP-1 platform. Components are ranked according to available engineering evidence collected before procurement. Rankings guide purchasing decisions and remain provisional until validated through MP-1 integration and verification testing.

## Procurement Classification

### Rank

| Rank | Meaning |
|------|---------|
| Best | Current reference recommendation for MP-1. |
| Better | Strong alternative with minor trade-offs. |
| Okay | Acceptable alternative with lower engineering confidence or reduced capability. |

### Status

| Status | Meaning |
|--------|---------|
| Research | Candidate remains under investigation because important evidence is incomplete. |
| Future Evaluation | Candidate is not part of the current procurement baseline but may be reconsidered later. |
| Provisional | Research is complete enough to support procurement, but the component has not yet been validated in MP-1. |
| Approved | Component has passed procurement, integration, and verification testing. |

### Design Role

| Design Role | Meaning |
|-------------|---------|
| Reference | Preferred baseline component for the current MP-1 configuration. |
| Alternative | Substitute candidate that may be procured if the reference component is unavailable or unsuitable. |

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

## Revision History

- Initial flight-servo evaluation completed.
- Brushless propulsion motor evaluation completed.
- Electronic speed controller evaluation completed.
- Procurement terminology standardized so rank, status, and design role are distinct fields.
- Main battery evaluation pending.
