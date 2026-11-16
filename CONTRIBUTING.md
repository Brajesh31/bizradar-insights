# 🤝 Contributing Guide

Thank you for improving BizRadar Insights. Contributions should make the application more accurate, understandable, accessible, secure and maintainable.

## 1. Before starting

1. Read README, this guide and SECURITY.md.
2. Check open issues and existing implementation.
3. Identify the affected route, component, service, migration or function.
4. For larger work, open a feature proposal before making broad changes.
5. Never use real customer records, private conversations, API tokens or production exports in fixtures.

## 2. Local development

```bash
npm ci
npm run dev
```

Before submitting:

```bash
npm run lint
npm run build
```

The current package does not define a unit test script yet. Add test coverage when changing domain calculations or remote data flows, and document exactly what was run.

## 3. Code expectations

### React/TypeScript
- Use explicit types for page/service contracts.
- Keep page components focused on orchestration.
- Avoid unsafe `any` where domain models exist.
- Handle loading, empty, error and success states.
- Avoid expensive work inside render loops.

### Analytics
- Document formulas, units, assumptions and bounds.
- Preserve provenance labels.
- Keep synthetic data visibly distinct from external results.
- Add boundary tests for scoring/finance/risk changes.
- Avoid presenting an estimate as an observation.

### Supabase
- Add reviewed migrations for schema changes.
- Update generated database types.
- Add/adjust RLS policies and test with two users.
- Validate Edge Function payloads.
- Keep provider secrets server-side.

### Accessibility
- Use semantic elements and labels.
- Maintain keyboard reachability and visible focus.
- Provide text alternatives for important chart/map information.
- Do not communicate status by color alone.

## 4. Change workflow

1. Create a focused branch.
2. Preserve existing files/assets unless a scoped change requires editing.
3. Make a small, reviewable change.
4. Add tests and documentation.
5. Run lint/build.
6. Review data/security/accessibility impact.
7. Submit a PR with summary, evidence, risks and migration instructions.

## 5. Pull request checklist

- [ ] Scope and rationale are clear.
- [ ] Existing application files are preserved.
- [ ] No .env, tokens, user data or provider secrets are included.
- [ ] Supabase schema/types/RLS updated if needed.
- [ ] Analytics formulas and provenance documented.
- [ ] Loading/error/empty states handled.
- [ ] Accessibility impact reviewed.
- [ ] Commands and tests reported honestly.
- [ ] README/docs/changelog updated where relevant.

## 6. Security reports

Do not open a public issue with exploitable details. Follow SECURITY.md.
