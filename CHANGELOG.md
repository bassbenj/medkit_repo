# MEDKIT Changelog

All notable changes to MEDKIT are documented here.

---

## v1.4 — Stage 3: Import Merge + Conflict Resolution
*Current release*

### Added
- **Import preview dialog** — selecting a file now shows a full preview: incoming company name, tag, export date, and record counts before any data is changed.
- **Overwrite / Merge choice** — two clearly presented options with descriptions. Overwrite replaces everything (existing behavior). Merge combines records intelligently.
- **Merge engine** — full merge logic:
  - Different company tags → clean merge, entire structure moves in with no conflict check
  - Same company tag → timestamp-based resolution, newer `last_modified` wins
  - New records from import → added to local database
  - Existing records where local is newer → kept unchanged
- **Merge log** — real-time log shown during merge showing every added, updated, skipped, and conflicted record with color coding.
- **Conflict resolution modal** — when same ID + different name detected, a step-by-step modal shows both versions side by side with timestamps. Superadmin selects which version to keep. Merge cannot complete until all conflicts are resolved.
- **Skip conflict** — option to skip a conflict and keep local record.
- **Additional Items merge behavior** — incoming additional items are tagged with source company tag and core flag is stripped. Receiving Superadmin can manually re-flag as core.
- **Local identity protected** — Superadmin PIN, company name, and company tag are always preserved from local database during any merge. Import can never overwrite these.

### Changed
- Import button in System tab now triggers the new preview flow
- Export reference to "coming in v1.4" updated

## v1.3 — Stage 2: Company Setup + Timestamps
*Current release*

### Added
- **First-time setup screen** — on fresh install, Superadmin sets company name, company tag (2–6 chars), and PIN before accessing the system. Cannot be skipped. Cannot be changed after setup.
- **Company tag auto-prefix** — all new individual and group IDs are automatically prefixed with the company tag (e.g. `FOG-001`). Prefix is applied even if the user types a bare number.
- **Company name display** — shown in amber in the sidebar below the MEDKIT logo after login.
- **`last_modified` timestamps** — every create and edit operation on individuals, groups, kit states, pharma states, and training states now records an ISO timestamp. Foundation for merge logic in v1.4.
- **`db_version` field** — tracks database schema version for migration purposes.
- **Silent DB migration** — on first open of v1.3, existing v1.1/v1.2 databases are automatically upgraded with new fields. No data loss. No user action required.
- **Export metadata** — exported JSON now includes `_export_meta` with company name, tag, export timestamp, and record counts. Export filename now includes company tag: `medkit_FOG_2026-03-18.json`.
- **Import preview dialog** — selecting a file now shows incoming company, record counts, and export date before committing. Overwrite only for now.
- **System tab** — now shows company identity card and database summary alongside export/import controls.

### Changed
- Import button now triggers preview flow instead of immediate overwrite

---

## v1.2 — Stage 1: Water Scenario + Additional Items
### Added
- **Water / Sea / River scenario module** — added to all kit levels. Light version on individual IFAK and CivFA Kit (whistle, waterproof tape, near-drowning card, etc.). Full version on Fire Team, Squad, and Section (throwline, O2, traction splint, hypothermia station, coast guard contacts, etc.).
- **Additional Items section** — permanent named section at the bottom of every kit level and the pharma panel. Superadmin managed. Each item can be optionally flagged as core to count toward the progress bar.
- **Pharma Additional Items** — same section in the pharma panel with full drug fields (brand, use, adult/pediatric dose, tier designation).
- **Company tag pill** — displayed on each additional item showing the originating company (populated from v1.3 onward).
- **Progress bar includes additional core items** — kit and pharma progress bars now count additional items flagged as core by Superadmin.

### Fixed
- **Superadmin IFAK/CivFA progress bar** — Superadmin kit states now stored in dedicated `sa_kit` key. Previously always returned empty, making progress bars appear broken for Superadmin.
- **Extra items missing tag** — tag field was not being saved when Superadmin added extra kit items in v1.1.

---

## v1.1 — Core System Expansion
### Added
- **Tag system** — one tag per item across all kits and pharma. 18 tag categories with color-coded pills.
- **Filter bars** — kit filter and pharma filter are independent on individual pages. Group kits have their own kit filter. Filter shows only populated tags.
- **Two-column layout** — individual IFAK and Civilian FA Kit pages split into kit checklist (left) and pharmaceutical panel (right).
- **Pharmaceutical panel** — Tier 1 OTC core, Tier 1 OTC additional, Tier 1b Topical core, Tier 1b Topical additional, Tier 2 Rx (reference only). One shared state per individual — checking on IFAK page reflects on CivFA page.
- **Shared pharma progress bar** — one combined bar counting Tier 1 OTC core + Tier 1b Topical core.
- **Section 4 — Protocols & Mnemonics** — 12 protocol cards across 6 categories. Filter: ALL / TACTICAL / CIVILIAN. Split cards (side-by-side) for different protocols. Shared cards (one box) for identical protocols. Printable.
- **Section reorder** — Protocols moved to Section 4, SAR to Section 5, Sourcing to Section 6.

### Changed
- Civilian FA Kit — removed OTC meds, antibiotic ointment, ORS (moved to pharma panel)
- Group kits — OTC medications pack replaced with deployment reminder note
- IFAK hiking scenario — removed Diamox, glucose gel, electrolytes (moved to pharma)
- Content area widened to accommodate two-column layout

---

## v1.0 — Initial Release
### Features
- Single offline HTML file — no server, no installation, no internet required
- Role hierarchy: Superadmin → Admin → Team Lead → Individual
- Group hierarchy: Section → Squad → Fire Team → Individual
- Individual IFAK checklist with progress bar (core items only)
- Civilian FA Kit checklist with progress bar (all items)
- Group kit checklists — Fire Team, Squad, Section (no progress bar)
- Scenario modules — Fire/Burn, Tactical/War, Street/Road, Mountain/Hiking
- Civilian Training pathway — Tier 1 to Tier 4 with progress bar (core items)
- AFP Reserve medical pathway — checklist only
- Med Professionals page — bridging recommendations
- Non-Medical Tools — Section 3
- Sourcing Guide — Section 4 (moved to Section 6 in v1.1)
- SAR Recommendations — Section 5
- Dark / Light mode with per-user preference
- Export / Import JSON
- Admin Command Panel — create/edit/archive individuals and groups
- Print support — kit pages and training pages
- Login: PIN or Individual ID
