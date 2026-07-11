# Refrigeration Survey
**City Technical Solutions — Field Engineering Tool**

A self-contained mobile-first web app for conducting refrigeration system surveys in supermarkets and retail stores. Built as a single HTML file — no installation, no server, no internet required after loading.

---

## Overview

The survey covers three equipment categories across four markets (Malaysia, Singapore, Hong Kong, Australia). Each category supports multiple units per store, with a system type selector that adapts the survey structure to the site's actual configuration.

| Tab | Coverage |
|---|---|
| ❄ Chiller | Display cases, cool rooms, shared rack and condenser |
| 🧊 Freezer | Display cases, cool rooms, shared rack and condenser |
| 🫙 Ice Machine | Standalone ice makers (auto-configured) |

---

## Getting Started

1. Open `refrigeration_survey.html` in any modern browser (Chrome, Safari, Edge)
2. On mobile: tap **Share → Add to Home Screen** to install as a PWA
3. Fill in **Site Information** at the top
4. Select a tab (Chiller, Freezer, or Ice Machine)
5. Choose the **system type** — Centralised or Standalone
6. Tap **+ Add [unit]** to add units and begin the survey

No login required. Works fully offline once the page is loaded.

---

## System Types

### Centralised
One shared compressor rack and condenser serves multiple display cases. The survey structure reflects this:

```
+ Add Chiller unit    (repeating — one card per display case)
+ Add Cool Room       (repeating — one card per cool room)
Rack Info             (one set — shared for all units)
Condenser Info        (one set — shared for all units)
```

### Standalone
Each unit has its own built-in compressor and condenser (e.g. standalone chiller, standalone aircon, standalone cool room). Every unit card contains the full question set:

```
+ Add Chiller unit    → Chiller questions + Rack Info + Condenser Info
+ Add Cool Room       → Cool Room questions + Rack Info + Condenser Info
```

### Ice Machine
Ice machines are always standalone. The system type question is skipped — tap **+ Add Ice Machine** to start immediately.

---

## Question Sets

### Chiller / Freezer display case unit (13 items)
| # | Item | Type |
|---|---|---|
| 1 | Water leaking? | Yes/No/N/A |
| 2 | Door seals intact and airtight? | Yes/No/N/A |
| 3 | Anti-condensate heaters on timers? | Yes/No/N/A |
| 4 | Night blinds / closing fitted? | Yes/No/N/A |
| 5 | Chiller type | Select: Multideck / Island |
| 6 | Night blinds / closing type | Select: Curtain / Door / None |
| 7 | Temperature within specified range? | Yes/No/N/A |
| 8 | Defrosting type | Select: Hot Gas / Heat Element / Ambient |
| 9 | Defrost cycles per day | Select: 6 / 4 / 2 / Demand-controlled |
| 10 | Ice forming? | Yes/No/N/A |
| 11 | Fan motor type | Select: EC Fans / Fixed Speed / Direct Cool |
| 12 | Refrigerant control | Select: Solenoid / AKV(EEV) / TXV / Cap. tube |
| 13 | Drain pan condition | Select: Clean / Dirty |

### Cool Room unit (9 items)
| # | Item | Type |
|---|---|---|
| 1 | Door seals intact and airtight? | Yes/No/N/A |
| 2 | Door condition | Select: Good / Needs attention / Poor |
| 3 | Temperature within specified range? | Yes/No/N/A |
| 4 | Defrosting type | Select: Hot Gas / Heat Element / Ambient |
| 5 | Defrost cycles per day | Select: 6 / 4 / 2 / Demand-controlled |
| 6 | Ice forming? | Yes/No/N/A |
| 7 | Fan motor type | Select: EC Fans / Fixed Speed / Direct Cool |
| 8 | Refrigerant control | Select: Solenoid / AKV(EEV) / TXV / Cap. tube |
| 9 | Cold room door buzzer installed? | Yes/No/N/A |

### Rack Info (8 items — shared or per standalone unit)
| # | Item | Type |
|---|---|---|
| 1 | Number of compressors | Text |
| 2 | Refrigerant type | Select: R404a / R134a / R449a / R22 / Other |
| 3 | Compressor type | Select: Fixed Speed / VSD / Not Working |
| 4 | Compressor manager installed? | Yes/No/N/A |
| 5 | Pressure setting | Text |
| 6 | Refrigerant leak detector installed? | Yes/No/N/A |
| 7 | Low-side pressure | Text |
| 8 | High-side pressure | Text |

### Condenser Info (3 items — shared or per standalone unit)
| # | Item | Type |
|---|---|---|
| 1 | Number of fans | Text |
| 2 | Condenser fan motor type | Select: EC Fans / Fixed Speed / Static Condenser |
| 3 | Condenser coil condition | Select: Green / Amber / Red |

### Ice Machine unit (12 items)
| # | Item | Type |
|---|---|---|
| 1 | Ice machine operation | Select: Interval 2 / Interval 4 / On Demand / 24/7 |
| 2 | Temperature within specified range? | Yes/No/N/A |
| 3 | Ice forming correctly? | Yes/No/N/A |
| 4 | Water leaking? | Yes/No/N/A |
| 5 | Refrigerant type | Select: R404a / R134a / R449a / R22 / Other |
| 6 | Refrigerant control | Select: Solenoid / AKV(EEV) / TXV / Cap. tube |
| 7 | Refrigerant leak detector installed? | Yes/No/N/A |
| 8 | Condenser type | Select: Air-cooled / Water-cooled |
| 9 | Condenser fan motor type | Select: EC Fans / Fixed Speed / Static Condenser |
| 10 | Condenser coil condition | Select: Green / Amber / Red |
| 11 | Unit cleaned recently? | Yes/No/N/A |
| 12 | Water filter installed? | Yes/No/N/A |

---

## Per-Question Features

Every question row supports:

- **📷 Camera** — tap to capture a photo directly from the device camera or gallery. Thumbnail appears below the question. Tap thumbnail to view full size. Tap × to remove.
- **📝 Note** — tap to expand a text box for observations, measurements, or corrective actions specific to that question. The note icon highlights yellow when a note has been entered.

---

## Site Information

The collapsible site info panel captures:

- Survey reference number (auto-generated: `CFM-RF-YYYYMMDD-001`, editable)
- Store code, store name, store type, address
- Country (Malaysia / Singapore / Hong Kong / Australia)
- State / Region (country-aware dropdown — options change based on selected country)
- GPS location — tap **Get GPS** to capture coordinates; auto-fills Country and State/Region via OpenStreetMap reverse geocoding if internet is available at that moment
- Auditor name and company, audit date, site contact, average monthly bill
- General site notes

---

## Export

Tap **Export ▾** in the footer to choose:

| Option | Format | Use |
|---|---|---|
| Save as PDF | PDF | Final report — full survey with photo appendix |
| Save as CSV | .csv | One row per question per unit — for data analysis |
| Save as Excel | .xlsx | Site Info + Survey Detail + Summary sheets |
| Save as JSON | .json | Save progress to continue editing later |

### CSV / Excel structure (Survey Detail sheet)
Each row represents one question from one unit:

`Reference | Store | Date | Auditor | Country | State/Region | Section | System Type | Unit | Question | Answer | Note | Photos`

### Summary sheet (Excel only)
One row per unit showing Yes / No / N/A / Blank counts and total questions answered.

---

## Save and Resume

To save a survey in progress and continue later:

1. Tap **Export → Save as JSON**
2. A `.json` file is saved to your device (e.g. `CFM-RF-20260704-001-Giant_PJ.json`)
3. To resume: tap **Load** in the footer, pick the saved `.json` file
4. The full survey restores — units, answers, notes, site info

Multiple surveys can be saved as separate files. The tool has no built-in file library — manage files through your device's Files app or Downloads folder.

---

## Photo Appendix (PDF)

When exporting PDF, a photo appendix is automatically added at the end showing all captured photos at full size. Photos are arranged in a 2-column grid, up to 8 per page. Each photo is labelled:

```
Section | Unit name | Question text
e.g.  Chiller | Chiller 1 | Door seals intact and airtight?
```

---

## Dark / Light Mode

Tap the **☀/☽** button in the top-right corner to toggle between dark mode (default) and light mode. The preference is saved in the browser and restored on next load.

---

## Reference Numbers

Survey reference numbers follow the format `CFM-RF-YYYYMMDD-NNN` where NNN is a daily sequence counter. The counter auto-increments each time a new survey is started or reset. The reference is editable — tap the field in Site Information to change it.

---

## Market Support

| Country | State/Region options | Currency hint |
|---|---|---|
| Malaysia | 16 states and federal territories | RM |
| Singapore | 5 planning regions | S$ |
| Hong Kong | 18 districts | HK$ |
| Australia | 6 states + 2 territories | A$ |

GPS auto-detect identifies the country and region automatically when internet is available at the time of capture. If offline, country and region can be selected manually — GPS coordinates are still captured either way.

---

## Technical Notes

- **Single file** — entire app is one `.html` file (~364 KB). No external dependencies except SheetJS (CDN, needed for Excel export only) and OpenStreetMap Nominatim (needed for GPS reverse geocoding only). All other features work offline.
- **No data is sent to any server** — all survey data stays on the device.
- **PWA** — installable on iOS and Android via Add to Home Screen.
- **Browser support** — Chrome, Safari, Edge (modern versions). File capture requires HTTPS or localhost on some browsers.
- **Excel export** requires an internet connection to load the SheetJS library from CDN. PDF and JSON export work offline.
- **JSON save/load** preserves all DOM state including photos (stored as base64). Large numbers of high-resolution photos will increase JSON file size significantly.

---

## Files

| File | Description |
|---|---|
| `refrigeration_survey.html` | Main application — open this file |
| `refrigeration_survey_README.md` | This document |

---

*City Technical Solutions — Internal field tool. Not for public distribution.*
