# Installation

## System requirements

- **OS:** Windows 10 (x64) or Windows 11.
- **CPU:** 2 cores minimum, 4+ recommended.
- **RAM:** 4 GB minimum, 8 GB recommended.
- **Disk:** ~250 MB for the application, plus space for your project
  library.
- **Internet:** required for online activation; the application runs
  offline after activation, with an offline-grace window on
  subscription tiers.
- **Controller:** USB to a Marlin, GRBL, or GRBL-H-Par controller
  (auto-detected on connect). See [hardware.md](hardware.md).

## Installing

1. Download the installer from
   [foamsyncstudio.com/download](https://foamsyncstudio.com/download/).
2. Run the installer and follow the prompts. The default install path
   is `C:\Program Files\FoamSync` — change it if your IT policy
   requires.
3. Launch FoamSync. On first launch:
   - Accept the End User Licence Agreement.
   - The application enters trial mode automatically — 7 days of
     preview, output for evaluation, real machines run in virtual
     mode.

> [!NOTE]
> Trial mode runs the full feature set so you can evaluate every
> generator and the CAM pipeline. To connect a real machine and use
> the output in production, activate any paid tier
> ([activation.md](activation.md)).

## What gets installed

- `C:\Program Files\FoamSync\` — application files (read-only after
  install).
- `%USERPROFILE%\.foamsync\` — your user data:
  - `library/` — your saved scenes and parts.
  - `presets/` — material presets and calibration data.
  - `foamsync.log` — the application log.
  - `license.dat` — your licence file (created on activation).

User data is **not** removed on uninstall. Delete
`%USERPROFILE%\.foamsync\` manually for a clean wipe.

## Uninstall

Windows Settings → Apps → **FoamSync** → Uninstall.

## Multiple machines (Studio tier)

Studio tier grants three machine seats. Install on each machine
separately and activate each one (online, or with a licence file
issued against that machine's Machine ID).

## Next

- [Activation](activation.md)
- [Workflow](workflow.md)
