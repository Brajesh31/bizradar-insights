# Troubleshooting

## Supabase configuration errors

Confirm `.env` contains the correct `VITE_SUPABASE_URL` and publishable key, restart Vite after changes, and verify the development project is reachable.

## Authentication does not persist

Check browser storage policy, Supabase redirect configuration, email confirmation settings, and the AuthContext console error. Never log tokens.

## Routes return 404 after deployment

Configure the static host to rewrite client-side routes to `index.html`.

## Map or analytics output is empty

Check the selected category/location, data freshness, provider configuration, and network errors. Mock or rule-based outputs must remain clearly labeled.
