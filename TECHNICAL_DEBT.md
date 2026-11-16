# 🧱 Technical Debt Register

This register is based on the source/repository inspection performed for this documentation pass. It is not an assertion that an item has been fixed.

| ID | Priority | Finding | Impact | Recommended action |
|---|---|---|---|---|
| TD-001 | High | Tracked `.env` file | Configuration is exposed in repository history | Remove from tracking, add ignore rule, rotate any confidential values |
| TD-002 | High | Public `parse-idea` function with JWT verification disabled | Model gateway can be abused and incur cost | Add rate limits, payload cap, validation and abuse controls |
| TD-003 | High | Wildcard CORS on Edge Functions | Broad cross-origin request surface | Restrict allowed origins where appropriate |
| TD-004 | High | Edge Function input validation not standardized | Malformed/oversized requests and model cost abuse | Introduce shared schema validation |
| TD-005 | High | RLS deployment behavior not independently verified | Cross-user data exposure risk | Add automated two-user RLS tests |
| TD-006 | High | AI output parsed without robust schema validation in parse-idea | Malformed model output can cause runtime failure | Zod/JSON schema validation and safe failure |
| TD-007 | Medium | generate-insights may return HTTP 200 on failure | Monitoring/client may treat error as success | Use correct non-2xx contract |
| TD-008 | Medium | Synthetic/random market data resembles live metrics | User overconfidence | Add provenance metadata and visual labels |
| TD-009 | Medium | Fixed category growth rates drive forecasts | Projection is not validated predictive model | Version assumptions and provide sensitivity/ranges |
| TD-010 | Medium | Some shared calculations occur inside page/list rendering | Excess computation and repeated work | Profile and hoist shared derivations |
| TD-011 | Medium | No test script in package.json | Regressions may reach production | Add Vitest, RTL, Supabase/RLS and E2E coverage |
| TD-012 | Medium | Map/geocoding provider restrictions not documented in code | Token quota abuse | Restrict tokens and monitor provider usage |
| TD-013 | Medium | User conversation history/context lacks consistent size policy | Cost/privacy risk | Add retention and payload caps |
| TD-014 | Medium | Browser errors and function telemetry not standardized | Slow incident diagnosis | Add safe structured observability |
| TD-015 | Low | Generated Supabase types need schema drift checks | Type/runtime mismatch | Regenerate and compare types in CI |

## Recommended execution order

1. **Secret hygiene:** remove tracked env file and rotate any sensitive value that appeared in history.
2. **Function abuse controls:** protect public parser with quotas, limits, validation and logging.
3. **Database authorization:** verify all RLS policies with two distinct users.
4. **AI boundaries:** schema validate requests and responses, standardize error statuses.
5. **Data integrity:** expose mock/provider/rule-based/AI provenance in reports.
6. **Test infrastructure:** add unit, component, Edge Function and RLS tests.
7. **Performance/operations:** profile, monitor and document real deployment behavior.

Do not mark debt complete based only on a documentation edit.
