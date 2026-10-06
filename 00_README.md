# OSMOO Website Master Documentation — Ultra Detailed

This folder is the implementation source of truth for the production OSMOO website and commercial platform.

## Product identity
- Product: OSMOO
- Parent company: Osmiora
- Public domain: osmoo.in
- OSMOO Pro target: $24/month
- Early access: first 500 eligible users receive 1.5 years of OSMOO Pro, enforced server-side.

## Quality bar
The website is a real software product, not a landing-page mockup. Authentication, billing, entitlements, downloads, skill distribution, developer tooling, admin, analytics, storage, and APIs must be functional, tested, observable, and secure.

## Non-negotiables
1. Never trust the browser for authorization, price, entitlement, role, or payment state.
2. Never expose admin capability through hidden URLs, frontend flags, or obscurity.
3. Every `/api/admin/*` operation requires server-side authentication, role authorization, rate limiting, audit logging, and step-up authentication for sensitive actions.
4. Uploaded files are hostile input. Enforce decompression limits, archive nesting limits, file-count limits, size limits, MIME/content verification, timeouts, and isolated processing.
5. Never extract an uploaded archive directly into a web-served directory.
6. Never execute uploaded skill code during upload validation.
7. Payment webhooks must be signature verified, replay protected, idempotent, and processed transactionally.
8. Database access must use parameterized queries/ORM protections, least-privileged credentials, TLS, backups, migration controls, and auditability.
9. Secrets belong in a secret manager/environment, never source control or client bundles.
10. Production releases must be reproducible and artifact-integrity checked.

## Implementation order
Architecture -> database -> identity -> authorization -> billing -> entitlements -> downloads -> skills -> developer portal -> admin -> frontend -> observability -> security testing -> deployment -> acceptance.

## Source-of-truth hierarchy
1. Security invariants in `10_SECURITY/*`
2. Database and API contracts in `05_BACKEND/*`
3. Product behavior in `01_PRODUCT/*`
4. UI behavior in `02_DESIGN/*`
5. QA acceptance criteria in `15_QA/*`

Where documents conflict, security and server-side correctness win over convenience.
