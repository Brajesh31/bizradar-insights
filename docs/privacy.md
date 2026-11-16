# 🕊️ Privacy and Data Handling

## Data categories
Potential data handled by the app includes:
- Authentication email and profile metadata.
- User-entered business ideas.
- Saved idea and report attributes.
- AI assistant messages and prompt context.
- Location query strings and coordinates.
- Contact form content where submitted to a provider.

Inspect actual migrations and page handlers for exact persisted fields.

## Minimization rules
- Collect only information required for a feature.
- Avoid asking for personal identifiers in business idea descriptions.
- Do not store location histories without a product requirement.
- Limit AI history size and retention.
- Avoid logging full prompts by default.
- Never include user records in public fixtures, screenshots or issues.

## Ownership
Saved records and conversations must be isolated by authenticated owner. Use database RLS, not only query filters in React.

## Model processing
When user text/context is sent to a model gateway, disclose the purpose and relevant provider path. Send only necessary context. Model output may be wrong or incomplete.

## Retention and deletion target
Define what is stored, why, providers involved, retention length, user export/deletion, backup retention after deletion, and log redaction practices.

This guide is not a legal or compliance assessment.
