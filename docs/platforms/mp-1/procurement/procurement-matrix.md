# docs/platforms/mp-1/procurement/procurement-matrix.md

# Servo Evaluation Matrix

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
