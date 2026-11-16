# ❓ FAQ

**What is BizRadar?** A React/TypeScript app for business opportunity exploration and feasibility analysis.

**Is all market data live?** No. The market generator uses synthetic values with random variation. Provider-backed paths must be evaluated separately.

**Is BizScore validated?** It is heuristic scoring logic. No independent calibration/validation study is included.

**Does the product use AI?** Selected Supabase Edge Functions call the Lovable AI Gateway. Some local summaries are template-based rather than LLM-generated.

**Does the app need Supabase?** Yes for current authentication, persistence and Edge Function paths.

**Can I run without Mapbox?** Some functionality may still load, but map components may require provider configuration.

**Where should server secrets go?** Supabase Edge Function secrets, never Vite-prefixed variables.

**Why must .env be untracked?** It is environment-specific and may contain credentials/configuration. Rotate any confidential values exposed in history.

**Are automated tests present?** Current package scripts include lint/build but not a dedicated unit-test command.

**Can I rely on profit forecasts?** No. They are illustrative estimates that need independent market, cost and legal validation.

**How is deployment handled?** Build Vite, deploy dist with SPA rewrites, and separately configure Supabase schema/Auth/functions.
