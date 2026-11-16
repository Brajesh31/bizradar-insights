# ⚡ Performance Engineering

## Runtime profile

The app is a React/Vite SPA with route pages, a large Radix/shadcn component surface, Recharts, Mapbox GL, local analytics modules and Supabase/Edge Function calls.

## Performance hotspots

| Surface | Potential issue | Measurement |
|---|---|---|
| First route | Large shared bundle | Vite bundle output/Lighthouse |
| Maps | Mapbox GL, heatmap point volume | Network, render and memory profile |
| Charts | Large series/re-render loops | React Profiler |
| Opportunity list | Repeated competition/scoring calculation | CPU profile |
| Geocoding | Request on every keystroke | Request count/latency |
| Supabase | Slow queries/RLS | Network timings and logs |
| AI functions | Model provider latency/retries | Function duration |

## Optimization priorities

1. Debounce geocoding and cancel obsolete requests.
2. Avoid repeating shared competition analysis in each opportunity card.
3. Lazy-load map/chart-heavy route modules where beneficial.
4. Bound heatmap grid size and input point count.
5. Paginate or virtualize long lists.
6. Memoize expensive calculations only after profiling.
7. Use Query cache policies and invalidation intentionally.
8. Add timeouts and bounded retry policies.
9. Keep loading/error states localized.
10. Record a bundle report for major dependency changes.

## Targets to measure
These are proposed budgets, not observed metrics: first route load, interaction responsiveness, map render latency, Supabase query duration, function latency, and bundle size should be tracked in CI or release review.

No verified benchmark numbers are currently included.
