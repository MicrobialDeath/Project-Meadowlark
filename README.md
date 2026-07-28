# Project Meadowlark

Project Meadowlark is an open engineering project dedicated to the design, development, verification, and documentation of autonomous fixed-wing aerial systems.

The project applies systems engineering principles to create aircraft that are modular, maintainable, extensible, and supported by complete engineering documentation. Rather than focusing solely on building an aircraft, Meadowlark emphasizes developing a comprehensive engineering record that supports repeatability, traceability, verification, and long-term evolution.

---

# Project Goals

Project Meadowlark aims to:

- Develop autonomous fixed-wing aircraft using disciplined systems engineering.
- Produce complete engineering documentation alongside implementation.
- Maintain traceability between requirements, architecture, analysis, verification, and engineering decisions.
- Create modular systems that can evolve across multiple aircraft platforms.
- Publish original engineering work as an open reference for others to learn from and build upon.

---

# Current Development Platform

The initial development platform is:

**Meadowlark Platform 1 (MP-1)**

MP-1 uses the Flightory LARK airframe as the initial reference aircraft while Project Meadowlark develops its own:

- Electrical architecture
- Avionics architecture
- Mechanical integration
- Software architecture
- Autonomous capabilities
- Verification procedures
- Engineering documentation
- System integration

The Flightory LARK serves as the physical development platform and does not define the long-term architecture of Project Meadowlark.

---

# Repository Organization

The repository is organized into major engineering domains.

| Directory | Purpose |
|-----------|---------|
| `assets/` | Images, diagrams, logos, and other project assets |
| `docs/` | Engineering documentation |
| `hardware/` | Original hardware designs and manufacturing files |
| `references/` | Third-party reference documentation |
| `software/` | Source code and supporting software |
| `tools/` | Engineering templates and utilities |

---

# Engineering Documentation

Engineering documentation is organized by platform.

Example:

```text
docs/
├── program/
└── platforms/
    └── mp-1/
```

Platform documentation includes:

- Analysis
- Architecture
- Drawings
- Engineering Decision Records (EDRs)
- Interfaces
- Procurement
- References
- Requirements
- Verification

Project-wide engineering governance and standards are maintained separately under:

```text
docs/program/
```

---

# Engineering Philosophy

Project Meadowlark is guided by the following principles:

- Engineering rigor takes priority over process for its own sake.
- Documentation is part of the engineering deliverable.
- Define before building whenever practical.
- Requirements drive design.
- Significant engineering decisions are documented.
- Verification demonstrates compliance.
- Build capability in layers.
- Prefer evolution over replacement.
- Design for future platforms without compromising the current platform.
- Maintain one authoritative source for every engineering artifact.

---

# Repository Status

Project Meadowlark is currently in active early-stage engineering.

Current efforts include:

- Repository governance
- Engineering documentation
- MP-1 systems architecture
- Component evaluation
- Electrical system design
- Software framework planning

---

# Licensing

Unless otherwise noted, original Project Meadowlark documentation and software are released under the repository license.

Third-party documentation, trademarks, aircraft designs, CAD models, and other intellectual property remain the property of their respective owners.

Project Meadowlark references third-party products only for engineering evaluation and interoperability.

---

# Contributing

Contributors are encouraged to review:

- `CONTRIBUTING.md`
- `docs/program/engineering-standards.md`

before submitting changes.

These documents define repository conventions, engineering workflow, documentation standards, and contribution expectations.

---

# Acknowledgements

Project Meadowlark recognizes the many individuals, organizations, and open-source communities whose research, tools, documentation, and software make projects like this possible.

Their work provides the foundation upon which new engineering knowledge can be developed and shared.
