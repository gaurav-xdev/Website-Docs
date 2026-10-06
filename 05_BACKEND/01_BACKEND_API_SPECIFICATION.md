# Backend API Specification

## API groups
`/v1/auth`, `/v1/account`, `/v1/billing`, `/v1/entitlements`, `/v1/releases`, `/v1/downloads`, `/v1/skills`, `/v1/developers`, `/v1/api-keys`, `/v1/admin`, `/v1/webhooks`.

## Request rules
Maximum body sizes per endpoint. Strict content types. Schema validation. Reject unknown fields for security-sensitive operations where practical.

## Pagination
Cursor pagination for mutable large collections. Stable ordering. Maximum page size enforced server-side.

## Authorization
Every handler obtains authenticated principal and resource scope before querying/mutating.

## Idempotency
Mutation endpoints that can be retried accept an idempotency key. Store request fingerprint and result.

## Rate limits
Identity, IP, account, endpoint, and expensive-operation limits can be combined.

## Webhooks
Dedicated ingress, raw-body signature verification, event ID deduplication, queue handoff, safe response semantics.

## API keys
Prefix keys for identification, store only hashes, display secret once, support scopes and revocation.

## CORS
Allow only explicitly configured origins. No wildcard credentials.

## Security headers
CSP, HSTS, frame restrictions, content-type sniffing protection, referrer policy, permissions policy.

## Observability
Every request gets a correlation/request ID. Logs exclude passwords, session cookies, authorization headers, payment secrets, and raw sensitive payloads.
