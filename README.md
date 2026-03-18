# MEDKIT — Field Medical System

A single-file offline medical readiness tracker for Filipino civilians, AFP reservists, volunteer organizations, and small tactical groups.

No installation. No server. No internet required. Open the HTML file in any browser.

---

## Quick Start

1. Download `MEDKIT.html`
2. Open it in any browser (Chrome, Firefox, Edge)
3. On first launch — complete the one-time setup (company name, tag, PIN)
4. Login with your Superadmin PIN (default: set during setup)

---

## How to Update

Always keep the file named `MEDKIT.html`. When a new version is released:

1. **Export your data first** — Command Panel → System → Export JSON. Save the backup.
2. Replace `MEDKIT.html` with the new version.
3. Open the new file — your data carries over automatically.
4. If data does not appear — use Import JSON to restore your backup.

> ⚠️ Never rename the file between versions. Data is stored per filename in the browser.

---

## Roles

| Role | Access |
|---|---|
| **Superadmin** | Full access. Company setup. Export/Import. Add items. |
| **Admin** | Manage individuals and groups. View all progress. |
| **Team Lead** | Tick group kit checklists. |
| **Individual** | Own IFAK, CivFA Kit, Pharma, Training checklists. |
| **Guest** | Civilian kit, pharma, protocols, sourcing — session only, nothing saved. |

---

## Login Methods

- **PIN login** — Enter your assigned PIN
- **Individual ID login** — Enter your ID directly (no PIN needed if no PIN set)
- **Continue as Guest** — Coming in v1.4

Default Superadmin PIN: set during first-time setup.

---

## Structure

```
Section (15–20 persons)
└── Squad / Unit (7–12 persons)
    └── Fire Team / Element (2–5 persons)
        └── Individual
            ├── IFAK Checklist
            ├── Civilian FA Kit
            ├── Pharmaceutical Kit
            └── Training Checklist
```

Groups must be created before assigning individuals. Individuals can exist without a group assignment.

---

## Kit Sections

Each kit level contains:

| Section | Description |
|---|---|
| **Core** | Required items — count toward progress bar |
| **Fire / Burn** | Burn and fire incident add-ons |
| **Tactical / War** | Combat and active threat add-ons |
| **Street / Road** | Vehicle accident add-ons |
| **Mountain / Hiking** | Trail and wilderness add-ons |
| **Water / Sea / River** | Water incident add-ons — light for individual, full for groups |
| **Additional Items** | Unit-specific items added by Superadmin. Can be flagged as core. |

---

## Pharmaceutical Panel

Appears on Individual IFAK and Civilian FA Kit pages. One shared checklist per person — checking an item on one page reflects on the other.

| Tier | Description |
|---|---|
| **Tier 1 OTC — Core** | Standard over-the-counter medications. Count toward progress bar. |
| **Tier 1 OTC — Additional** | Optional OTC add-ons. |
| **Tier 1b Topical — Core** | Standard topical medications. Count toward progress bar. |
| **Tier 1b Topical — Additional** | Optional topical add-ons. |
| **Tier 2 Rx** | Prescription only — reference list, no checkboxes. |
| **Additional Items** | Unit-specific pharma added by Superadmin. Can be flagged as core. |

---

## Progress Bars

| Kit | What counts |
|---|---|
| IFAK | Core items + Additional Items flagged as core |
| Civilian FA Kit | Core items + Additional Items flagged as core |
| Pharmaceutical | Tier 1 OTC core + Tier 1b Topical core + Additional Items flagged as core |
| Civilian Training | Core-flagged training items per tier |
| Group kits | No progress bar |

---

## Protocols & Mnemonics (Section 4)

Field reference cards covering:

- MARCH / ABCDE — Primary assessment
- TCCC Phases / STOP — Scene safety
- AVPU — Consciousness check (shared)
- OPQRST — Pain assessment (shared)
- DCAP-BTLS / Look-Listen-Feel — Physical assessment
- SMARCH / SAMPLE — Patient history
- 9-Line MEDEVAC / SBAR Handover — Communication
- SBAR — Situation communication (shared)
- START Triage — Mass casualty (shared)
- Tourniquet Rule / Stop the Bleed — Hemorrhage control
- Care Under Fire / Bystander Safety — Threat management
- RICE — Musculoskeletal (shared)

Filter: ALL / ⚔ TACTICAL / 🏥 CIVILIAN

Printable — print button appears when on this page.

---

## Multi-Team Data Sync

Each deployment of MEDKIT is a standalone database. Teams exchange data via Export/Import JSON.

**Company identity** is set once during first-time setup and cannot be changed:
- **Company Name** — e.g. Forward Observer Group
- **Company Tag** — e.g. FOG (2–6 chars)

All individual and group IDs are auto-prefixed with the company tag: `FOG-001`, `FOG-Alpha Element`.

**Merge behavior** (coming in v1.4):
- Different company tags → clean merge, no conflicts possible
- Same company tag → timestamp-based conflict resolution
- Same ID, different name → manual resolution per record

For now: Export/Import with Overwrite is available. Import shows a preview before committing.

---

## Data Storage

All data is stored in the browser's **localStorage**. This means:

- Data is stored per browser per file path
- Clearing browser data will erase MEDKIT data
- Always keep an Export JSON backup
- Recommended: one designated device as "master" with regular exports

**Storage capacity:** Approximately 2,000–3,000 individuals before approaching browser limits.

---

## Version History

| Version | What changed |
|---|---|
| v1.0 | Initial release — roles, kits, training, protocols, sourcing, SAR |
| v1.1 | Tag system, filter bars, two-column layout, pharmaceutical panel, protocols page, section reorder |
| v1.2 | Water/Sea/River scenario, Additional Items section (kit + pharma), Superadmin kit state fix |
| v1.3 | First-time setup screen, company tag + auto-prefix, timestamps on all writes, export metadata, import preview, silent DB migration |
| v1.4 | Merge import, conflict resolution, guest access *(planned)* |

---

## Sourcing

See **Section 6 — Sourcing Guide** inside the app for detailed sourcing information.

**Priority note:** Never compromise on tourniquets, chest seals, or hemostatic gauze. Authenticated brands only — CAT Gen7, SOFTT-W, HyFin/HALO, QuikClot Combat Gauze.

---

## Training Pathway

See **Section 1 — Training** inside the app for the full training pathway.

Civilian tiers: Entry → Intermediate → Advanced → Tactical  
AFP Reserve: Medical component pathway  
Med Professionals: Bridging recommendations

---

## License

For organizational and personal preparedness use. Not a substitute for professional medical training or licensed medical advice.

---

*Built for Philippine civilian, AFP Reserve, and volunteer organization use.*
