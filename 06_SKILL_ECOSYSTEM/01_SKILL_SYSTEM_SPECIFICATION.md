# Skill System Specification

## Skill manifest
Required fields: name, slug, version, publisher, description, runtime compatibility, requested permissions, entry points, dependencies, artifact checksum, license, metadata.

## Permissions
Examples: filesystem.read, filesystem.write, browser.use, process.execute, network.request, clipboard.read, automation.control.

## Trust
Untrusted -> reviewed -> verified publisher. Trust never overrides runtime permission enforcement.

## Installation
Client downloads immutable artifact and validates checksum/signature. Server authorization decides access.

## Execution
Skills run inside the OSMOO-controlled capability boundary. A manifest permission is a declaration, not a bypass.

## Versioning
Published versions are immutable. Security revocation can block a version globally.

## Dependency policy
Pin or constrain dependencies. Detect cycles. Prevent dependency confusion by using canonical publisher/namespace identity.
