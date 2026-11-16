# 🟩 Supabase Setup Guide

## 1. Project separation

Create a development Supabase project. Use separate projects for local, staging and production environments where possible. Never use production data in local development fixtures.

Gather the project URL and a browser-safe publishable/anon key. Keep service-role credentials and database passwords server-side.

## 2. Configure the browser client

Set in local `.env`:
- `VITE_SUPABASE_URL`
- `VITE_SUPABASE_PUBLISHABLE_KEY`

The Supabase client is instantiated in `src/integrations/supabase/client.ts`. It persists sessions in browser localStorage. This is client configuration, not the authorization boundary.

## 3. Apply migrations

Review the timestamped files in `supabase/migrations/` before applying. A safe CLI workflow is:

```bash
supabase login
supabase link --project-ref YOUR_PROJECT_REF
supabase db push
```

Use a disposable project for schema validation. Do not run destructive reset commands against production.

## 4. Authentication

The AuthContext implements email/password sign-up, sign-in, sign-out, session restoration and state-change subscription. Configure:
- Site URL and redirect allowlist.
- Email confirmation behavior.
- Password policy.
- SMTP provider.
- Rate limits and abuse protection.

## 5. Edge Functions

Functions:
- `parse-idea`
- `generate-insights`
- `ai-assistant`

Deploy:

```bash
supabase functions deploy parse-idea
supabase functions deploy generate-insights
supabase functions deploy ai-assistant
```

Set `LOVABLE_API_KEY` as a Supabase Edge Function secret. Never include it in `.env` or any `VITE_*` variable.

## 6. JWT configuration

Current `supabase/config.toml`:
- parse-idea: JWT verification disabled.
- generate-insights: JWT verification enabled.
- ai-assistant: JWT verification enabled.

The public parser requires strict validation, quotas, abuse monitoring and request-size caps. Confirm the deployed configuration, not only the source file.

## 7. Row-Level Security

For every user-owned table:
- Enable RLS.
- Select only rows where owner ID equals `auth.uid()`.
- Insert only rows owned by the authenticated user.
- Restrict update/delete to the owner.
- Do not rely on client-side filters.
- Test with two separate users and anonymous access.

## 8. Deployment verification

- [ ] Email sign-up/sign-in works.
- [ ] Session persists and sign-out clears state.
- [ ] User A cannot read User B's rows.
- [ ] JWT rules match the intended public/private model.
- [ ] Edge Function secrets configured.
- [ ] Model calls work within quota.
- [ ] CORS and function input limits reviewed.
