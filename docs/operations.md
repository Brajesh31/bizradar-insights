# 🧰 Operations and Maintenance

## Components and operational signals

| Component | Signals |
|---|---|
| Static frontend | Deploy status, browser errors, route failures |
| Supabase Auth | Sign-up/login/session restoration failures |
| Postgres | Query failures, RLS denials, migration state |
| Edge Functions | Invocation count, errors, latency |
| AI Gateway | Rate limits, credits, retries and duration |
| Map/geocoding | Token validity, quotas, provider outages |

## Monitoring recommendations
Track frontend runtime errors, auth errors, database failures, RLS denials, Edge Function latency/error rate, AI provider errors/cost and map quota failures.

Do not log credentials, session tokens or sensitive business-plan content unnecessarily.

## Routine maintenance
- Review dependency updates and advisories.
- Run lint/build after dependency changes.
- Review RLS policies when schema changes.
- Rotate server secrets if exposure is suspected.
- Review CORS, function validation and quotas.
- Validate provider terms and data freshness.
- Keep source-provenance and methodology docs current.

## Incident response outline
1. Identify affected component and time window.
2. Classify availability, integrity, privacy, security or quota impact.
3. Restrict/disable abusive public functions if required.
4. Rotate exposed secrets.
5. Preserve sanitized logs and commit/migration references.
6. Restore safely.
7. Record impact and follow-up work.

No production SLA, monitoring dashboard, paging policy or confirmed hosting environment is asserted here.
