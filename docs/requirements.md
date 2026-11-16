# 📋 Requirements and Acceptance Criteria

## 1. Scope

This document describes current feature scope and recommended quality requirements. Statements marked **Current** are evidenced by checked-in source. Statements marked **Target** describe acceptance expectations and may not yet be implemented.

## 2. Functional requirements

| ID | Requirement | Status/evidence |
|---|---|---|
| FR-001 | Render a landing page at `/` | Current: `src/pages/Index.tsx` |
| FR-002 | Provide opportunity discovery at `/opportunities` | Current |
| FR-003 | Search for locations and select a result | Current service/page flow |
| FR-004 | Select a business category | Current |
| FR-005 | Generate opportunity cards from selected inputs | Current; local rule-based/mock data |
| FR-006 | Render map context for a selected location | Current; map provider config may be required |
| FR-007 | Calculate BizScore and score explanations | Current local engines |
| FR-008 | Generate feasibility report data | Current report builder |
| FR-009 | Display forecast and competitor panels | Current |
| FR-010 | Parse a free-text business idea through an Edge Function | Current; external AI key/config required |
| FR-011 | Generate AI insight text through an Edge Function | Current; external AI key/config required |
| FR-012 | Provide AI assistant interaction | Current function configured with JWT verification |
| FR-013 | Register, sign in and sign out | Current Supabase Auth context |
| FR-014 | Persist saved ideas | Current page/database integration |
| FR-015 | Compare saved/candidate ideas | Current UI route |
| FR-016 | Display About and Contact pages | Current |
| FR-017 | Show fallback route for unknown paths | Current `NotFound` page |

## 3. Non-functional requirements

| ID | Requirement | Target acceptance |
|---|---|---|
| NFR-001 | Maintainable frontend | TypeScript strictness and clear module boundaries |
| NFR-002 | Reproducible install | `npm ci` completes from committed lockfile |
| NFR-003 | Static quality | `npm run lint` returns success |
| NFR-004 | Production bundle | `npm run build` completes without errors |
| NFR-005 | Secret management | No local/server secret committed or exposed to client |
| NFR-006 | Authorization | Supabase RLS protects every user-owned table |
| NFR-007 | Resilience | API errors, missing provider config and timeouts are handled |
| NFR-008 | Accessibility | Keyboard, focus, labels, contrast and semantic structure reviewed |
| NFR-009 | Performance | Route, chart and map loading do not unnecessarily block core UI |
| NFR-010 | Privacy | Collect only necessary personal/business information |
| NFR-011 | Data provenance | User can distinguish mock, derived, provider and AI data |
| NFR-012 | Observability | Edge Function failures and relevant usage metrics are recorded safely |

## 4. User-facing acceptance criteria

### Opportunity exploration
- [ ] User can enter a location query.
- [ ] Search result selection updates the chosen location.
- [ ] User can choose a category.
- [ ] Analysis is blocked until both required inputs exist.
- [ ] Result cards identify the location/category context.
- [ ] Synthetic market assumptions are disclosed.

### Feasibility reports
- [ ] Report shows score inputs and output dimensions.
- [ ] Forecast output includes its timeframe and assumptions.
- [ ] Financial values identify currency and whether they are estimated.
- [ ] Missing/failed data does not silently become authoritative zero.
- [ ] User can return to the originating workflow.

### Authentication and saved records
- [ ] Auth errors are understandable and do not reveal secret details.
- [ ] User can see their own saved records only.
- [ ] User A cannot read/update/delete User B's rows.
- [ ] Sign-out invalidates application state as expected.
- [ ] Loading and empty states are available.

### AI-backed flows
- [ ] Invalid/oversized input is rejected server-side.
- [ ] Missing server secret produces a safe error.
- [ ] Provider rate limit and payment errors are surfaced accurately.
- [ ] Model output is parsed and schema-validated before use.
- [ ] User is told generated content may contain errors.

## 5. Explicit non-goals

This app is not a regulated investment adviser, credit scoring platform, business-registration portal, guarantee of profitability, verified census/market statistics source, or substitute for field research and professional accounting/legal advice.
