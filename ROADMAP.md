# 🛣️ Product and Engineering Roadmap

This roadmap separates product ideas from verified current implementation. Items remain proposals until code and tests demonstrate completion.

## Phase 0: Security and trust
- [ ] Remove tracked `.env`; inspect history and rotate confidential values.
- [ ] Add rate limits and payload caps to unauthenticated `parse-idea`.
- [ ] Restrict CORS where practical.
- [ ] Validate all Edge Function request and model response shapes.
- [ ] Audit RLS policies and automate two-user tests.
- [ ] Standardize non-2xx errors and safe logging.

## Phase 1: Evidence and methodology
- [ ] Add provenance metadata to market and competitor records.
- [ ] Label mock/random data clearly in UI.
- [ ] Version BizScore methodology.
- [ ] Add formula documentation and worked examples.
- [ ] Add forecast sensitivity/ranges and assumptions.
- [ ] Independently validate external provider coverage.

## Phase 2: Engineering quality
- [ ] Add Vitest and React Testing Library.
- [ ] Add Edge Function tests.
- [ ] Add Supabase RLS integration tests.
- [ ] Add Playwright smoke journeys.
- [ ] Add accessibility automation and manual evidence.
- [ ] Add generated-type/schema drift check.

## Phase 3: Product capability
- [ ] Introduce vetted market datasets with source/freshness metadata.
- [ ] Add user-controlled comparison criteria.
- [ ] Add exportable report formats with assumptions and references.
- [ ] Add transparent data confidence/provenance panels.
- [ ] Improve saved idea filtering and organization.

## Phase 4: Operations
- [ ] Add structured monitoring and correlation IDs.
- [ ] Define AI usage quotas and budgets.
- [ ] Test backup/restore procedures.
- [ ] Define incident, privacy and retention processes.
- [ ] Establish performance budgets.

## Non-goals
Do not promise guaranteed business success or represent heuristic/mock output as validated investment advice.
