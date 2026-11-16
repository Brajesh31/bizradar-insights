# 🔌 API and Supabase Edge Functions

## Function inventory

| Function | JWT in config | Purpose |
|---|---:|---|
| `parse-idea` | Disabled | Calls model gateway to extract structured fields from idea text |
| `generate-insights` | Enabled | Generates short insight text from opportunity metrics |
| `ai-assistant` | Enabled | Authenticated conversational assistant with per-user history |

## parse-idea

### Request
The function reads JSON containing `ideaText`.

### Processing
1. Reads `LOVABLE_API_KEY` from server environment.
2. Builds a system instruction for structured idea extraction.
3. Sends a prompt to the configured Lovable AI Gateway model.
4. Requests JSON output.
5. Parses response and returns structured fields.

Requested output includes category, niche, pricing level, target audience, capital intensity, operational complexity, keywords, unique selling points, space, staffing, inventory and technology requirements.

### Security constraints
JWT verification is disabled in the checked-in configuration. Add maximum request size, string/type validation, quotas, rate limiting, output schema validation and safe error handling. Assume this endpoint is publicly reachable unless separately restricted.

## generate-insights

### Request fields observed
Demand index, competition index, forecast growth, population density, BizScore now/12M, trend direction, category, title, competition density/count, category difficulty and opportunity type.

### Processing
- Requires `LOVABLE_API_KEY`.
- Builds a consultant-style prompt.
- Calls `google/gemini-2.5-flash` through the gateway.
- Retries selected rate-limit/network conditions.
- Returns generated insight text.

JWT verification is enabled in config. Validate field types/ranges. The current catch path can return HTTP 200 with an error-shaped body, which makes monitoring and client handling ambiguous. Prefer non-2xx status for failures.

## ai-assistant

### Request fields observed
- `message`
- `context`
- `sessionId`

### Processing
1. Reads Authorization header.
2. Creates a Supabase client carrying that Authorization header.
3. Calls `auth.getUser()`.
4. Retrieves a conversation matching session ID and authenticated user ID.
5. Builds context and prior conversation prompt.
6. Calls the model gateway.
7. Updates or inserts conversation history.
8. Returns generated assistant text.

### Security requirements
Validate message type/length, context size/keys, session ID, prior history size/roles, record ownership, rate limits and response schema. Do not return internal exception messages directly.

## CORS and HTTP handling

Inspected functions currently use `Access-Control-Allow-Origin: *` and allow Authorization, x-client-info, apikey and content-type. Where the frontend origin is known, use a specific allowlist. Browser CORS is not a replacement for authentication.

## Recommended response contract

| HTTP status | Meaning |
|---|---|
| 200 | Valid successful response |
| 400 | Invalid request data |
| 401 | Missing/invalid authentication when required |
| 403 | Authenticated but not permitted |
| 413 | Payload exceeds size limit |
| 429 | Rate/cost limit reached |
| 502/503 | Upstream provider unavailable |
| 500 | Unexpected server error |

Return safe user messages plus a correlation ID. Keep stack traces and provider internals in protected logs only.
