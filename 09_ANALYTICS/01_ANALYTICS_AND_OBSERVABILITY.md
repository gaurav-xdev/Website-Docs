# Analytics and Observability

## Product events
signup_started/completed, email_verified, download_started/completed, checkout_started/completed, subscription_changed, skill_viewed/installed, developer_submission, release_update.

## Privacy
Do not collect microphone audio, passwords, payment secrets, full task content, clipboard content, or arbitrary files as analytics.

## Event validation
Events have allowlisted names and typed properties. Reject arbitrary client property blobs.

## Observability
Structured logs, metrics, traces, error tracking, uptime checks, queue depth, webhook latency, checkout conversion, download failures.

## Correlation
Request IDs connect web request -> API -> worker -> provider event without exposing secrets.

## Alerts
Authentication abuse, webhook failures, payment reconciliation mismatch, download failures, database errors, elevated 5xx, admin security events.
