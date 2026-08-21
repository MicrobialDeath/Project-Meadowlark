# Development and Data Infrastructure

**Status:** Active

## Purpose

This document records the Project Meadowlark development, data-management, remote-access, media-ingestion, and backup workflow.

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
build-media/
flight-logs/
gps/
missions/
parameters/
sitl/
telemetry/
```

The Samsung local repository is the normal editing location for Project Meadowlark.

---

## iPhone

**Role:** Primary field/build media capture device

Photos, screenshots, videos, and other selected build media can be uploaded directly to the human-facing Dropbox intake location:

```text
Project Meadowlark/
└── Build Media/
    └── Inbox/
```

The iPhone does not need direct access to Heimdall for media ingestion. Dropbox acts as the intake handoff point.

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
│   ├── build-media/
│   │   └── inbox/
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

Authorized project updates may also be committed directly to GitHub through the connected project tooling. The Samsung working copy should pull/synchronize those changes before local editing resumes.

GitHub is the synchronization point for repository content. Syncthing does not synchronize Git repositories.

Raw build media should not be automatically committed to Git. Only deliberately selected media that supports the engineering record should be promoted into version-controlled evidence.

---

## Dropbox

**Roles:** Human-facing media intake and machine-managed off-site backup

Human-facing workspace/intake:

```text
Project Meadowlark/
└── Build Media/
    └── Inbox/
```

Machine-managed backup destination:

```text
Project Meadowlark Backup/
├── data/
└── repository/
```

These locations serve different purposes:

- `Project Meadowlark/` is an interactive workspace and intake area that may be used from devices such as the iPhone.
- `Project Meadowlark Backup/` is managed by Heimdall backup automation and should generally not be edited manually.

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

Operational data such as telemetry, flight logs, mission files, parameter snapshots, battery data, GPS data, build media, analysis output, and simulation results should use this path rather than Git unless a specific artifact is intentionally promoted into version-controlled evidence.

---

# Build Media Intake

Build media includes photographs, screenshots, videos, screen recordings, and other visual records produced during fabrication, assembly, integration, and testing.

The complete media archive belongs in the data system rather than the Git repository.

## Capture and intake path

The normal iPhone workflow is:

```text
iPhone
    ↓ selected media uploaded to Dropbox
Dropbox/Project Meadowlark/Build Media/Inbox
    ↓ hourly rclone copy
Heimdall /srv/meadowlark/data/build-media/inbox
    ↕ Syncthing
Samsung C:\Meadowlark\field-data\build-media\inbox
```

The Dropbox-to-Heimdall operation uses `rclone copy`, not `rclone sync`.

This is intentional:

- Source files are not removed from the Dropbox Inbox after ingestion.
- Deleting an item from the Dropbox Inbox does not instruct the intake job to delete the Heimdall copy.
- Existing Heimdall media is not removed merely because it is absent from the Dropbox intake folder.

## Hourly automation

Heimdall runs:

```text
meadowlark-media-intake.timer
```

The timer executes hourly and invokes:

```text
meadowlark-media-intake.service
```

Script:

```text
/srv/meadowlark/backups/meadowlark-media-intake.sh
```

Logs:

```text
/srv/meadowlark/backups/logs/meadowlark-media-intake-YYYY-MM-DD.log
```

The systemd timer is persistent so a missed scheduled run can execute after Heimdall returns online.

## Media organization

The intake directory is a landing area, not necessarily the final organizational structure. Build media may later be organized by date and event, for example:

```text
build-media/
├── inbox/
└── archive/
    ├── YYYY-MM-DD-lark-print-progress/
    ├── YYYY-MM-DD-airframe-assembly/
    └── YYYY-MM-DD-avionics-fit-check/
```

Event folders may contain media-type subdirectories such as `photos/`, `screenshots/`, and `video/` when useful.

## GitHub promotion

GitHub should contain only curated build media that materially supports documentation, verification, or the progressive engineering record.

The intended evidence location is:

```text
docs/platforms/mp-1/evidence/build-media/
```

Large raw videos, duplicate photographs, alternate angles, failed-print documentation that has no continuing engineering value, and other bulk media should remain in the Heimdall/Dropbox archive rather than Git.

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

Because build media resides under `/srv/meadowlark/data`, ingested media is included automatically in the nightly off-site backup.

Script:

```text
/srv/meadowlark/backups/meadowlark-backup.sh
```

Logs:

```text
/srv/meadowlark/backups/logs/meadowlark-backup-YYYY-MM-DD.log
```

Both nightly timers use persistent systemd scheduling so a missed scheduled run can execute after Heimdall returns online.

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
- Selected build-media artifacts that materially support the engineering record

## Field Data / Heimdall

Use the Syncthing/Heimdall data path for generated, operational, or archival data such as:

- Raw telemetry
- Flight-controller logs
- Mission Planner logs
- Battery records
- GPS records
- Parameter snapshots
- Mission files
- Simulation output
- Analysis output
- Complete build-media archive

---

# Operating Workflow

Normal Project Meadowlark repository work should follow this pattern:

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

When an authorized change is made directly to GitHub, the Samsung working copy should pull/synchronize before local editing continues.

Field-generated data follows a separate automatic path:

```text
Samsung field data
        ↓ Syncthing
Heimdall central data archive
        ↓ versioning + nightly rclone copy
Dropbox off-site backup
```

Build media captured on the iPhone follows:

```text
iPhone
        ↓ upload selected media
Dropbox Project Meadowlark/Build Media/Inbox
        ↓ hourly non-destructive rclone copy
Heimdall build-media archive
        ↕ Syncthing
Samsung field-data copy
        ↓ nightly backup from Heimdall
Dropbox Project Meadowlark Backup/data
```

The aircraft and Ground Control Station should remain operational without depending on Heimdall, Dropbox, GitHub, Tailscale, or internet connectivity during a field session.

---

# Configuration Principle

Project infrastructure should remain simple, observable, and recoverable.

Automation must fail safely rather than overwrite local changes, force Git history, or propagate destructive deletion behavior into the off-site backup.
