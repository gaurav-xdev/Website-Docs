# Developer Portal Specification

## Developer lifecycle
Create account -> verify identity/contact requirements -> create publisher/project -> configure metadata -> upload -> automated validation -> security checks -> review -> publish.

## API keys
Generate cryptographically random secret, display once, store hash, show prefix, scope, rotate, revoke, audit.

## Upload
Never execute code. Enforce package limits and archive safety. Scan in isolation. Store immutable original.

## Publishing
A version can publish only if validation, integrity, policy, and required review gates pass.

## Abuse controls
Rate limits, upload quotas, publisher suspension, artifact revocation, audit logs.

## Developer analytics
Only expose safe aggregate usage and errors. Never leak other developers' data.
