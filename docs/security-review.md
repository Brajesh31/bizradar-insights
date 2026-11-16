# 🔐 Security Review

This is a static source review, not a penetration test. Verify deployed Supabase policies/configuration independently.

| Priority | Finding | Evidence | Risk |
|---|---|---|---|
| High | `.env` tracked | Repository tree includes .env | Project configuration public; rotate confidential values and remove from history |
| High | parse-idea JWT verification disabled | supabase/config.toml | Public model endpoint can be abused/costly |
| High | Wildcard CORS in Edge Functions | Function source | Broad browser origin access |
| High | Limited visible request/schema constraints | Edge Function handlers | Oversized/malformed input and cost abuse |
| High | User-provided context/history passed to AI | ai-assistant | Prompt manipulation, payload/privacy issues |
| Medium | Internal error text returned | Function catch blocks | Information leakage |
| Medium | generate-insights error path responds HTTP 200 | Function source | Monitoring/client may treat failure as success |
| Medium | Synthetic/random data rendered as market metrics | marketData and forecast engines | Misleading decisions |
| Medium | UI route guards are not authorization | React pages | Must rely on RLS and JWT |
| Medium | Public map tokens need provider restrictions | map configuration | Quota abuse |

## Immediate remediation
1. Remove `.env` from tracking and ignore it.
2. Inspect Git history; rotate any confidential values ever committed.
3. Rate-limit and quota-control public `parse-idea`.
4. Validate payload types, ranges, and sizes for every function.
5. Restrict CORS to known frontend origins when feasible.
6. Test RLS with two users and anon.
7. Validate AI output shape before use.
8. Return consistent error statuses and generic client messages.
9. Avoid logging prompts, user PII and tokens unless explicitly necessary and protected.

## Verification checklist
- [ ] Provider/service secrets absent from client build.
- [ ] User A cannot access User B records.
- [ ] Anonymous parser has quotas/size limits.
- [ ] JWT-required functions reject invalid tokens.
- [ ] Function payloads are schema-validated.
- [ ] CORS origin policy reviewed.
- [ ] Error responses contain no secrets or stack traces.
