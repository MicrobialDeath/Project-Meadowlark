# Project Meadowlark

Project Meadowlark is an open engineering project focused on building, testing, and documenting autonomous fixed-wing aircraft.

The project emphasizes practical engineering:

- Build a working aircraft
- Keep the design understandable
- Record important decisions
- Verify capability through testing
- Preserve enough information for another person to reproduce the work
- Add complexity only when a clear requirement justifies it

The current development platform is Meadowlark Platform 1 (MP-1).

---

## Meadowlark Platform 1

MP-1 uses the Flightory LARK as its initial reference airframe.

The baseline objective is to demonstrate:

- Manual takeoff
- Manual and stabilized flight
- Onboard waypoint mission execution
- Return-to-launch
- Immediate RC pilot takeover
- Manual landing
- Reliable flight logging

MP-1 is an engineering testbed, not a final production aircraft.

See the [MP-1 documentation](docs/platforms/mp-1/README.md) for current status, design, hardware selection, build instructions, testing, and engineering decisions.

---

## Repository Structure

```text
Project-Meadowlark/
├── README.md
├── CONTRIBUTING.md
├── CHANGELOG.md
├── LICENSE
├── docs/
│   └── platforms/
│       └── mp-1/
│           ├── README.md
│           ├── design.md
│           ├── components.md
│           ├── build.md
│           ├── testing.md
│           └── decisions.md
└── references/
    └── flightory-lark/
        └── README.md
```

Directories for assets, hardware, software, tools, and test evidence will be created when the project produces material that belongs in them.

---

## Documentation

The MP-1 documentation set is intentionally compact:

- [MP-1 overview](docs/platforms/mp-1/README.md)
- [Design](docs/platforms/mp-1/design.md)
- [Components](docs/platforms/mp-1/components.md)
- [Build](docs/platforms/mp-1/build.md)
- [Testing](docs/platforms/mp-1/testing.md)
- [Engineering decisions](docs/platforms/mp-1/decisions.md)

Build and test evidence will be stored under `docs/platforms/mp-1/evidence/` once records exist.

---

## Third-Party Material

Project Meadowlark uses third-party products, software, and reference designs.

Unless explicitly permitted by the applicable license, this repository does not redistribute proprietary aircraft design files, CAD, printable files, manuals, vendor documentation, or restricted technical drawings.

The Flightory LARK design must be obtained directly from Flightory and used according to its current licensing terms.

See the [Flightory LARK reference](references/flightory-lark/README.md).

---

## Contributing

Contributions should improve technical accuracy, safety, reproducibility, clarity, maintainability, or test evidence.

Before contributing, review [CONTRIBUTING.md](CONTRIBUTING.md).

---

## License

Original Project Meadowlark material is provided under the repository license unless otherwise noted.

See [LICENSE](LICENSE).

Third-party material remains subject to its original license and ownership.

---

## Acknowledgements

Project Meadowlark builds on the work of open-source software communities, aircraft designers, manufacturers, researchers, and individual builders.
