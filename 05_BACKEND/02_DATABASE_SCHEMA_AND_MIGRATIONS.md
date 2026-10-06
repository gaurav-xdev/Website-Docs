# Database Schema and Migrations

## Core tables
users
- id UUID
- email_normalized
- email_verified_at
- password_hash nullable
- status
- created_at
- updated_at
- deleted_at nullable

sessions
- id
- user_id
- token_hash
- expires_at
- created_at
- revoked_at
- last_seen_at
- device metadata safe subset

identities/passkeys
- id
- user_id
- provider/credential identifier
- credential public key data
- timestamps

subscriptions
- id
- user_id
- provider
- provider_customer_id
- provider_subscription_id
- product_id
- status
- period_start/end
- cancel_at_period_end
- timestamps

payment_events
- id
- provider
- provider_event_id UNIQUE
- event_type
- signature_verified
- received_at
- processed_at
- processing_status

entitlements
- id
- user_id
- type
- source
- status
- starts_at
- ends_at
- metadata
- timestamps

releases
- id
- version
- platform
- architecture
- channel
- artifact_id
- checksum
- signature metadata
- published_at
- revoked_at

skills
- id
- publisher_id
- slug UNIQUE
- status
- current_public_version
- created_at

skill_versions
- id
- skill_id
- version
- manifest
- artifact_id
- checksum
- scan_status
- review_status
- published_at

developer_accounts
- id
- user_id
- status
- verification metadata

api_keys
- id
- developer_id
- prefix
- key_hash
- scopes
- created_at
- last_used_at
- revoked_at

audit_logs
- id
- actor_user_id
- action
- resource_type
- resource_id
- result
- request_id
- metadata_safe
- created_at

analytics_events
- id
- anonymous/user reference
- event_name
- properties_safe
- occurred_at

## Database security
Use separate application DB roles for runtime and migrations. Runtime role cannot create/drop schemas. Production DB is private-network only. TLS is required.

## Constraints
Unique provider event IDs, unique normalized email, unique release tuple, unique skill version, foreign keys, check constraints for status fields.

## Migrations
Use versioned migrations, test from empty database and from latest production-like snapshot, and use expand/contract for breaking changes.
