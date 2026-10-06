# Admin Operations and Security TRD

## Admin threat model
Assume attackers know `/admin` and all API routes. Security must remain intact.

## Controls
MFA/passkey required for privileged accounts. Short session duration. Secure cookies. Reauthentication/step-up for sensitive mutations. Strong rate limits. Audit every mutation.

## Authorization
Use deny-by-default policy. Explicit permission matrix. No client-supplied role.

## Session isolation
Admin sessions are distinguishable and can have stricter expiration. Revocation is immediate.

## Audit
Immutable/append-oriented audit records. Protect against ordinary admins deleting their own evidence.

## Support role
Support access is narrower than admin. Avoid direct database access.

## Emergency response
Ability to disable a compromised account, revoke sessions/API keys, freeze publishing, and revoke artifacts.

## Secret handling
Admin panel must never display payment provider secrets, database credentials, signing private keys, or raw API secrets.
