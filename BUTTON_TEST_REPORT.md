# Memoriza Palavra 3.7 — Button and regression test report

Date: 2026-11-17

## Fixes
- Replaced the `+ Adicionar` inline class toggle with an explicit `toggleAdd()` controller, keeping its accessible expanded state, button label, scroll and input focus synchronized.
- Improved required-field handling when saving a passage and kept the editor open for corrections.
- Fixed the empty-library `Dica` and review controls to show guidance rather than attempting to access a nonexistent verse.
- Updated the empty-library add shortcut to use the same add controller.
- Clearing a draft now refreshes passage detection feedback.
- Improved add-form spacing and minimum tap targets.

## Automated Chromium tests
Using `/usr/bin/chromium` with Playwright, the page HTML was loaded using `page.set_content()` because direct `file://` navigation is blocked by this environment. A controlled localStorage mock was used, so these are browser interaction and simulated-storage tests, not a real-device storage durability guarantee.

18/18 responsive regression checks passed at 390×844, 768×1024, and 1280×800:
- Open and save passage using `+ Adicionar`
- Passage recognition preview
- Four study modes and answer interaction
- Hint, restart, mark review, search
- Draft saving and clearing
- Backup export download
- No page JavaScript exceptions
- No horizontal overflow

Additional 4/4 checks passed:
- Correct-answer progression unlocks the next passage stage
- Importing a backup preserves saved word statistics
- Empty-library hint and review buttons do not throw
- No JavaScript exceptions in those scenarios

## Limitations
- Direct local-file navigation was blocked; tests used in-memory HTML.
- iPhone Safari and long-term localStorage persistence were not tested on a physical device.
- Cloud sync is not configured or verified.
- Keep a JSON backup before replacing a previously used app file or origin.
