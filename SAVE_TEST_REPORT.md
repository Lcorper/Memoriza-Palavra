# Memoriza Palavra — correção do salvamento (3.10)

Tested with Chromium using page content loaded directly (file navigation is restricted in this environment).

- JavaScript syntax: passed (`node --check`).
- Save with writable simulated browser localStorage: passed; library count 3 → 4, form closes, no JS exceptions.
- Save with blocked browser localStorage: passed; visible error, original text retained, form remains open, library count unchanged.
- Four study modes after saving: passed (Ler, Complete a passagem, Memorização gradual, Digitar).
- Viewport: 390 × 844.

Important limitation: Simulated storage is not equivalent to a real iPhone Safari test. ChatGPT's file preview may restrict persistent browser storage. In that case, a standalone HTML file cannot reliably persist saved passages inside the preview. Open the file in a normal browser or publish it to an HTTPS site.
