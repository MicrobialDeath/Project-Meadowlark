# Development and Data Infrastructure

**Status:** Active

## Purpose

This document records the Project Meadowlark development, data-management, remote-access, and backup workflow.

It is intentionally separate from MP-1 aircraft hardware documentation. Aircraft component selection remains authoritative in `docs/platforms/mp-1/components.md`.

---

# System Roles

## SamsungLaptop

**Role:** Primary development workstation and field Ground Control Station (GCS)

Baseline:

- Windows 11
- Visual Studio Code (VS Code)
- Git
- Mission Planner
- Tailscale
- Syncthing
- Dropbox client/account access as needed

Primary local Git working copy:

```text
C:\Meadowlark\repo\Project-Meadowlark
```

Primary field-data root:

```text
C:\Meadowlark\field-data
```

Field-data directories:

```text
analysis/
battery/
flight-logs/
gps/
missions/
parameters/
sitl/
telemetry/
```

The Samsung local repository is the normal editing location for Project Meadowlark.

---

## Heimdall

**Role:** Central engineering/data server and secondary Git working copy

Platform:

- Raspberry Pi 5
- Ubuntu 24.04 LTS
- 1 TB NVMe storage
- Tailscale
- Syncthing
- Git
- rclone

Primary project root:

```text
/srv/meadowlark/
```

Structure:

```text
/srv/meadowlark/
├── repo/
│   └── Project-Meadowlark/
├── data/
│   ├── analysis/
│   ├── battery/
│   ├── flight-logs/
│   ├── gps/
│   ├── missions/
│   ├── parameters/
│   ├── sitl/
│   └── telemetry/
├── evidence/
└── backups/
    └── logs/
```

Heimdall is not the primary day-to-day editing location for the Git repository.

---

## GitHub

**Role:** Authoritative remote version-control repository

Repository:

```text
MicrobialDeath/Project-Meadowlark
```

Normal development workflow:

```text
Samsung local repository
        ↓ commit + push
GitHub main branch
        ↓ nightly safe update
Heimdall repository
```

GitHub is the synchronization point for repository content. Syncthing does not synchronize Git repositories.

---

## Dropbox

**Role:** Off-site backup target

Dropbox destination:

```text
Project Meadowlark Backup/
├── data/
└── repository/
```

Dropbox is not part of the live Git or Syncthing workflow. It receives backup copies from Heimdall through rclone.

---

# Remote Access

Tailscale provides the private network path between SamsungLaptop and Heimdall.

Heimdall Tailscale identity:

```text
heimdall
100.69.251.61
```

SamsungLaptop can reach Heimdall over home Wi-Fi, Starlink, phone hotspot, or another internet connection.

Typical Secure Shell (SSH) access:

```text
ssh rhandrews@100.69.251.61
```

VS Code Remote - SSH is configured for Heimdall, but the normal Meadowlark editing workflow uses the local Samsung repository.

---

# Field-Data Synchronization

Syncthing continuously synchronizes:

```text
SamsungLaptop
C:\Meadowlark\field-data
        ↕
Heimdall
/srv/meadowlark/data
```

The shared folder ID is:

```text
meadowlark-field-data
```

Both endpoints use **Send & Receive** mode.

Heimdall uses **Staggered File Versioning** with a maximum age of **365 days**. Previous versions are retained under:

```text
/srv/meadowlark/data/.stversions
```

The Syncthing marker directory is:

```text
/srv/meadowlark/data/.stfolder
```

Operational data such as telemetry, flight logs, mission files, parameter snapshots, battery data, GPS data, analysis output, and simulation results should use this path rather than Git unless a specific artifact is intentionally promoted into version-controlled evidence.

---

# Nightly Automation

## Git update

At **01:50 local time**, Heimdall runs:

```text
meadowlark-git-update.timer
```

The update process:

1. Requires the Heimdall repository working tree to be clean.
2. Fetches `origin` from GitHub.
3. Updates `main` using a fast-forward-only merge.
4. Aborts instead of forcing or automatically merging unexpected local changes.

Script:

```text
/srv/meadowlark/backups/meadowlark-git-update.sh
```

Logs:

```text
/srv/meadowlark/backups/logs/meadowlark-git-update-YYYY-MM-DD.log
```

---

## Dropbox backup

At **02:00 local time**, Heimdall runs:

```text
meadowlark-backup.timer
```

The backup copies:

```text
/srv/meadowlark/data
    → Dropbox/Project Meadowlark Backup/data

/srv/meadowlark/repo/Project-Meadowlark
    → Dropbox/Project Meadowlark Backup/repository
```

The backup uses `rclone copy`, not `rclone sync`.

This is intentional: files already present in Dropbox are not automatically deleted merely because they disappear from Heimdall.

The live Syncthing `.stfolder` marker is excluded from Dropbox backup. Syncthing `.stversions` recovery history is included.

Script:

```text
/srv/meadowlark/backups/meadowlark-backup.sh
```

Logs:

```text
/srv/meadowlark/backups/logs/meadowlark-backup-YYYY-MM-DD.log
```

Both timers use persistent systemd scheduling so a missed scheduled run can execute after Heimdall returns online.

---

# Data-Handling Rule

Use the following rule when deciding where Meadowlark material belongs.

## Git / GitHub

Use Git for intentional project records such as:

- Design documents
- Component selections
- Engineering decisions
- Build instructions
- Test procedures
- Scripts and software
- Configuration files intentionally placed under version control
- Curated verification evidence

## Field Data / Heimdall

Use the Syncthing/Heimdall data path for generated or operational data such as:

- Raw telemetry
- Flight-controller logs
- Mission Planner logs
- Battery records
- GPS records
- Parameter snapshots
- Mission files
- Simulation output
- Analysis output

---

# Operating Workflow

Normal Project Meadowlark work should follow this pattern:

```text
Design / discussion
        ↓
Edit local Samsung Git repository in VS Code
        ↓
Review changes
        ↓
Commit and push to GitHub
        ↓
01:50 — Heimdall safely fast-forwards from GitHub
        ↓
02:00 — Heimdall repository and project data copied to Dropbox
```

Field-generated data follows a separate automatic path:

```text
Samsung field data
        ↓ Syncthing
Heimdall central data archive
        ↓ versioning + nightly rclone copy
Dropbox off-site backup
```

The aircraft and Ground Control Station should remain operational without depending on Heimdall, Dropbox, GitHub, Tailscale, or internet connectivity during a field session.

---

# Configuration Principle

Project infrastructure should remain simple, observable, and recoverable.

Automation must fail safely rather than overwrite local changes, force Git history, or propagate destructive deletion behavior into the off-site backup.
