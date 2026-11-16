# 📂 Project Structure and File Responsibilities

## Top-level folders

| Path | Purpose |
|---|---|
| `.github/` | GitHub workflows and contribution templates |
| `docs/` | Engineering, product, security and operations documentation |
| `public/` | Static assets copied by Vite |
| `src/components/` | Shared product components and UI primitives |
| `src/contexts/` | Context providers including auth |
| `src/hooks/` | Shared React hooks |
| `src/integrations/supabase/` | Supabase client and generated database types |
| `src/lib/` | Domain calculation and reporting engines |
| `src/pages/` | Route-level screens |
| `src/services/` | Market data, map, AI, geocoding and external service modules |
| `supabase/functions/` | Deno Edge Functions |
| `supabase/migrations/` | SQL schema history |
| `assets/diagrams/` | Documentation SVG diagrams |

## Route files

| File | Route |
|---|---|
| `src/pages/Index.tsx` | `/` |
| `src/pages/Opportunities.tsx` | `/opportunities` |
| `src/pages/FeasibilityReport.tsx` | `/feasibility-report` |
| `src/pages/SavedIdeas.tsx` | `/saved` |
| `src/pages/Compare.tsx` | `/compare` |
| `src/pages/IdeaAnalyzer.tsx` | `/idea-analyzer` |
| `src/pages/Auth.tsx` | `/auth` |
| `src/pages/About.tsx` | `/about` |
| `src/pages/Contact.tsx` | `/contact` |
| `src/pages/NotFound.tsx` | fallback |

## Domain library map

The `src/lib/` directory contains modules such as:
- Category intelligence.
- BizScore and score explanation.
- Competitor-quality analysis.
- Customer persona matching.
- Decision matrices.
- Failure prediction.
- Finance calculations and formatting.
- Idea enhancement.
- Reporting and report assembly.
- Risk index.
- Seasonal forecasting.
- SWOT generation.
- Comparison and recommendation engines.

The `src/services/` directory contains:
- AI client helpers.
- Competition scanner.
- Forecast engine.
- Geocoding.
- Heatmap generation.
- Market data and opportunity generation.
- Scoring.
- Trend simulation.

## Supabase layout

`supabase/config.toml` defines function JWT behavior. Function implementation lives in `supabase/functions/<function-name>/index.ts`; migrations live in `supabase/migrations/`.

## Generated files and ownership

`src/integrations/supabase/types.ts` is generated/maintained from the database schema. Prefer regenerating it from the authoritative Supabase schema after migration changes, rather than manually making divergent edits.

## Change discipline

When a new feature is added, update:
1. Route or component map if applicable.
2. API/database documentation if remote data is involved.
3. Analytics methodology and data-source register if scoring changes.
4. Security and privacy docs if new user data is collected.
5. Tests and workflows.
6. README and changelog when a user-facing capability changes.
