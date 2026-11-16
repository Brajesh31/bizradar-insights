# 🚢 Deployment Guide

## Frontend build

```bash
npm ci
npm run lint
npm run build
```

Vite outputs the static site in `dist/`. Deploy that directory to a host that supports SPA fallback routing.

## BrowserRouter rewrites

The app uses BrowserRouter. Configure the host to rewrite non-file application paths to `index.html`. Test direct refresh on:
- /opportunities
- /feasibility-report
- /saved
- /compare
- /idea-analyzer
- /auth

## Frontend environment
Configure browser-safe variables in the hosting provider:
- `VITE_SUPABASE_URL`
- `VITE_SUPABASE_PUBLISHABLE_KEY`
- Optional restricted `VITE_MAPBOX_TOKEN`

These are compiled into the bundle. Rebuild after changing them.

## Supabase platform
1. Link target project.
2. Apply reviewed migrations.
3. Verify RLS and Auth settings.
4. Set function secrets.
5. Deploy Edge Functions.
6. Check JWT/CORS/input limits.
7. Test both authenticated and anonymous behavior.

## Release checklist
- [ ] .env is not tracked.
- [ ] Server secrets are not in frontend bundle.
- [ ] npm ci/lint/build pass.
- [ ] SPA deep-link refresh works.
- [ ] Migrations applied.
- [ ] RLS ownership tests pass.
- [ ] Function secrets set server-side.
- [ ] JWT/CORS/quotas/validation checked.
- [ ] Mock data disclosures visible.
- [ ] Accessibility/browser smoke checks recorded.
- [ ] Rollback path identified.
