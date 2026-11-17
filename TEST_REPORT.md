# Memoriza Palavra 3.5 — browser test report

Date: 2026-11-17

Chromium was run headlessly through Playwright. Since navigation to local files and loopback URLs is blocked in this environment, the HTML was loaded using `page.set_content`. A localStorage-compatible in-memory mock was used to test saving, backup, and restoring. These are genuine browser JavaScript interactions, but not a live hosting or real-device test.

## Passed
- Startup with existing sample verses and no page JavaScript errors
- Phone 390×844, tablet 768×1024, desktop 1280×800: no horizontal document overflow
- Paste and detect a three-verse numbered passage; save and select it
- Automatic local save data shape
- Cumulative passage selection and unlocking after a mistake-free multiple-choice round
- Wrong-answer recording, no false unlock after a mistake, and correct-answer auto advance
- Spaced repetition rating saved to the selected passage
- Backup download and backup import restoration
- No JavaScript page errors in exercised scenarios

## Not yet verified
- Real iOS Safari and Android Chrome devices
- Real browser persistent localStorage across sessions, files, or deployment origins
- Supabase account and cloud synchronization
- Every possible Bible text formatting pattern
- All keyboard and accessibility interactions

## Compatibility
The existing `memoriza_palavra_v1` and `memoriza_palavra_activity_v1` storage keys were retained. No stored user data was modified by these tests. Always import a backup when switching storage origins.
