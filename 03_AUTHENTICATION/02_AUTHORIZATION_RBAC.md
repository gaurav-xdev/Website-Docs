# Authorization and RBAC

## Roles
USER, DEVELOPER, SUPPORT, ADMIN, SUPER_ADMIN.

## Permission examples
users.read, users.write, billing.read, billing.refund, releases.publish, skills.review, skills.publish, developers.manage, audit.read, system.configure.

## Critical rule
Roles and permissions are evaluated server-side on every protected request. Frontend route guards are UX only.

## Admin access
`/admin` being unknown or difficult to guess is not a control. A user without the required role receives a generic authorization failure. `/api/admin/*` independently enforces the same policy.

## Step-up authentication
Required for password changes by privileged users, role changes, refunds, release publication, API-key recovery, security configuration, and destructive account operations.

## Audit
Record actor, role, permission, action, resource, result, request ID, timestamp, and safe metadata.

## Separation
Support should not automatically gain payment-refund or release-publishing privileges.

## Break-glass
If implemented, use separately controlled emergency credentials, mandatory audit, expiration, and post-use review.
