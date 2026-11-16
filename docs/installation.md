# 🚀 Installation and Local Development

## Prerequisites

- Node.js LTS compatible with Vite 5.
- npm.
- Git.
- Supabase project for Auth, Postgres and Edge Functions.
- Optional Mapbox browser token if the map implementation is enabled.
- Supabase CLI and Deno for local Edge Function work.

Check your versions:

```bash
node --version
npm --version
```

## Clone the project

```bash
git clone https://github.com/Brajesh31/bizradar-insights.git
cd bizradar-insights
```

## Install exact dependencies

```bash
npm ci
```

Use npm because the repository includes `package-lock.json`. Do not substitute Bun/Yarn commands for this project unless its dependency-management policy is deliberately changed.

## Configure environment

Copy `.env.example` to `.env` and enter your own Supabase development project values. Keep `.env` local and untracked.

Required browser variables:
- `VITE_SUPABASE_URL`
- `VITE_SUPABASE_PUBLISHABLE_KEY`

Optional:
- `VITE_MAPBOX_TOKEN`

Never set a service-role key or AI provider secret in a Vite-exposed variable.

## Configure Supabase

1. Create/select a Supabase project.
2. Set local URL and publishable key.
3. Review the migrations in chronological order.
4. Apply migrations using the Supabase CLI or SQL editor.
5. Verify RLS policies for all tables.
6. Configure Edge Function secrets server-side.
7. Set auth redirect URLs and allowed origins.
8. Deploy functions after reviewing their authorization and CORS rules.

See [supabase-setup.md](supabase-setup.md).

## Run the frontend

```bash
npm run dev
```

Vite prints a development URL, commonly `http://localhost:5173`.

## Validate the app

```bash
npm run lint
npm run build
npm run preview
```

The package currently does not define `npm test`. Do not assume an absent test script is a successful test.

## Common setup issues

- Missing Supabase URL/key: validate local `.env` names and restart Vite.
- Auth callback failure: configure redirect URLs in Supabase.
- Empty persisted data: inspect RLS policies and user_id filters.
- AI function errors: validate server-side gateway secret and deployment status.
- Map blank/error: configure a public map token and confirm provider restrictions.
- Database type mismatch: regenerate Supabase types after migrations.

## Clean reset

```bash
rm -rf node_modules dist
npm ci
npm run build
```

PowerShell:

```powershell
Remove-Item -Recurse -Force node_modules, dist -ErrorAction SilentlyContinue
npm ci
npm run build
```
