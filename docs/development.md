# Development

Use two-space TypeScript formatting and keep domain calculations in `src/lib/` or `src/services/` rather than embedding them in visual components. Add or update Supabase migrations for schema changes; do not edit a deployed database manually without recording the change.

Run:

```powershell
npm run lint
npm run build
```

Test signed-out and signed-in paths, expired sessions, empty results, failed Supabase requests, map failures, and mobile layouts. Keep real user and location data out of local fixtures.
