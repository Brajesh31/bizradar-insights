# Application interfaces

The browser routes are `/`, `/opportunities`, `/feasibility-report`, `/about`, `/contact`, `/auth`, `/saved`, `/compare`, and `/idea-analyzer`. Unknown routes render `NotFound`.

Supabase Auth provides email/password sign-up, sign-in, session lookup, auth-state events, and sign-out. Supabase database and Edge Function contracts are defined by the SQL migrations and function source under `supabase/`. Keep generated types in sync with schema changes and enforce access with RLS.
