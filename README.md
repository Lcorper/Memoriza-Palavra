# Memoriza Palavra — hosted personal edition

## What is included
- `index.html`: existing memorization app (Portuguese)
- `cloud.js`: optional account sign-in and cloud sync via Supabase
- `supabase.sql`: database schema and row-level security

## Setup
1. **Export a backup from your current app before migration.** Open the new site and import that backup to preserve your previous verses and activity.
2. Create a Supabase project at https://supabase.com. In SQL Editor, run `supabase.sql` once. If policies already exist, don't run the same SQL again without checking them.
3. Under Authentication settings, enable Email sign-in. Set the Site URL to the address of your hosted app. Confirm-email behavior is controlled by your Supabase project.
4. Deploy the `memoriza_site` folder as a static site on Vercel, Netlify, or another HTTPS static host. Vercel can deploy by importing a Git repository containing this folder, with no build command and the folder as its root directory.
5. On your hosted site, click **☁ Sincronização**. Paste your Supabase project URL and **public anon/publishable key** (never a service_role/secret key). Save the configuration, then create an account and sign in.
6. Click **Sincronizar agora** and verify the status. After signing in on another device, synchronize and refresh the page to load the newly imported verses.

## Important limitations
- Until the site is deployed and Supabase is configured, the app remains **local-only**. This package does not create an account, database, or hosted site automatically.
- Cloud sync requires an internet connection and an authenticated account. Offline changes remain in browser storage and will sync after reconnection or when you click Sync.
- This is an early personal-use sync implementation, **not** a production-grade multi-device conflict resolution engine. It merges verses by ID (local copy wins), merges activity keys, and retains local draft fields when present. Simultaneous edits across devices may overwrite some changes. Keep occasional exported backups, especially before initial migration.
- Authentication tokens and project configuration are stored in browser localStorage. Use a trusted device, HTTPS, and a strong password. Supabase RLS policies restrict each user to their own row.
- NVI/ARA copyrighted Bible text is not bundled or retrieved. Users paste verses themselves; public redistribution requires separate licensing review.

## Version 3.2 — passagens longas e painel
- Cole uma passagem de vários versículos (por exemplo Romanos 8:28–35) no campo de texto; mantenha a referência com intervalo e escolha NVI ou ARA. O texto deve ser fornecido pelo usuário.
- O modo Ler respeita as quebras de parágrafo; o modo Complete a passagem permite praticar o texto inteiro ou partes de até 45 palavras, mantendo os registros de erros por posição no texto original.
- O painel exibe revisões pendentes, palavras com erros e próximas revisões. Nenhuma informação existente é excluída pela atualização.
- A versão continua usando as mesmas chaves de armazenamento local; cloud sync requer configuração própria. Faça uma cópia dos dados antes de trocar o arquivo HTML.
