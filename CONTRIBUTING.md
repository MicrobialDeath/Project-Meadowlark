# Contributing to Project Meadowlark

Thank you for contributing to Project Meadowlark.

The goal of this repository is to produce engineering work that another person can understand, reproduce, and improve.

The project values clear documentation and repeatable engineering over unnecessary process.

---

# Guiding Principles

Every contribution should improve at least one of the following:

- Technical accuracy
- Safety
- Reproducibility
- Clarity
- Maintainability
- Test evidence

If a change does not improve one of those areas, reconsider whether it belongs in the repository.

---

# Before You Make Changes

Before making significant changes:

1. Read the repository `README.md`.
2. Read the relevant platform documentation.
3. Understand the current design before proposing a new one.
4. Search for existing documentation to avoid duplication.

---

# One Authoritative Source

Each topic should have one authoritative home.

| Topic | Primary Document |
|-------|------------------|
| Project overview | `README.md` |
| Platform overview | `docs/platforms/mp-1/README.md` |
| System design | `design.md` |
| Component selection | `components.md` |
| Assembly and configuration | `build.md` |
| Verification | `testing.md` |
| Major engineering decisions | `decisions.md` |
| Test records and logs | `evidence/` |

Avoid copying the same information into multiple files.

---

# Documentation Style

Write for the next engineer.

Prefer:

- Clear language
- Short sections
- Descriptive headings
- Tables where appropriate
- Explicit assumptions
- Measured values instead of estimates when available

Avoid:

- Marketing language
- Unnecessary jargon
- Repeating the same information
- Process for its own sake

When information is uncertain, say so.

---

# Engineering Decisions

Record significant architectural or project decisions in:

```text
docs/platforms/mp-1/decisions.md
```

Each decision should briefly describe:

- The decision
- Why it was made
- Important consequences
- When it should be reconsidered

Do not create a new document for routine decisions.

---

# Components

Component selection belongs in:

```text
docs/platforms/mp-1/components.md
```

Record:

- Selected hardware
- Alternatives
- Remaining questions
- Compatibility concerns
- Verification still required

Do not duplicate component information in build or testing documents unless required for context.

---

# Building

Assembly, wiring, firmware installation, and configuration belong in:

```text
docs/platforms/mp-1/build.md
```

Build records for a specific aircraft belong under:

```text
docs/platforms/mp-1/evidence/
```

---

# Testing

Testing belongs in:

```text
docs/platforms/mp-1/testing.md
```

Record actual test results under:

```text
docs/platforms/mp-1/evidence/
```

Do not place raw logs or photographs inside the primary documentation files.

---

# Evidence

Engineering claims should be supported by evidence whenever practical.

Evidence may include:

- Flight logs
- Photographs
- Measurements
- Parameter files
- Mission files
- Build records
- Inspection records
- Ground-test reports
- Flight-test reports

Keep evidence organized so another person can understand what configuration produced it.

---

# Repository Organization

Add new top-level folders only when they solve a real organizational problem.

Prefer extending the existing structure before creating another one.

If a document becomes too large or covers multiple unrelated subjects, split it only after identifying clear ownership boundaries.

---

# Third-Party Material

Respect the licenses of third-party work.

Do not commit proprietary:

- CAD
- STL
- 3MF
- STEP
- Manuals
- Datasheets
- Software
- Design packages

unless redistribution is explicitly permitted.

Instead, document where the material can be obtained.

---

# Commit Messages

Use short, descriptive commit messages.

Examples:

```text
Simplify MP-1 documentation
Select reference propulsion system
Add initial waypoint test procedure
Document servo load testing
```

Avoid vague messages such as:

```text
Updates
Changes
Fix stuff
Misc
```

---

# Pull Requests

A good pull request should explain:

- What changed
- Why it changed
- Any assumptions made
- Any remaining open questions

Include screenshots or photographs when they help explain hardware changes.

---

# Questions

If documentation and implementation disagree:

1. Stop.
2. Determine which is correct.
3. Update the documentation or implementation.
4. Record the change if it materially affects the project.

The repository should describe the aircraft that actually exists—not the one we intended to build months ago.
