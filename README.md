# Projekt Organizer

A self-contained browser application for managing utility-planning projects (sessions), from initial data capture through processing, billing, and quality assurance.

**Version:** 1.1.0  
**Distribution:** single HTML file — no installation, no server, no account required.

A core design assumption is that the entire tool lives in **one file**: open it in a browser and start working. No setup wizard, no dependencies, no companion files to copy or keep in sync. The only optional extras are two small cursor images for a cosmetic UI preference — they are not required for any project functionality.

---

## Purpose

Projekt Organizer was built to **speed up day-to-day project work** in our team. Before this tool, project information, hour reports, billing figures, and workflow status were spread across spreadsheets, folders, and ad-hoc notes. That made it easy to lose context, repeat manual copy-paste, and lose track of where a session stood in the pipeline.

This application brings the essentials into one place:

- structured project and site (*Baustelle*) data  
- workflow checklists aligned with our internal process  
- time reporting (*Stundennachweis*) with predefined T 6.x positions  
- billing line items and cost calculation  
- one-click copy outputs for downstream tools (reports, Aufmaß, summaries)

The goal is simple: **less administrative overhead, more time on actual project work**, with a clear status for every open session.

---

## How it works

Projekt Organizer runs entirely in the browser. Open `project-organizer.html` in Chrome or Edge (recommended), create or select a project, and work in the tabbed editor. All changes are saved automatically to the browser’s local storage.

Projects can be exported to JSON for backup or transfer. Settings (time-report positions, default *Bearbeiter*, UI preferences) are stored separately and can also be exported/imported.

> **Important:** Browser storage is local to that browser on that computer. Export your projects regularly. Clearing site data or browser history can remove unsaved work.

---

## Features

### Project management

- Create projects with name and *Bearbeiter* (processor ID)
- Project list with pagination, sorting (by date, name, status), and overview statistics
- Status workflow with colour coding:
  - *in Bearbeitung* (in progress)
  - *abgerechnet* (billed)
  - *in QS* (in quality assurance)
  - *fertig nach QS* (completed after QS)
- Key dates: created, sent to QS, completed
- Rename project and *Bearbeiter* in place
- Project age indicator (warns when open sessions approach critical age)

### Multi-site support (*Baustelle*)

- One primary site plus additional *Baustellen* per project
- Each site has its own field set, checklists, hour rows, and cost rates
- Tabbed navigation between sites within a project

### Project data (*Allgemein*)

- Core identifiers: project number, location (*Ortschaft*), project folder, order number
- Automatic *Sparte* derivation from cable-length inputs
- Billing quantity fields with optional spreadsheet-style formulas (e.g. `=100+50-20`), stored per project and included in export

### Processing (*Bearbeitung*)

- Structured checklist covering cables, plant data, dimensions, labels, network files, operating plans, checklist spreadsheets, and billing documents
- Free-text notes for processing

### Billing (*Abrechnung*)

- Predefined billing positions (flat rates, length-based items, connection and node charges)
- Configurable unit rates per site
- Live cost calculation and project total
- **Stundennachweis** (time report): rows with date, position (T 6.x), description, hours, and processor
- Drag-and-drop row reordering, sort by date
- Copy to clipboard:
  - full time report
  - hours summary
  - Aufmaß L25 data block

### Corrections (*Korrektur*)

- Correction-phase checklist and notes

### Settings

- Default *Bearbeiter*
- Time-report configuration: T 6.x position codes, titles, and *Beschreibung* option lists
- UI: theme (6 colour schemes), language (Polish / German), tab icon, optional custom button cursor
- Factory defaults are embedded in the HTML; updated defaults reload on refresh when the built-in configuration changes

### Import / export

| Action | Description |
|--------|-------------|
| **Export projects** | Downloads all projects as JSON (`project-organizer-{BEARBEITER}-{date}.json`) |
| **Import projects** | Loads one or more JSON files; merge with conflict handling (skip or overwrite existing IDs) |
| **Export / import settings** | Separate JSON for time-report configuration only |

---

## Quick start

1. Open `project-organizer.html` in your browser.
2. Set your default *Bearbeiter* in **Settings** (gear icon).
3. Click **Create project**, enter the session name (e.g. project folder name).
4. Fill in project data, track checklist progress, and add time-report rows as you work.
5. Use **Export projects** periodically to save a backup JSON file.

---

## Requirements

- Modern browser (Chrome or Edge recommended)
- JavaScript enabled
- Optional: `cursor-cat-head.png` and `cursor-cat-paw.png` in the same folder — purely cosmetic; the app works fully without them

No network connection is required after the file is available locally. In practice, **`project-organizer.html` is all you need**.

---

## Repository contents

| File | Role |
|------|------|
| `project-organizer.html` | Complete application (markup, styles, logic, default configuration) |
| `cursor-cat-head.png`, `cursor-cat-paw.png` | Optional cursor assets |
| `README.md` | This document |

---

## Data privacy

All project data stays on the user’s machine inside the browser unless explicitly exported. There is no telemetry, cloud sync, or external API.

---

## Language

The interface is available in **Polish** and **German**, switchable from the header. Domain labels (*Bearbeiter*, *Baustelle*, *Stundennachweis*, etc.) follow the terminology used in our team’s German-language workflow.
