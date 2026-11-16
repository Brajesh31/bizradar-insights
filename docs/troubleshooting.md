# 🛠️ Troubleshooting

## Install/build
- Use Node/npm versions compatible with Vite 5.
- Remove partial node_modules and run `npm ci`.
- Do not mix lockfiles/package managers.
- Check lint/type errors at the first failing file.
- Regenerate Supabase types after schema changes.

## Supabase config
Missing URL/key: verify local `.env` names and restart Vite. Never paste values publicly.

Auth callback failure: configure Supabase site URL and redirect allowlist.

Saved records absent: inspect current user, query errors and RLS policies. Test with a second user.

## AI functions
Missing gateway key: set `LOVABLE_API_KEY` in Supabase Edge Function secrets, not browser env.

Rate limits/credits: inspect provider quota. Do not retry indefinitely.

Malformed AI output: validate JSON/schema and handle failure explicitly.

Assistant rejects request: confirm JWT, session and conversation ownership.

## Map/geocoding
Check provider token, domain restrictions, map container height, network errors, attribution and quota.

## Direct route refresh gives 404
Configure SPA rewrite to index.html for BrowserRouter routes.

## Bug report
Include steps, browser, OS, Node version, commit SHA and sanitized logs. Never include API keys, session tokens, user records or database exports.
