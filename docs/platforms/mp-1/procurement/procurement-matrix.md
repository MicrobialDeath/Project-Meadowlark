# MP-1 Procurement Evaluation Matrix

## Purpose

This document records the engineering comparison of candidate hardware for the MP-1 platform. Rankings are based on published manufacturer documentation, independent testing, original Flightory references, and engineering suitability.

---

# Flight Control Servo Evaluation

| Attribute | Corona DS929MG | Hitec HS-82MG | EMAX ES08MD II |
|----------|----------------|---------------|----------------|
| Rank | Best | Better | Okay |
| Status | Provisional | Provisional | Provisional |
| Design Role | Reference | Alternative | Alternative |
| Voltage | 4.8–6.0 V | 4.8–6.0 V | 4.8–6.0 V |
| Weight | 12.5 g | 19 g | ~12 g |
| Gear Material | Metal | Metal | Metal |
| Torque | 2.2–2.5 kg·cm | 3.4 kg·cm | ~2.4 kg·cm |
| Documentation | Good | Excellent | Fair |
| Engineering Confidence | High | High | Medium |

### Recommendation

The Corona DS929MG remains the reference servo because it most closely matches the Flightory LARK baseline while providing sufficient published electrical characteristics.

---

# Brushless Motor Evaluation

| Attribute | T-Motor F90 1300KV | EMAX ECO II 2807 | FlyFishRC Flash 2806.5 |
|----------|---------------------|------------------|------------------------|
| Rank | Best | Better | Okay |
| Status | Provisional | Provisional | Provisional |
| Design Role | Reference | Alternative | Alternative |
| Motor Class | 2806.5 | 2807 | 2806.5 |
| KV | 1300 | 1300 | 1350 |
| MP-1 Voltage | 4S | 4S | 4S |
| Weight | 46.6 g | To Verify | To Verify |
| Peak Current | 45.1 A | To Verify | To Verify |
| Documentation | Excellent | Good | Fair |
| Independent Testing | Available | Available | Limited |
| Engineering Confidence | High | Medium | Low–Medium |

### Recommendation

The T-Motor F90 remains the reference propulsion motor because it is the original Flightory selection and has the strongest published engineering evidence.

---

# Electronic Speed Controller Evaluation

| Attribute | Hobbywing Skywalker 50A V2 | Hobbywing Skywalker 40A V2 | ZTW Beatles 40A | T-Motor AT40A |
|----------|-----------------------------|-----------------------------|-----------------|---------------|
| Rank | Best | Better | Okay | Alternate |
| Status | Provisional | Provisional | Provisional | Research |
| Design Role | Reference | Alternative | Alternative | Alternative |
| Continuous Current | 50 A | 40 A | 40 A | 40 A nominal |
| Peak Current | 70 A | 60 A | 50 A | To Verify |
| Battery | 3–4S | 3–4S | 2–4S | 2–4S reported |
| BEC | 5V / 5A Switching | 5V / 5A Switching | 5V / 3A | To Verify |
| Weight | 36 g | 36 g | 36 g | To Verify |
| Programming | Extensive | Extensive | Standard | Unknown |
| Active Freewheeling | Yes | Yes | Not Identified | Unknown |
| Search Mode | Yes | Yes | No | Unknown |
| Protection | Comprehensive | Comprehensive | Standard | Unknown |
| Documentation | Excellent | Excellent | Good | Fair |
| Engineering Confidence | High | High | Medium–High | Medium |

### Recommendation

The Hobbywing Skywalker 50A V2 is the current MP-1 reference ESC. It provides the strongest combination of current margin, documentation quality, switch-mode BEC capability, fixed-wing features, and protection functions.

The Skywalker 40A V2 remains an excellent lower-current alternative.

The ZTW Beatles 40A is an acceptable budget option but provides reduced BEC capability and lower burst-current margin.

The T-Motor AT40A remains under evaluation pending more complete manufacturer documentation.

---

## Procurement Philosophy

Component rankings are determined using the following order of evidence:

1. Published manufacturer specifications
2. Original Flightory design references
3. Independent engineering testing
4. Community operational experience
5. Engineering evaluation

Verification testing occurs after procurement to validate these selections rather than establish them.
