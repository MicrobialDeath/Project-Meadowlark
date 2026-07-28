# Project Meadowlark

Project Meadowlark is an open engineering project focused on the design, development, verification, and documentation of autonomous fixed-wing aerial systems.

The project applies systems engineering principles to produce aircraft that are modular, maintainable, and thoroughly documented. Rather than focusing solely on building an aircraft, Meadowlark emphasizes creating a complete engineering record that supports repeatability, traceability, verification, and future platform evolution.

---

# Project Goals

Project Meadowlark aims to:

- Develop autonomous fixed-wing aircraft using sound engineering practices.
- Produce complete engineering documentation alongside implementation.
- Maintain traceability between requirements, architecture, analysis, verification, and engineering decisions.
- Design systems that can evolve across multiple aircraft platforms.
- Publish original engineering work as an open reference for others.

---

# Current Development Platform

The initial development platform is:

**Meadowlark Platform 1 (MP-1)**

MP-1 uses the Flightory LARK airframe as its physical reference platform while Meadowlark develops its own:

- Electrical architecture
- Avionics architecture
- Software architecture
- Verification procedures
- Engineering documentation
- System integration

The Flightory LARK serves only as the initial hardware platform and does not define the long-term architecture of Project Meadowlark.

---

# Repository Organization

The repository is organized into several major areas.

| Directory | Purpose |
|-----------|---------|
| `assets/` | Images, diagrams, logos, and other project assets |
| `docs/` | Engineering documentation |
| `hardware/` | Original hardware designs and manufacturing files |
| `references/` | Third-party reference documentation |
| `software/` | Source code and software tools |
| `tools/` | Templates and engineering utilities |

---

# Engineering Documentation

Engineering documentation is organized by platform.

Example:

```text
docs/
    program/
    platforms/
        mp-1/
```

Platform documentation includes:

- Architecture
- Requirements
- Analysis
- Interfaces
- Procurement
- Verification
- Engineering Decision Records (EDRs)

---

# Engineering Philosophy

Project Meadowlark follows several guiding principles.

- Engineering over documentation.
- Documentation supports engineering.
- Define before building whenever practical.
- Build capability in layers.
- Prefer evolution over replacement.
- Optimize for clarity.
- Record significant engineering decisions.
- Verify assumptions whenever practical.
- Design for future platforms without compromising the current platform.

---

# Engineering Standards

Project engineering standards are maintained separately under:

```text
docs/program/
```

These standards define:

- Documentation requirements
- Repository conventions
- Engineering workflow
- Evidence levels
- Source classifications
- Engineering Decision Record (EDR) process

---

# Repository Status

Project Meadowlark is currently in active early-stage engineering.

Current activities include:

- Repository establishment
- Engineering documentation
- MP-1 systems architecture
- Component evaluation
- Electrical system design

---

# Licensing

Unless otherwise noted, original Project Meadowlark documentation and software are released under the repository license.

Third-party documentation remains the property of its respective owners.

Project Meadowlark does **not** redistribute proprietary aircraft designs, CAD models, printable files, or other protected intellectual property belonging to third parties.

---

# Acknowledgements

Project Meadowlark recognizes and appreciates the work of the open-source and maker communities whose tools, documentation, and research make projects such as this possible.

Third-party products and documentation referenced within this repository remain the intellectual property of their respective owners.