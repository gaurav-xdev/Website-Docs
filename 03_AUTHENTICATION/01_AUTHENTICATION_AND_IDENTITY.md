# Authentication and Identity

## Required flows
Sign up, verify email, login, logout, password reset, change password, email change, session listing/revocation, account deletion, optional MFA/passkey.

## Passwords
Use Argon2id or an equivalent modern password hashing configuration. Never log passwords or verification tokens.

## Sessions
Use secure, HttpOnly, SameSite cookies for browser sessions where architecture supports them. Rotate session identifiers after authentication/privilege changes. Store only hashed refresh/session tokens when persistent tokens are required.

## Recovery
Reset tokens are random, single-use, short-lived, and stored hashed. Account recovery never reveals whether arbitrary email addresses exist beyond safe UX requirements.

## Rate limits
Separate login, registration, reset, verification, and MFA attempt limits.

## CSRF
Use SameSite cookies plus CSRF protection for state-changing cookie-authenticated requests.

## Passkeys
Design identity records so passkey credentials can be added without changing user identity semantics.

## Account deletion
Require reauthentication/confirmation. Schedule deletion according to legal/operational retention requirements. Revoke sessions and API keys immediately.
