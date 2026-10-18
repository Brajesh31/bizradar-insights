# BizRadar Insights

BizRadar Insights is a Vite and React business-intelligence dashboard for exploring business opportunities by location and category. It combines market scoring, forecasts, competitor analysis, category intelligence, map heatmaps, saved ideas, and Supabase authentication in a client-side application.

## Features

- Opportunity discovery and feasibility reports.
- BizScore evolution, forecast, trend, competition, category, and AI-insight panels.
- Demand, competition, and opportunity heatmap views.
- Supabase email/password sign-up, sign-in, session persistence, and sign-out.
- Saved ideas, comparison, contact, and idea-analyzer routes.
- Shadcn/Radix UI components, Tailwind CSS, Recharts, and Mapbox integration.

## Requirements

- Node.js and npm.
- A Supabase project configured with the public Vite variables described in `.env.example`.
- Mapbox configuration if map features require a live map token.

## Getting started

```powershell
npm ci
npm run dev
```

Open the Vite URL shown in the terminal. Validate the production bundle with `npm run build`; run `npm run lint` for static checks and `npm run preview` to inspect the built output.

## Routes

`/` is the landing page, `/opportunities` lists opportunities, `/feasibility-report` presents analysis, `/saved` shows saved ideas, `/compare` compares candidates, `/idea-analyzer` runs analysis, `/auth` handles authentication, and `/about` and `/contact` provide informational pages.

## Architecture and data

`src/App.tsx` composes providers and routes. `src/contexts/AuthContext.tsx` wraps Supabase Auth. Analytics engines under `src/lib/` and `src/services/` calculate scores, forecasts, distances, competitors, and heatmaps. Supabase schema, functions, and migrations live under `supabase/`. Some analytics currently use mock or rule-based data and should not be treated as financial or investment advice.

Read [SECURITY.md](SECURITY.md), [docs/installation.md](docs/installation.md), and [docs/architecture.md](docs/architecture.md) before connecting production data.

## License

MIT licensed. See [LICENSE](LICENSE).
Last updated: 2026-10-18 22:50 UTC
