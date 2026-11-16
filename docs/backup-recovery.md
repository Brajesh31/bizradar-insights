# 💾 Backup and Recovery

This guide contains recommended practices, not proof that backup policies are enabled in the connected Supabase project.

## Database backup
Use the project's supported backup/PITR features. Confirm schedule, retention, point-in-time recovery, access controls, RTO and RPO.

## Development exports
Use Supabase CLI/PostgreSQL tooling for synthetic fixtures only. Keep exports outside Git with restricted permissions. Never commit real user rows, auth records, session tokens or conversation history.

## Restore test
1. Restore into isolated non-production project.
2. Verify migration state.
3. Check core tables, indexes and constraints.
4. Confirm TypeScript types align with restored schema.
5. Verify RLS policies.
6. Test auth, saved records and Edge Function behavior.
7. Record restore duration and test output.
8. Secure or remove the test environment.

## Frontend recovery
```bash
npm ci
npm run build
```

Retain deploy environment configuration in the host's secret manager. Use the incident template for restore records.
