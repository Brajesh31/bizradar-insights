# 🔐 Security Policy

## Project classification

BizRadar Insights is a business-opportunity exploration and decision-support application. It is not a regulated financial service or a guarantee of business performance. Security reports are welcome.

## Known source-level concerns

Static inspection found:
- A tracked `.env` file in the repository.
- `parse-idea` configured with JWT verification disabled.
- Edge Functions using wildcard CORS.
- Inconsistent visible input size/type/schema validation.
- AI outputs parsed/consumed without a consistent schema-validation boundary.
- RLS behavior not independently verified against the deployed project.

See [security review](docs/security-review.md) and [threat model](docs/threat-model.md).

## Secret handling

- Treat all `VITE_*` values as public browser configuration.
- Never commit service-role keys, database passwords, AI gateway keys or private provider credentials.
- Store model/provider secrets in Supabase Edge Function secrets.
- The repository previously tracked `.env`; inspect Git history and rotate any confidential values that may have appeared there.
- Removing a file in a later commit does not erase old Git history.

## Safe usage

- Use synthetic user data for development.
- Do not share access tokens, auth cookies, private exports or user conversation history.
- Do not use business scores as guarantees or financial advice.
- Keep test projects separate from production.

## Reporting a vulnerability

Do not publish active exploit details or secrets in a public issue. Contact the maintainer privately through the GitHub profile at <https://github.com/brajesh31>. Include affected path, impact, reproduction using synthetic values and a proposed mitigation. Do not attach credentials or user records.

## Security response expectations

A maintainer should acknowledge, reproduce, assess severity, coordinate remediation, rotate exposed credentials where appropriate, verify the fix and publish a sanitized advisory when warranted.
