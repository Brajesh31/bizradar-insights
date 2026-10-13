# Deployment

Build with `npm ci` and `npm run build`, then deploy the `dist/` directory to a static host configured to rewrite application routes to `index.html`.

Configure only public Vite values at build time. Apply Supabase migrations and verify RLS policies separately. Keep service-role keys and third-party provider secrets in Edge Functions or a server-side secret manager. Configure HTTPS, security headers, monitoring, rate limits, and privacy notices before production.
