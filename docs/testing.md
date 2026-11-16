# 🧪 Testing and Quality Strategy

## Current scripts

The package defines `dev`, `build`, `build:dev`, `lint` and `preview`. It does not define a dedicated unit-test command today. Add testing infrastructure before claiming unit/integration coverage.

## Recommended layers

| Layer | Scope | Suggested tooling |
|---|---|---|
| Static checks | ESLint, TypeScript, bundle | Existing commands |
| Unit | Score, finance, risk, forecast and transformation rules | Vitest |
| Component | Loading/empty/error/form states | React Testing Library |
| Integration | Supabase query and function invocation | Supabase local stack |
| RLS | User ownership boundaries | SQL tests/two-user fixtures |
| Edge Function | Validation, auth, gateway failures, quotas | Deno tests |
| E2E | Sign-in, explore, report, save, compare | Playwright |
| Accessibility | Keyboard and semantics | axe-core and manual |
| Performance | Maps, charts, routes and data | Lighthouse/React Profiler |

## Manual scenario matrix

| ID | Area | Scenario | Expected |
|---|---|---|---|
| AUTH-01 | Auth | Valid sign-up | Expected confirmation state |
| AUTH-02 | Auth | Invalid password | Safe error |
| AUTH-03 | Auth | Reload with session | Session restored |
| AUTH-04 | Auth | Sign out | User state cleared |
| LOC-01 | Location | Empty/short query | No invalid request |
| LOC-02 | Location | Select result | Coordinates/address propagate |
| OPP-01 | Opportunities | Missing required inputs | Analyze disabled |
| OPP-02 | Opportunities | Valid synthetic input | Cards render |
| SCORE-01 | Scoring | Boundary values | Documented range maintained |
| SCORE-02 | Scoring | Same input to deterministic function | Same output |
| FORE-01 | Forecast | All categories | Valid 6M/12M shape |
| MAP-01 | Map | Missing token | Safe fallback |
| REPORT-01 | Report | Missing query parameters | Clear redirect/message |
| SAVE-01 | Saved | Save as user A | Row owned by A |
| RLS-01 | Security | User B requests A row | Denied |
| AI-01 | Edge | Empty/oversized input | Rejected |
| AI-02 | Edge | Gateway 429/402/500 | Correct status handling |
| AI-03 | Edge | Invalid model JSON | Safe error |
| AI-04 | Assistant | Foreign session ID | No cross-user access |
| A11Y-01 | Accessibility | Keyboard-only path | Core actions usable |

## Local checks

```bash
npm ci
npm run lint
npm run build
```

Record exact output, commit, Node/npm versions and test environment. A successful build is not proof of provider, RLS or calculation correctness.

## Test data
Use synthetic users, fictional business ideas and mock records only. Never commit production exports, auth data, session tokens, model-provider keys or user conversation history.
