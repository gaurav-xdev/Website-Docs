# Payments and Billing PRD

## Provider
Current commercial integration target: Dodo Payments. Provider access occurs only from trusted server infrastructure.

## Checkout
Server creates checkout session from a server-known product/price ID. Browser receives only the safe checkout redirect/session information.

## Never trust
Do not accept amount, currency, product ID, subscription tier, discount, or entitlement from browser JSON as authoritative.

## Billing lifecycle
Created -> pending -> active -> past_due/grace -> canceled/expired/refunded where applicable.

## Webhooks
Verify provider signature against raw request body. Reject stale/replayed events. Persist provider event ID before processing. Process idempotently.

## Reconciliation
Periodic server-side reconciliation compares local subscriptions against provider state and flags discrepancies.

## Refunds
Privileged operation, step-up auth, explicit target display, reason, audit, and provider confirmation.

## Fast payment UX
Keep checkout creation synchronous and lightweight. Move email, analytics, and secondary work to background jobs.

## Failure
If payment succeeds at provider but webhook is delayed, show pending verification rather than granting access from the browser.
