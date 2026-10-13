# Architecture

This Vite application composes React routes in `src/App.tsx` with Query Client, Supabase authentication, toast providers, and shared UI primitives.

`src/contexts/AuthContext.tsx` subscribes to Supabase Auth and exposes sign-up, sign-in, session, and sign-out state. Analytics logic is separated into pure or mostly pure engines under `src/lib/` and service modules under `src/services/`. Visual components under `src/components/` render score, forecast, trend, competition, category, and map views.

Supabase client configuration is loaded from Vite environment variables. Database migrations and Edge Functions are under `supabase/`. Treat UI route checks as convenience only; authorization belongs in Supabase policies and server-side functions.
