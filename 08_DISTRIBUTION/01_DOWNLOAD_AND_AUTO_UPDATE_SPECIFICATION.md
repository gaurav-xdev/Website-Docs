# Download and Auto Update Specification

## Release artifact model
Every release has version, platform, architecture, channel, checksum, signature, artifact URL, release notes, minimum supported version, and publication/revocation state.

## Download authorization
Server returns a short-lived signed download URL or controlled proxy response. Never expose bucket credentials.

## Artifact integrity
Client verifies SHA-256 and preferably a publisher signature before installation.

## Update security
Manifest is retrieved over TLS, validated against a trusted signing key, and rejected if expired, malformed, downgraded unexpectedly, or revoked.

## Rollout
Support staged channels if needed: stable, beta, dev.

## Failure recovery
Download interruption resumes/restarts safely. Failed installation retains previous working version when possible.

## Revocation
Compromised release can be revoked and blocked by manifest policy.
