# Entitlements and Subscriptions TRD

## Data model
Subscription represents provider commercial state. Entitlement represents application access. Do not conflate them.

## Granting
Entitlement is granted only from verified server events or controlled admin action.

## Early access
First-500 logic must be atomic: reserve/grant against a database constraint/transaction so concurrent checkouts cannot exceed the cap.

## Entitlement projection
Frontend receives safe fields: entitlement type, active status, start/end timestamps, limits. Never expose internal provider secrets.

## Revocation
Cancellation/expiry/refund can revoke future access according to product policy. Existing local app access should be governed by signed entitlement/update policy where applicable.

## Audit
Every grant, change, and revoke is traceable to source event or privileged actor.

## Idempotency
Repeated webhook delivery produces exactly one logical state transition.
