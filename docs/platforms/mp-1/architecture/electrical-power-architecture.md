# MP-1 Electrical Power Architecture

**Status:** Draft  
**Revision:** 0  
**Evidence Level:** E0 — Concept

## Purpose

This document defines the high-level electrical power architecture for the MP-1 platform. It identifies the major electrical subsystems, their relationships, and the current architectural assumptions.

Detailed component selection, electrical sizing, procurement decisions, test procedures, and verification results are documented separately.

## Scope

This document covers the high-level distribution of electrical power to:

- Propulsion
- Flight avionics
- Control surface servos
- Navigation equipment
- Radio Control (RC) equipment
- Telemetry equipment
- Sensors
- Future payloads
- Future Companion Computer (CC) equipment

This document does not yet define:

- Specific component models
- Connector types
- Wire gauges
- Fuse ratings
- Final voltage regulator selections
- Final protection strategy
- Detailed wiring harness design

## High-Level Architecture

```text
Battery
   │
   ├── Electronic Speed Controller (ESC)
   │        │
   │        ├── Brushless Direct Current (BLDC) Motor
   │        │
   │        └── Battery Elimination Circuit (BEC), if used
   │
   └── Power Module / Regulated Power Distribution
            │
            ├── Flight Controller (FC)
            │      ├── Radio Control (RC) Receiver
            │      ├── Global Navigation Satellite System (GNSS) Receiver
            │      ├── Telemetry Radio
            │      └── Sensors
            │
            ├── Servo Power Bus
            │      ├── Left Aileron Servo
            │      ├── Right Aileron Servo
            │      └── Elevator Servo
            │
            └── Reserved Expansion Power
                   ├── Companion Computer (CC)
                   └── Payload