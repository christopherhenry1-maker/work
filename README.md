# Executive Dashboard (Google Apps Script + HTML)

This repository contains the Executive Dashboard front-end (HTML/CSS/JS) and the Google Apps Script backend that powers calendar sync, deliverables, and agenda workflows.

## What’s included
- **Frontend UI**: `claude pack/initial index`
- **Apps Script backend**: `claude pack/initial cs`
- **Apps Script manifest**: `claude pack/appsscript.json`

## Key features
- Two-week executive schedule view and monthly calendar view
- Deliverables tables for Sarcone and DK
- Agenda creation and agenda indicators
- Calendar sync from an executive Google Calendar into a Meetings sheet
- PDF export for the two-week schedule
- “On the Radar” overview section with a Google Sheet tab for high-level statements + a Gemini-generated weekly executive summary

## Quick start (Apps Script)
1. Open the Apps Script project and update the `CONFIG` values in `claude pack/initial cs`:
   - `DELIVERABLES_SHEET_ID`
   - `MEETINGS_SHEET_ID`
   - `EXECUTIVE_CALENDAR_ID`
   - Row range settings (if your sheet layout differs)
2. Run `setup()` once to create/verify sheets.
3. In the Google Sheet, use the **📊 Executive Dashboard** menu:
   - **🔄 Sync Calendar Now**
   - **🧠 Update On the Radar Summary (Gemini)** (optional)
   - **📅 Setup Daily Auto-Sync** (optional)
4. Deploy as a **Web App** and open the deployed URL.

## Gemini setup (On the Radar summary)
- The script expects a Script Property named `GEMINI_API_KEY`.
- Optional: set `GEMINI_MODEL` (default: `gemini-1.5-flash`).
- Add statements in the `On the Radar` tab, then run: **📊 Executive Dashboard > 🧠 Update On the Radar Summary (Gemini)**.

## Troubleshooting
- **Backend timeout** message in the UI:
  - Verify the Apps Script deployment is active.
  - Confirm Sheet IDs in `CONFIG` are correct.
  - Run `testDataRetrieval()` in Apps Script.

## Notes
- The dashboard expects Meetings and Deliverables tabs to exist (auto-created by `setup()`).
- Changes to deliverables section positions require updating the `*_START_ROW` values in `CONFIG`. The `*_END_ROW` values are treated as safety limits; exec sections can grow until the next section’s start row.

## Repo structure
- `claude pack/initial index` – main HTML/CSS/JS
- `claude pack/initial cs` – Apps Script backend
- `claude pack/appsscript.json` – Apps Script manifest
