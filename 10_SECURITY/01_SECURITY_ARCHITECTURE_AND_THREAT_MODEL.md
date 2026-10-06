# Security Architecture and Threat Model

## Threat categories
1. Account takeover.
2. Admin takeover.
3. Broken access control/IDOR.
4. Payment manipulation.
5. Webhook spoofing/replay.
6. Zip bombs/decompression bombs.
7. Malicious skill uploads.
8. Path traversal.
9. SSRF.
10. XSS/CSRF.
11. SQL/NoSQL injection.
12. Secret leakage.
13. Supply-chain compromise.
14. Malicious release update.
15. Denial of service.
16. Privilege escalation.

## Zip bomb defense
Treat every archive as hostile. Check compressed size, expected uncompressed size, cumulative extracted bytes, file count, compression ratio, nesting depth, and extraction time. Enforce hard ceilings. Extract only in isolated quarantine storage. Reject absolute paths, `..`, symlinks/hardlink-like entries, and unexpected file types. Never execute extracted content.

## SSRF defense
For server-side URL fetching: allow only required protocols, resolve DNS safely, block localhost/private/link-local/metadata ranges, re-check after redirects, restrict ports, enforce response-size/time limits, and use an egress proxy where appropriate.

## IDOR defense
Never fetch `/users/{id}` merely because the user is authenticated. Scope queries by authenticated principal/tenant and permission.

## XSS
Output encoding, framework escaping, strict HTML sanitization for rich content, CSP, and no unsafe HTML insertion by default.

## CSRF
SameSite plus CSRF tokens/origin checks for cookie-authenticated state changes.

## SQL injection
Parameterized queries/ORM. Never interpolate user input into SQL identifiers or clauses without allowlists.

## Secrets
Secret manager, short-lived credentials where possible, secret scanning, rotation, redaction.

## Supply chain
Lock dependencies, scan vulnerabilities, verify release artifacts, require protected CI branches and signed releases.

## Admin
Assume route discovery. Enforce security server-side.

## Database
Private network, TLS, least-privileged runtime role, migration role separation, backups, auditing, no direct public exposure.
