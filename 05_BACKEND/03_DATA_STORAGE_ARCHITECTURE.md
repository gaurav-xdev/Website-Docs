# Data Storage Architecture

## PostgreSQL
Transactional source of truth.

## Redis/cache
Ephemeral cache, rate limits, queue coordination. No irreplaceable source data.

## Object storage
Separate buckets/prefixes:
- public immutable web assets
- release artifacts
- private skill submissions
- processed/published skill artifacts

No executable upload is directly web-served before validation.

## Upload security
Enforce:
- maximum bytes
- maximum files
- maximum uncompressed bytes
- compression ratio limit
- maximum archive nesting
- filename normalization
- path traversal rejection
- symlink rejection
- forbidden extensions/content
- archive parser timeout
- malware/security scanning where available
- isolated temporary directory
- no execution

## Zip-bomb protection
A package is rejected if compressed size, uncompressed size, file count, nesting depth, compression ratio, or extraction time exceeds configured limits. Extraction occurs into a non-web-accessible quarantine directory. Never recursively extract archives without cumulative accounting.

## Backups
Encrypted, access-controlled, versioned, tested restore. Backup credentials differ from application runtime credentials.

## Retention
Define retention by data class; deletion jobs must be observable and retry-safe.
