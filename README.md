# Sheet-to-Doc Merge Creator

An Autocrat-style mail-merge tool for Google Sheets, built entirely in Google Apps Script — no add-ons, no external dependencies.

## What it does

- Reads rows from a Google Sheet (e.g. candidate assessment results, form responses, or any tabular records).
- When a trigger column (default: `Create Document?`) is set to **YES**, it copies a Google Doc template, replaces every `<<placeholder>>` with the matching column value, and exports a PDF.
- Writes the results back to four output columns: merged file ID, merged file URL (PDF), a clickable hyperlink to the merged Google Doc, and a merge status with timestamp.
- Shows a **confirmation dialog listing exactly which rows/names will be processed** before creating anything — nothing is generated without an explicit Yes.
- Placeholders are matched to **header names** (exact → prefix → contains), not column letters, so inserting or removing columns won't break the merge. Short tags can be mapped to long headers via a configurable alias table.
- Optional installable trigger: setting the trigger column to YES generates the document immediately (still with confirmation).

## Setup

1. Open your Google Sheet → **Extensions → Apps Script** → paste the contents of `sheet-to-doc-merge-creator.gs` → save.
2. Reload the spreadsheet. Two menus appear: **📄 Merge Creator** and **⚙️ Setup**.
3. Go to **⚙️ Setup → 🚀 Run setup wizard** and enter, step by step:
   - the link to your Google Doc **template** (containing `<<Header Name>>` placeholders),
   - the **output folder** (or keep the default: same folder as the template),
   - the **sheet name** and **header row**,
   - the **column headers** for the trigger and the four output columns, plus the column used as the display name in confirmation dialogs.
4. Optionally set **placeholder aliases** (JSON) to map short tags like `<<Name>>` to a longer header like `Candidate Name`.
5. Use **ℹ️ View current config** anytime to verify what's active.

All configuration is stored in Script Properties — **no IDs, keys, or names are hardcoded in the source**, and you never need to edit the code to reconfigure.

## Caveat on data sources

The example sheet schema included in the code comments (Candidate Name, Role, Score, etc.) is **deliberately simplified and example-only**. The author works with confidential HR data, so production column mappings, scoring schemas, and document templates cannot be published. Anyone adapting this template must supply their own header mapping and Doc template — the header-name resolution and alias system are designed to make that a configuration task, not a coding task.

## Attribution

**100% AI-generated, 100% human-directed.**
Directed and iterated by Yordhan Fitrians Akhmad B. based on real HR pain points — refined repeatedly for business fit, user experience, and workflow comfort. Published as a generic, reusable template.
