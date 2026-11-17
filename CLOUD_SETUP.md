# Memoriza Palavra 3.11 — Render + Supabase

The public Supabase Project URL and publishable key are already configured in `cloud.js`. Never put a service_role/secret key into website files.

## Publish to Render

Upload the **contents** of `memoriza_site` as the static-site root, with `index.html` and `cloud.js` side by side. Set Publish Directory to `.` if they are at repository root, or `memoriza_site` if they are inside that folder. No build command is required.

## Supabase prerequisites

The app expects the `public.user_data` table created previously, with `user_id uuid primary key`, `data jsonb`, `updated_at timestamptz`, and RLS policies allowing authenticated users to select/insert/update their own row. The app uses email/password authentication. Under Authentication → URL Configuration, use `https://memoriza-palavra.onrender.com` as the Site URL. Enable the Email provider. If email confirmation is on, confirm the email before signing in.

## First sync — avoid overwriting saved verses

1. On your **original device**, open the old app's `Meus dados` and export a JSON backup.
2. Deploy 3.11, open **☁ Minha nuvem**, and sign up/sign in.
3. On the original device, choose **Enviar este dispositivo à nuvem**. This uploads its current verses and study activity. It asks before overwriting existing cloud data.
4. On the **second device**, sign in with the same email, choose **Trazer dados da nuvem**, confirm replacement of its local library, and wait for reload.
5. After this initial setup, changes to verses and review activity are uploaded automatically when online. Drafts remain device-local.

**Important limitations:** This is simple snapshot sync, not conflict-free merging. Simultaneous edits on two devices can overwrite each other; use one device at a time and allow synchronization before switching. The automatic upload on opening a previously paired device is not a full two-way reconciliation: use **Trazer dados da nuvem** when returning to a device that has stale local data. A future version should implement revision-based conflict detection and automatic two-way merging before claiming fully seamless synchronization.

## Tests

JavaScript syntax checks passed. Chromium tests passed at 390×844, 768×1024, and 1280×800 for cloud dialog open/close, 66 Bible books, study-mode selection, and no page errors. The environment blocked browser navigation; tests used direct page content and injected the cloud script. Real Supabase authentication/database operations were **not** tested because they require your private account and live database. Verify upload, refresh, download on second device before trusting cloud saving.
