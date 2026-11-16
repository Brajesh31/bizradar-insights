# ⚙️ Environment and Application Configuration

## Browser-exposed variables

Vite exposes variables prefixed with `VITE_` to client-side code. Treat every such value as public.

| Variable | Required | Consumer | Secret? |
|---|---:|---|---|
| `VITE_SUPABASE_URL` | Yes | Supabase browser client | No |
| `VITE_SUPABASE_PUBLISHABLE_KEY` | Yes | Supabase browser client | No, browser-safe publishable key |
| `VITE_MAPBOX_TOKEN` | Conditional | Map components/services if wired | Public token, restrict by domain/scopes |

## Server-side Edge Function secrets

The function source reads:
- `LOVABLE_API_KEY`
- Supabase-provided `SUPABASE_URL`
- Supabase-provided `SUPABASE_ANON_KEY`

The latter Supabase values are provided by the Edge Function runtime in Supabase's environment. The Lovable API key must be configured using server-side secrets, not committed files or Vite-prefixed variables.

Example CLI pattern (use your current project ref):

```bash
supabase secrets set LOVABLE_API_KEY=your-server-side-secret
```

Do not place the real secret in shell history on shared machines. Prefer a protected secret manager/CI environment.

## Local setup

```bash
cp .env.example .env
```

Fill in only public browser configuration. The checked-in `.env` file was historically committed and must not be used as a credential source. Remove it from tracking and rotate any confidential values that may have appeared in Git history.

## Build modes

- `npm run dev`: local development mode.
- `npm run build`: production bundle.
- `npm run build:dev`: development-mode bundle.
- `npm run preview`: preview the last built output.

## Validation and failure behavior

The Supabase client currently reads the two required Vite variables during module initialization. Missing/invalid values can prevent API integration from functioning. A future improvement should validate configuration at startup and show a clear setup error without printing secrets.

## Configuration change checklist

- [ ] Update `.env.example` when adding/removing variables.
- [ ] Document whether the variable is browser or server-side.
- [ ] Never use `VITE_` for secrets.
- [ ] Add provider domain restrictions where available.
- [ ] Add an appropriate local/CI configuration validation.
- [ ] Ensure documentation contains placeholders, not live values.
