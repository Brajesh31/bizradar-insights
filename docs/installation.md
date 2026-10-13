# Installation

Requirements: Node.js, npm, a Supabase development project, and optional Mapbox access for live maps.

```powershell
Copy-Item .env.example .env
npm ci
npm run dev
```

Set `VITE_SUPABASE_URL` and `VITE_SUPABASE_PUBLISHABLE_KEY` in the untracked `.env`. Apply the repository's Supabase migrations using the Supabase CLI when database features are enabled. Never place service-role keys in Vite variables.
