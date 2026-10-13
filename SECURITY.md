# Security Policy

Never commit `.env`, Supabase service-role keys, Mapbox secrets, access tokens, customer records, or precise private location data. Only publish the Supabase URL and publishable browser key intended for the client; enforce authorization with Supabase Row Level Security and never rely on UI guards alone.

Review database policies, Edge Functions, external API proxying, rate limits, storage access, and analytics privacy before production. Treat opportunity scores and forecasts as informational, not financial advice.

Report vulnerabilities privately to Brajesh Kumar through <https://github.com/brajesh31>. Include sanitized reproduction steps, affected route or Supabase object, impact, and whether any secret was exposed. Rotate exposed credentials immediately.
