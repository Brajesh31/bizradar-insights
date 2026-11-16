# Release Checklist

## Source/build
- [ ] Commit/release branch identified.
- [ ] npm ci passes.
- [ ] npm run lint passes.
- [ ] npm run build passes.
- [ ] No tracked .env or generated output.

## Backend/data
- [ ] Migrations reviewed/applied.
- [ ] RLS tested with separate users.
- [ ] Supabase types match schema.
- [ ] Edge Function secrets set server-side.
- [ ] JWT/CORS/input validation/rate limits checked.

## Product
- [ ] Main user journeys smoke-tested.
- [ ] Chart/map fallback tested.
- [ ] Data provenance visible.
- [ ] Accessibility checks recorded.
- [ ] Performance regressions reviewed.

## Operations
- [ ] Monitoring and rollback owner identified.
- [ ] Backup/recovery path known.
- [ ] Changelog/release notes updated.
- [ ] Incident path available.

## Approval
- Reviewer:
- Date:
- Commit:
- Outstanding risks:
