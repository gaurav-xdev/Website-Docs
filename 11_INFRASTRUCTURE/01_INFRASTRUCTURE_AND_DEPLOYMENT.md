# Infrastructure and Deployment

## Network
Public edge exposes only required HTTPS services. Database/cache/queues are private.

## Secrets
Use managed secret storage. Separate credentials per environment. Production credentials are never copied to local machines or CI logs.

## Deployment
Immutable application image/artifact. Health checks. Rolling/blue-green deployment. Automatic rollback on failed health checks.

## Database migrations
Run migrations as a controlled release step using a migration role. Application runtime does not have schema-admin privileges.

## Storage
Private buckets by default. Public access only for explicitly public immutable assets. Signed URLs for private artifacts.

## WAF/rate limiting
Protect login, signup, password reset, webhooks, downloads, uploads, admin, and expensive endpoints.

## Backups
Encrypted automated backups with restore tests.

## Environment isolation
Development/staging/production have separate databases, storage, secrets, payment credentials, and domains.
