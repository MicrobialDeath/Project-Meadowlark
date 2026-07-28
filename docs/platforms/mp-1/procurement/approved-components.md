# MP-1 Approved Components

## Purpose

This document identifies the current procurement candidates for the MP-1 platform. Components are ranked according to available engineering evidence collected before procurement. Rankings are intended to guide purchasing and will be verified during integration testing.

## Procurement Status

| Rank | Meaning |
|------|---------|
| Best | Current reference recommendation for MP-1. |
| Better | Strong alternative with minor trade-offs. |
| Okay | Acceptable alternative with lower engineering confidence. |

| Status | Meaning |
|--------|---------|
| Provisional | Research complete but not yet validated in MP-1. |
| Approved | Validated after procurement and integration testing. |

---

# Flight Control Servos

## Primary Flight Servos

| Rank | Component | Status | Design Role | Notes |
|------|-----------|--------|-------------|-------|
| Best | Corona DS929MG | Provisional | Reference | Closest match to the Flightory LARK reference design. |
| Better | Hitec HS-82MG | Provisional | Alternative | Premium documentation and long-term support. |
| Okay | EMAX ES08MD II | Provisional | Alternative | Acceptable digital servo with incomplete published electrical data. |

### Engineering Requirements

| Requirement | Target |
|-------------|--------|
| Operating Voltage | 4.8–6.0 V |
| Gear Material | Metal |
| Weight | ≤15 g preferred |
| Torque | ≥2.0 kg·cm @ 6 V |
| Stall Current | ≤1.5 A preferred |
| Connector | JR/Futaba compatible |

---

# Brushless Propulsion Motors

## Propulsion Motor

| Rank | Component | Status | Design Role | Notes |
|------|-----------|--------|-------------|-------|
| Best | T-Motor F90 2806.5 1300KV | Provisional | Reference | Direct Flightory reference motor with strongest documentation. |
| Better | EMAX ECO II 2807 1300KV | Provisional | Alternative | Excellent value and strong community evidence. |
| Okay | FlyFishRC Flash 2806.5 1350KV | Provisional | Alternative | Mechanically suitable but supported by less fixed-wing evidence. |

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
| Best | Hobbywing Skywalker 50A V2 | Provisional | Reference | 50 A continuous, 70 A peak, 5V/5A switching BEC, extensive fixed-wing programming and protection features. |
| Better | Hobbywing Skywalker 40A V2 | Provisional | Alternative | Same published size and weight as the 50A model with reduced current margin. |
| Okay | ZTW Beatles 40A | Provisional | Alternative | Credible fixed-wing ESC with smaller BEC and lower burst capability. |
| Alternate | T-Motor AT40A | Research | Alternative | Awaiting complete manufacturer documentation. |

### Engineering Requirements

| Requirement | Target |
|-------------|--------|
| Continuous Current | 50 A preferred |
| Peak Current | ≥70 A preferred |
| Battery Compatibility | 4S required |
| BEC | 5 V / 5 A switching preferred |
| Aircraft Type | Fixed-wing specific preferred |
| Control Signal | Standard PWM |
| Programming | Brake, timing, startup, cutoff |
| Protection | Thermal, overload, low-voltage, signal-loss |
| Telemetry | Desirable but not required |

---

## Revision History

- Initial servo evaluation completed.
- Brushless motor evaluation completed.
- ESC evaluation completed.
- Main battery evaluation pending.
