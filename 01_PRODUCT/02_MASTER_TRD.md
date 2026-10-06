# OSMOO Website Master TRD

## 1. Reference architecture

Browser
-> CDN/edge/WAF
-> web application
-> authenticated API
-> domain/service layer
-> PostgreSQL
-> Redis/cache/queues
-> object storage/CDN
-> external providers (payments/email)
-> observability

Do not expose PostgreSQL, Redis, object storage, or provider credentials to browsers.

## 2. Service boundaries
- Web: rendering and interaction.
- API: authentication, authorization, domain operations.
- Worker: asynchronous jobs.
- Database: transactional source of truth.
- Object storage: immutable artifacts and controlled uploads.
- Queue: email, analytics, scans, webhook processing.
- Admin: same API security model with elevated permissions.

## 3. API principles
Version public contracts. Validate every request. Apply authorization after identity resolution and before business mutation. Use idempotency keys for retryable mutations. Return stable error codes and request IDs.

## 4. Transaction rules
Payment state changes, entitlement changes, and audit records must be transactionally coordinated or recoverable through an outbox/reconciliation pattern.

## 5. Concurrency
Use database constraints and transactions, not frontend assumptions, to prevent duplicate subscriptions, entitlement races, API-key reuse, skill-version collisions, and double processing.

## 6. Caching
Only cache data that can safely be stale. Never cache personalized responses in a shared cache without correct isolation. Never cache secrets.

## 7. Queues
Workers must be idempotent. Jobs require retry policy, dead-letter handling, maximum attempts, visibility timeout, and observability.

## 8. Configuration
Separate public build-time configuration from server secrets. Validate required configuration at startup and fail closed.

## 9. Failure modes
Provider unavailable -> preserve local transaction state and retry.
Database unavailable -> fail safe, no entitlement grant.
Storage unavailable -> no fake download success.
Email unavailable -> queue and expose recoverable state.
Webhook duplicated -> idempotency returns previous result.

## 10. Security architecture
TLS everywhere, secure cookies, CSP, CSRF strategy, strict CORS, rate limiting, WAF where available, dependency scanning, secret scanning, signed release artifacts, immutable production deployment.

## 11. Deployment
Blue/green or rolling deployment with health checks. Database migrations must be backward compatible during rollout.

## 12. API error contract
`code`, `message`, `request_id`, optional `field_errors`. Never return stack traces, SQL, secrets, provider payloads, or internal filesystem paths.

## 13. Data ownership
Every account-scoped resource has an explicit owner/workspace relation. Query helpers must require the scope rather than relying on callers to remember a WHERE clause.
