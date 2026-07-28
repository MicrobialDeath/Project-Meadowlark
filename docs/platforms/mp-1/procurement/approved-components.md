# docs/platforms/mp-1/procurement/approved-components.md

## Flight Control Servos

### Primary Flight Servo

| Classification | Component | Status | Notes |
|---------------|-----------|--------|-------|
| Reference | Corona DS929MG | Approved | Closest match to the Flightory LARK reference design. Serves as the baseline servo for MP-1 engineering and verification. |
| Approved | EMAX ES08MD II | Approved | Acceptable digital metal-gear alternative. Electrical performance requires validation before becoming the reference component. |
| Preferred | Hitec HS-82MG | Approved | Premium alternative offering excellent documentation, proven aviation reliability, and readily available replacement parts. Recommended where the additional weight is acceptable. |

## Engineering Requirements

Approved servos should meet the following minimum requirements:

| Requirement | Target |
|-------------|---------|
| Operating Voltage | 4.8–6.0 V |
| Gear Material | Metal |
| Weight | ≤15 g preferred |
| Torque | ≥2.0 kg·cm @ 6 V |
| Stall Current | ≤1.5 A |
| Connector | Standard JR/Futaba compatible |
| Intended Use | Primary flight control surfaces |

## Brushless Motor

### Propulsion Motor

| Classification | Component | Status | Notes |
|---------------|-----------|--------|-------|
| Best Candidate | T-Motor F90 1300KV | Provisional | Direct Flightory LARK reference motor. Strongest current fit for weight, documented use, and 4S endurance operation. |
| Better Candidate | EMAX ECO II 2807 1300KV | Provisional | Strong value alternative with comparable geometry and Flightory use on related aircraft. |
| Okay Candidate | FlyFishRC Flash 2806.5 1350KV | Provisional | Plausible 4S 7-inch alternative, but currently supported by weaker fixed-wing and LARK-specific evidence. |

### Engineering Requirements

| Requirement | Target |
|-------------|--------|
| Motor Class | Approximately 2806.5–2807 |
| KV | Approximately 1300–1350KV |
| Battery Compatibility | 4S required; 3S compatibility desirable |
| Propeller Compatibility | 7×4 through 7×6 |
| Weight | Approximately 45–55 g preferred |
| Peak Current | Compatible with a 40–45 A ESC envelope |
| Intended Use | Long-endurance fixed-wing propulsion |
| Documentation | Published manufacturer specifications required |
| Independent Evidence | Published thrust or comparable-aircraft data strongly preferred |
