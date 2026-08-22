# Calibrated Filament Profiles — Polymaker (PrusaSlicer)

## Purpose

This repository contains PrusaSlicer filament profiles for **Polymaker** filaments — including filament under the **Panchroma** and **Fiberon** product lines — calibrated and validated on the printers and hardware configuration described below. Each profile has been tuned through a structured calibration process rather than derived from manufacturer defaults alone, with the goal of providing print-ready, dimensionally accurate, and visually consistent results out of the box.

---

## Scope and Disclaimer

These profiles are tuned for the **exact hardware, nozzle diameter, and slicer version** listed below. Results may vary on different printer models, hotend types, nozzle diameters, or firmware versions. Users on different hardware should treat these profiles as a **starting point** and re-validate critical settings (first layer, flow, temperature) before production use.

---

## Testing Environment

### Printers

| # | Printer Model | Nozzle and Diameter | Notable Modifications |
|---|---|---|---|
| 1 | Prusa Core One+ | Brass — 0.4 mm Standard | MMU3 installed |
| 2 | Prusa MK4S | Brass CHT — 0.6 mm High Flow | Enclosure installed |
| 3 | Prusa MK4S | Brass CHT — 0.4 mm High Flow | Enclosure installed |

> **Note on printer naming:** PrusaSlicer's built-in system presets refer to printer 1 simply as "Core One" (no "+"). This repository uses "Core One / Core One+" interchangeably — testing was performed on a Core One+, and since it shares the same toolhead and nozzle system as the standard Core One, these profiles are expected to apply to both.

### Slicer

- **Software:** PrusaSlicer
- **Printer System Presets used as base:** Prusa Core One MMU3 0.4 Nozzle, Original Prusa MK4S HF0.6 Nozzle, Original Prusa MK4S HF0.4 Nozzle

### Build Environment

- **Room parameters:** Isolated, temperature-controlled room. Temperature held between 20–24°C during all prints. Room humidity kept below 25% at all times.
- **Filament parameters:** Filament stored in vacuum-sealed compartments with hygrometers confirming under 10% humidity. During printing, filament is held in temperature- and humidity-controlled filament dryers, confirming under 15% humidity.

---

## Filaments Tested

| Filament | Diameter |
|---|---|
| Panchroma CoPE | 1.75 mm |
| Panchroma Matte | 1.75 mm |
| Panchroma PLA | 1.75 mm |
| Panchroma Celestial | 1.75 mm |
| Polymaker HT-PLA | 1.75 mm |
| Polymaker PETG | 1.75 mm |

**Fiberon filaments** are part of the Polymaker product family and are **planned for future testing**. They are not yet covered by any profile in this repository — entries will be added here as calibration is completed.

---

## Calibration Methodology

Each filament profile was tuned using the following sequence of tests before being considered final:

1. **Temperature tower** — nozzle temperature range narrowed for layer adhesion, stringing, and surface finish.
2. **Flow rate / extrusion multiplier calibration** — single-wall or flow calibration cube used to correct under/over-extrusion.
3. **Pressure advance / linear advance** — tuned per filament on the firmware in use.
4. **Retraction tuning** — retraction distance and speed tuned against a stringing test object.
5. **Max flow rate / max volumetric speed** — upper bound validated per filament to avoid under-extrusion at speed.

---

## Slicer Print & Printer Settings

These profiles are built on top of PrusaSlicer's **built-in system presets** for print and printer settings — they are not custom files. Only the **filament `.ini` profiles** are included in this repository; select the corresponding print and printer settings from PrusaSlicer's system presets listed below.

**Print Settings (system preset):**
- `0.20mm SPEED @MK4S HF0.6`
- `0.20mm SPEED @MK4S HF0.4`
- `0.20mm SPEED @COREONE 0.4`

**Printer Settings (system preset):**
- `Original Prusa MK4S HF0.6 Nozzle`
- `Original Prusa MK4S HF0.4 Nozzle`
- `Prusa Core One MMU3 0.4 Nozzle`

---

## Repository Contents

Filament profiles are organized hierarchically — first by printer, then by nozzle, then by filament. Supporting evidence (test-print G-code and photos) is kept in a single `evidence/` folder per printer/nozzle combination, organized by filament:

```
/<Printer>/<Nozzle>/<Filament>/
/<Printer>/<Nozzle>/evidence/<Filament>/
```

For example:

```
/Core-One/0.4mm/Polymaker-PETG/
/Core-One/0.4mm/evidence/Polymaker-PETG/
/MK4S/0.6mm-HF/Polymaker-PETG/
/MK4S/0.6mm-HF/evidence/Polymaker-PETG/
/MK4S/0.4mm-HF/Polymaker-PETG/
/MK4S/0.4mm-HF/evidence/Polymaker-PETG/
```

Each filament folder contains the calibrated `.ini` profile and a changelog for that specific printer/nozzle/filament combination. The corresponding `evidence/<Filament>/` folder holds the G-code and photo used to validate that profile version.

---

## Versioning

Versioning is tracked **per filament profile**, not per printer or print-settings preset. Each profile follows a `vX` scheme:

- **X** — increments on a refinement to an existing calibration (temperature, flow, retraction, etc.)

The current version is noted in each profile's filename and tracked in a changelog alongside it.

---

## Community Contributions

Community-submitted improvements and additional calibrations for the filament vendors verified in this repository are welcome, and will be considered for merging as updated/versioned profiles.

To be considered, a submission **must** include all of the following:

1. **Identical hardware match** — same nozzle diameter and same printer model(s) as listed under [Testing Environment](#testing-environment). Submissions for different printers or nozzle sizes will not be merged into this profile set (feel free to fork instead).
2. **The filament profile file(s)** in the same slicer/version format used in this repository.
3. **The G-code file** used to produce the submitted test print, unedited.
4. **A clear photo** of the finished calibration/test print corresponding to the submitted G-code.
5. **A short summary** of what was changed from the base profile and why (e.g. "reduced hotend temp 5°C to reduce stringing on batch X").

Please open a pull request (GitHub) or a comment with linked files (Printables) to submit. In order to maintain a set standard and consistancy, all submissions will be tested and validated based on filament availability before being added to the listing.

---

## Printables Link

https://www.printables.com/model/1801353-calibrated-filament-profiles-polymaker-panchroma-f

---

## License

This work is licensed under [**CC BY-SA 4.0**](https://creativecommons.org/licenses/by-sa/4.0/) (Attribution-ShareAlike 4.0 International).

You are free to use, modify, and redistribute these profiles, including for commercial purposes, provided that:
- appropriate credit is given, and
- any derivative profiles are distributed under this same license.

By submitting a contribution under [Community Contributions](#community-contributions), you agree it will be distributed under this same CC BY-SA 4.0 license.

## Attribution

Maintained by raporter1992. Not affiliated with Polymaker or Prusa Research.
