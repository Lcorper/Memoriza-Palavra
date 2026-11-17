# Memoriza Palavra 3.6 — Mobile interface test report

## Passed (Chromium, HTML injected into an isolated test page)
- 390×844 phone, 768×1024 tablet, 1280×800 desktop
- No uncaught JavaScript errors during the tested flows
- No document-level horizontal overflow at these viewports
- Main navigation has four destination links
- Adding a three-verse numbered passage and detecting three sections
- Passage progress card and progressbar with three steps
- Switching between all four memorization modes
- Passage section selector appears in hybrid mode

## Limitations
- Browser security policy blocked navigation to the local HTML file; tests loaded HTML via `page.set_content`.
- Storage persistence across reloads and backup restore were not retested in this pass.
- Actual iOS Safari and live Supabase synchronization were not tested.
- These are smoke/regression checks, not an exhaustive verification of all quiz outcomes.

## Compatibility
- Existing `memoriza_palavra_v1`, `memoriza_palavra_activity_v1`, and `memoriza_palavra_draft_v1` storage keys are unchanged.
- No existing verse records were rewritten as part of this UI update.
- Export a backup from the prior version before switching to a different website origin or local file.
