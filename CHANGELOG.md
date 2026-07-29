# Changelog

All notable changes to Project Meadowlark are documented in this file.

The project follows a simple philosophy: record meaningful engineering and documentation milestones rather than every minor edit.

---

## Unreleased

### Documentation

- Continue development of the MP-1 engineering documentation.
- Continue hardware selection and verification.
- Prepare the repository for the first physical aircraft build.

---

## 2026-07 — Documentation Restructure

### Added

- Established a dedicated documentation structure for Meadowlark Platform 1 (MP-1).
- Defined clear ownership for architecture, hardware, build procedures, testing, and engineering decisions.
- Added repository-wide documentation principles emphasizing reproducibility and maintainability.
- Added a third-party reference section for the Flightory LARK airframe.

### Changed

- Simplified the repository structure to reflect the current state of the project.
- Reorganized MP-1 documentation into focused documents:
  - `README.md`
  - `design.md`
  - `components.md`
  - `build.md`
  - `testing.md`
  - `decisions.md`
- Converted internal document references to Markdown links.
- Clarified the boundary between project documentation and third-party material.
- Standardized document formatting, terminology, and cross-references.

### Removed

- Duplicate documentation across multiple files.
- Placeholder-only directories that did not yet contain project artifacts.
- Obsolete documentation structure and legacy organizational content.

### Documentation Philosophy

The repository now follows these principles:

- One authoritative source for each topic.
- Architecture, hardware, assembly, testing, and decisions are documented separately.
- Evidence is recorded independently from primary documentation.
- Documentation describes the aircraft that exists rather than planned future implementations.
- New directories and documents are introduced only when justified by project needs.

---

## Earlier Development

Before the July 2026 documentation restructure, the repository was in active planning and organization while the initial MP-1 baseline architecture and component evaluation were being established.

Historical details prior to the restructuring were intentionally consolidated into the entries above to keep the changelog focused on significant milestones rather than incremental editing activity.
