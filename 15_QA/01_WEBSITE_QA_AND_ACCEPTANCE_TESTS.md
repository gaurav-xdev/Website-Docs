# Website QA and Acceptance Tests

## A. Authentication
- New signup succeeds.
- Duplicate/invalid signup handled safely.
- Verification token expires and is single-use.
- Login rate limits trigger.
- Session revocation works.
- Password reset token cannot be reused.
- Normal user cannot access another account.

## B. Admin
- Anonymous cannot access admin.
- Normal user cannot access admin.
- Support cannot perform admin-only mutations.
- Admin API independently enforces role.
- Sensitive mutation without step-up fails.
- Audit record exists for successful/failed privileged actions.
- Admin cannot delete/alter audit evidence through ordinary UI.

## C. Payment
- Client cannot change price.
- Invalid provider signature rejected.
- Replay event rejected/idempotent.
- Duplicate event creates no duplicate entitlement.
- Delayed webhook does not produce false success.
- Refund/cancel updates entitlement according to policy.
- Early-access cap cannot be exceeded under concurrent checkout attempts.

## D. Database
- Runtime DB credential cannot perform migrations.
- Public network cannot reach DB.
- Injection tests fail safely.
- Foreign-key/unique constraints prevent duplicate state.
- Backup restore succeeds.

## E. Upload/zip bomb
- Oversized upload rejected.
- Oversized decompressed archive rejected.
- High compression-ratio archive rejected.
- Excessive file count rejected.
- Deep nesting rejected.
- `../` path rejected.
- absolute path rejected.
- symlink rejected.
- corrupted archive rejected.
- extraction timeout is bounded.
- no extracted file becomes web-executable.
- uploaded code is never executed during scanning.

## F. Skills
- Permission declaration required.
- Untrusted skill cannot obtain undeclared capability.
- Revoked skill is blocked.
- Paid skill cannot be unlocked locally.
- Published version is immutable.

## G. Downloads/update
- Wrong platform artifact cannot install.
- checksum mismatch blocks install.
- signature mismatch blocks install.
- revoked release is blocked.
- interrupted download recovers.
- failed update preserves previous version where supported.

## H. Frontend
- Responsive desktop/tablet/mobile.
- Keyboard navigation.
- Reduced motion.
- Screen-reader labels.
- Loading/error/empty states.
- No sensitive information in browser console.

## I. API
- Schema validation.
- Authorization.
- rate limits.
- pagination limits.
- CORS.
- CSRF where applicable.
- secure headers.
- no stack traces.

## J. Release acceptance
Release is blocked by critical/high security failures, broken payment state transitions, broken authentication, broken download integrity, data-loss bugs, or unauthorized admin access.

## Final gate
All required CI checks pass, production configuration is validated, migrations are tested, backups are restorable, monitoring is live, and release artifacts are checksummed/signed.
