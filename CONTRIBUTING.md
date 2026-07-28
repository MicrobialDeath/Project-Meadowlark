# Contributing to Project Meadowlark

Thank you for your interest in Project Meadowlark.

Project Meadowlark is an engineering project first and an open-source software project second. Contributions are expected to meet the same standards of technical rigor, documentation quality, and traceability applied throughout the repository.

This document defines the engineering and repository conventions used by the project.

---

# Engineering Principles

All contributions should support the following principles:

- Engineering before implementation.
- Documentation accompanies design.
- Design decisions should be traceable.
- Requirements drive implementation.
- Verification demonstrates compliance.
- Simplicity is preferred over unnecessary complexity.
- Clear documentation is part of the engineering deliverable.

---

# Repository Organization

The repository is organized into major engineering domains.

```text
assets/
docs/
hardware/
references/
software/
tools/
```

Each directory has a specific purpose and should not be used as general storage.

---

# Documentation Standards

Engineering documentation is written in Markdown unless another format is specifically required.

Documents should:

- Use clear section headings.
- Be technically precise.
- Avoid unnecessary duplication.
- Reference authoritative sources where appropriate.
- Clearly distinguish facts, assumptions, and future work.

Whenever practical, documents should answer:

- What problem is being solved?
- Why was this approach selected?
- What alternatives were considered?
- How can the decision be verified?

---

# Naming Conventions

Use lowercase filenames.

Separate words with hyphens.

Examples:

```text
project-standards.md
power-system-architecture.md
edr-0004-flight-controller-selection.md
```

Avoid spaces in filenames.

---

# Repository Structure

Repository organization should remain stable.

Major engineering information belongs in only one authoritative location.

Avoid creating duplicate documentation covering the same subject.

---

# Engineering Decision Records (EDRs)

Significant engineering decisions should be documented as Engineering Decision Records.

Each EDR should include:

- Decision
- Context
- Alternatives Considered
- Rationale
- Consequences

EDRs are immutable historical records.

If a later decision supersedes an earlier one, create a new EDR rather than rewriting history.

---

# Requirements

Requirements should be:

- Necessary
- Testable
- Verifiable
- Unambiguous

Avoid vague language such as:

- Better
- Faster
- Improved
- Reasonable

Prefer measurable statements whenever possible.

---

# Verification

Engineering work should include a method of verification whenever practical.

Verification may include:

- Inspection
- Analysis
- Demonstration
- Test

Verification evidence should be retained whenever practical.

---

# Source Classification

Information used within the project should be distinguishable by origin.

Examples include:

- Original engineering work
- Manufacturer documentation
- Industry standards
- Academic publications
- Community references

Third-party reference material should remain within the `references/` directory whenever possible.

---

# Markdown Standards

Use:

- ATX headings (`#`)
- Fenced code blocks
- Tables where appropriate
- Relative links within the repository

Avoid excessive formatting that reduces readability.

---

# Commit Message Conventions

Commit messages should clearly describe the engineering change.

Preferred examples:

```text
docs: establish MP-1 repository structure

docs: add electrical architecture overview

feat: implement telemetry parser

fix: correct battery connector specification

refactor: reorganize platform documentation
```

Avoid vague messages such as:

```text
Update

Changes

Misc

Stuff
```

---

# Pull Requests

Pull requests should:

- Have a clearly stated purpose.
- Include supporting documentation where applicable.
- Reference affected engineering documents.
- Preserve repository organization.
- Avoid unrelated changes.

---

# Licensing

Contributors are responsible for ensuring they have the right to contribute any submitted material.

Do not contribute proprietary documentation, copyrighted engineering drawings, or other protected material without permission.

---

# Engineering Standards

Detailed engineering standards are maintained separately under:

```text
docs/program/
```

Repository-wide engineering conventions should be updated there rather than duplicated across multiple documents.

---

# Questions

If you are uncertain where new work belongs, or whether a proposed change aligns with the project's engineering philosophy, open a discussion before implementing significant structural changes.

Maintaining a consistent engineering repository is considered part of the project's design process.