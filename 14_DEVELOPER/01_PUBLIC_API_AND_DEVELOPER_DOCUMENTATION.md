# Public API and Developer Documentation

## Sections
Overview, authentication, quickstart, API keys, scopes, endpoints, pagination, errors, webhooks, rate limits, SDK/examples, versioning, changelog, security.

## Authentication
Use scoped API keys or OAuth-style mechanisms where appropriate. Never put secret keys in frontend code.

## API versioning
Use explicit major versioning. Deprecations have dates and migration guidance.

## Rate limits
Document limits but enforce server-side. Return standard retry guidance.

## Webhooks
Sign events, provide event IDs, timestamps, replay guidance, retry behavior, and verification examples.

## Developer security
Provide secure storage, key rotation, least privilege, and incident-response guidance.
