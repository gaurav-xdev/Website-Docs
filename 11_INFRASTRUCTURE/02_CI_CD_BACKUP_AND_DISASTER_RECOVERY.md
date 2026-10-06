# CI/CD Backup and Disaster Recovery

## CI gates
Format/lint -> typecheck -> unit tests -> integration tests -> security scans -> dependency scan -> secret scan -> build -> artifact integrity -> deployment.

## Protected branches
Require review and passing checks for production.

## Artifact promotion
Build once, promote the same immutable artifact through environments where possible.

## Database recovery
Define RPO/RTO. Test point-in-time recovery. Verify backups by restoring to isolated environment.

## Disaster scenarios
Database loss, storage loss, provider outage, compromised release, leaked secret, malicious skill, domain outage.

## Compromise recovery
Revoke sessions/API keys, rotate secrets, freeze publishing, revoke releases/skills, restore trusted artifacts, communicate impact.

## Backup security
Backups are not public and use separate access credentials.
