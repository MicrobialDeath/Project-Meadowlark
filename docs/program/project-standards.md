# Engineering Standards

This document defines the engineering standards governing Project Meadowlark.

Its purpose is to establish a consistent methodology for engineering development, documentation, repository organization, and technical decision-making.

All engineering work within this repository should conform to these standards unless an approved Engineering Decision Record (EDR) explicitly documents an exception.

---

# Guiding Principles

Project Meadowlark follows several fundamental principles.

1. Engineering precedes implementation.
2. Documentation is an engineering deliverable.
3. Significant decisions are recorded.
4. Requirements drive design.
5. Verification demonstrates compliance.
6. Simplicity is preferred over unnecessary complexity.
7. Every engineering artifact has a single authoritative source.

---

# Repository Philosophy

The repository is the authoritative engineering record for Project Meadowlark.

Engineering work should be reproducible from repository contents.

Repository organization should prioritize:

- Traceability
- Maintainability
- Readability
- Long-term evolution

Repository organization should remain stable whenever practical.

---

# Repository Organization

```
Project-Meadowlark/

assets/
docs/
hardware/
references/
software/
tools/
```

Each directory has a defined purpose.

Engineering information should exist in only one authoritative location.

---

# Platform Organization

Engineering documentation is organized by platform.

Example:

```
docs/platforms/mp-1/
```

Each platform may contain:

- analysis
- architecture
- drawings
- edr
- interfaces
- procurement
- references
- requirements
- verification

Future platforms should follow the same structure whenever practical.

---

# Document Status

Engineering documents should indicate their current maturity.

Recommended status values are:

| Status | Meaning |
|---------|---------|
| Draft | Initial development |
| Review | Under technical review |
| Approved | Accepted baseline |
| Superseded | Replaced by a newer document |
| Archived | Retained for historical purposes |

---

# Document Header

Engineering documents should begin with the following metadata.

| Field | Description |
|--------|-------------|
| Title | Document title |
| Document ID | Unique identifier if applicable |
| Revision | Current revision |
| Status | Document status |
| Author | Primary author |
| Last Updated | Date of latest revision |

Not every document requires every field, but major engineering documents should follow this convention.

---

# Naming Conventions

Use:

- lowercase filenames
- hyphen-separated words
- descriptive names

Examples:

```
battery-system.md

power-distribution.md

edr-0003-flight-controller-selection.md
```

Avoid:

- spaces
- CamelCase
- vague filenames

---

# Markdown Standards

Use:

- ATX headings (`#`)
- fenced code blocks
- GitHub Markdown tables
- relative links

Avoid excessive formatting.

Clarity is preferred over decoration.

---

# Engineering Decision Records

Engineering Decision Records (EDRs) document significant technical decisions.

Each EDR should include:

- Decision
- Context
- Alternatives
- Rationale
- Consequences

EDRs are historical records.

Do not rewrite previous decisions.

If a decision changes, create a new EDR.

---

# Requirements Standards

Requirements should be:

- Necessary
- Unambiguous
- Testable
- Verifiable

Avoid subjective language.

Poor example:

> The aircraft should be lightweight.

Better example:

> Empty aircraft mass shall not exceed 1.8 kg.

---

# Verification Methods

Verification should identify how compliance will be demonstrated.

Preferred methods include:

- Inspection
- Analysis
- Demonstration
- Test

Whenever practical, verification evidence should be retained.

---

# Evidence Levels

Engineering information should be evaluated according to its confidence.

| Level | Description |
|---------|-------------|
| Verified | Confirmed through testing or direct measurement |
| Validated | Confirmed against authoritative documentation |
| Derived | Engineering conclusion based on verified information |
| Assumed | Working assumption pending confirmation |

Assumptions should be minimized and clearly identified.

---

# Source Classification

Engineering sources should be distinguishable.

Typical source categories include:

- Original Meadowlark engineering
- Manufacturer documentation
- Industry standards
- Academic literature
- Regulatory publications
- Community references

Whenever practical, original sources should be preferred over secondary summaries.

---

# Repository Assets

Repository assets should be categorized appropriately.

| Directory | Contents |
|-----------|----------|
| assets | Images, logos, diagrams |
| hardware | Original mechanical designs |
| software | Source code |
| references | Third-party reference material |
| tools | Templates and utilities |

Generated artifacts should not replace original engineering sources.

---

# Review Process

Major engineering documents should undergo technical review before being considered approved.

Review should evaluate:

- Technical correctness
- Internal consistency
- Traceability
- Completeness
- Clarity

---

# Change Management

Engineering documents evolve through controlled revisions.

Significant architectural changes should:

1. Update affected documents.
2. Record new engineering decisions.
3. Preserve historical traceability.
4. Identify superseded material where appropriate.

---

# Continuous Improvement

Engineering standards are expected to evolve.

Changes to this document should be infrequent, deliberate, and justified.

Whenever possible, repository-wide standards should be modified here rather than duplicated throughout individual engineering documents.