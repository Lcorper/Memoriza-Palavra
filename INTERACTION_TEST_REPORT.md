# Memoriza Palavra 3.8 — interaction verification

Fix: replaced the first + Adicionar JavaScript-only button with a native HTML details/summary control. The form can now open without an inline JavaScript handler. The existing `toggleAdd(true/false)` API is preserved for other controls. Added a visible selected study mode and larger mobile touch targets. Removed the stale `cloud.js` reference (cloud sync is not configured in this local release).

Automated Chromium checks using `page.set_content` (direct local-file navigation is blocked in this environment): 24/24 passed across 390×844, 768×1024, 1280×800. Each viewport verified opening add form, saving a passage, all four study modes, closing/reopening the form, and no page JavaScript errors. Existing demo entries were retained.

Limitations: actual Safari and sandbox HTML preview are not testable here. This test does not verify all nested game buttons, persistence after browser restart, or cloud sync. A host preview that disables JavaScript may allow the native Add form to open but cannot run the interactive study games; use a real browser or host the app.
