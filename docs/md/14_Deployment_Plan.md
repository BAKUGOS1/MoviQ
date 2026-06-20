# MoviQ Deployment Plan

## Environments

- Local development
- Staging
- Production

## Core Services

- Web app
- API service
- Worker service
- Render service
- Supabase database/auth
- Object storage
- Temporal server/cloud
- Observability stack

## Deployment Requirements

- Separate runtime configuration per environment.
- Database migrations must be reviewed before production.
- Storage buckets must separate raw uploads, working files and exports.
- Render jobs must use deterministic artifact paths.
- Health checks are required for API, worker and render service.
- Rollback strategy must exist for app and service deployments.

## Production Readiness

- Domain configured
- Secrets configured outside code
- RLS enabled
- Logs and traces available
- Backup and retention policy defined
- Smoke tests pass after deployment
