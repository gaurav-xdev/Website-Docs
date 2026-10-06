# Security Testing and Incident Response

## Automated tests
Authentication bypass, privilege escalation, IDOR, CSRF, XSS, SSRF, path traversal, malformed archives, zip bombs, webhook spoofing/replay, rate limits, API-key exposure, upload MIME confusion, oversized payloads.

## Archive security tests
- tiny compressed archive with huge expansion
- deeply nested archives
- many-file archive
- traversal names
- absolute paths
- symlinks
- duplicate entries
- corrupted archive
- encrypted archive if unsupported
- archive with executable payload
- decompression timeout case

Expected result: reject safely without excessive CPU/memory/disk use.

## Payment tests
Fake signature rejected. Replay rejected. Duplicate event produces one transition. Wrong product cannot grant Pro. Client price manipulation has no effect.

## Admin tests
Normal user cannot access admin UI data or API. Support cannot perform admin-only actions. Admin session expiration works. Sensitive action without step-up fails.

## Incident response
Detect -> contain -> preserve evidence -> rotate/revoke credentials -> eradicate -> recover -> communicate -> postmortem.

## Security release gate
Critical/high vulnerabilities and unresolved authorization bypasses block release.
