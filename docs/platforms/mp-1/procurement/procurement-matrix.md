# MP-1 Procurement Evaluation Matrix

## Flight Servo Evaluation

| Attribute | Corona DS929MG | EMAX ES08MD II | Hitec HS-82MG |
|----------|----------------|----------------|---------------|
| Classification | Reference | Approved | Preferred |
| Operating Voltage | 4.8–6.0 V | 4.8–6.0 V | 4.8–6.0 V |
| Weight | 12.5 g | ~12 g | 19 g |
| Gear Material | Metal | Metal | Metal |
| Torque | 2.2–2.5 kg·cm | ~2.4 kg·cm | 3.4 kg·cm |
| Idle Current | 10 mA | Unknown | 10 mA |
| Operating Current | 200–240 mA | Unknown | 280 mA |
| Stall Current | ~960 mA | Unknown | 1.8 A |
| Documentation Quality | Good | Fair | Excellent |
| Engineering Confidence | High | Medium | Verified |

## Engineering Assessment

### Corona DS929MG

Advantages:

- Closest match to the original Flightory LARK recommendation.
- Sufficient published electrical characteristics to support power-budget analysis.
- Lightweight and cost-effective.
- Serves as the MP-1 engineering reference component.

Trade-offs:

- Manufacturer documentation is less comprehensive than Hitec.
- Stall current is sourced from a reputable secondary datasheet rather than current manufacturer documentation.

---

### EMAX ES08MD II

Advantages:

- Digital control.
- Good reputation within the RC community.
- Similar size and weight to the Corona servo.

Trade-offs:

- Published electrical characteristics are incomplete.
- Requires validation before becoming a reference component.

---

### Hitec HS-82MG

Advantages:

- Excellent manufacturer documentation.
- Complete published electrical specifications.
- Long-established aviation reputation.
- Replacement gear sets and service parts readily available.

Trade-offs:

- Approximately 6–7 g heavier than the Corona reference servo.
- Higher cost.

---

## Procurement Recommendation

The Corona DS929MG remains the MP-1 reference servo because it best aligns with the Flightory reference design while providing sufficient published electrical characteristics for engineering analysis.

The Hitec HS-82MG is the preferred premium alternative where increased weight is acceptable in exchange for improved documentation, long-term support, and proven reliability.

## Brushless Motor Evaluation

| Attribute | T-Motor F90 1300KV | EMAX ECO II 2807 1300KV | FlyFishRC Flash 2806.5 1350KV |
|----------|---------------------|---------------------------|--------------------------------|
| Preliminary Rank | Best | Better | Okay |
| Status | Provisional | Provisional | Provisional |
| Motor Class | 2806.5 | 2807 | 2806.5 |
| KV | 1300KV | 1300KV | 1350KV |
| Intended Voltage | Manufacturer: 5–6S; Flightory: 4S | 4–6S, subject to source verification | 4–6S, subject to source verification |
| MP-1 Voltage | 4S | 4S | 4S |
| Weight | 46.6 g including leads | To verify | To verify |
| Internal Resistance | 76 mΩ | To verify | To verify |
| Propeller Envelope | 7-inch | 7-inch | 7-inch |
| Peak Current | 45.1 A for 60 s at published test condition | To verify | To verify |
| Published Power | 1,059 W for 60 s at published test condition | To verify | To verify |
| LARK-Specific Evidence | Direct | None identified | None identified |
| Similar-Aircraft Evidence | Strong | Strong | Limited |
| Manufacturer Documentation | Strong | Moderate | Moderate |
| Independent Testing | Available | Available | Limited |
| Engineering Confidence | High | Medium | Low–Medium |

### Preliminary Motor Recommendation

The T-Motor F90 1300KV is the current Best candidate because it is the direct Flightory LARK reference motor and has the strongest documented relationship to the intended MP-1 configuration.

The EMAX ECO II 2807 1300KV is the current Better candidate because it offers comparable geometry and strong value, with published use by Flightory on related aircraft.

The FlyFishRC Flash 2806.5 1350KV is the current Okay candidate because it appears electrically and mechanically plausible, but currently lacks equivalent fixed-wing and LARK-specific evidence.

These rankings are provisional and should not be interpreted as final procurement approval until manufacturer specifications, independent thrust data, reliability evidence, and availability have been fully compared.
