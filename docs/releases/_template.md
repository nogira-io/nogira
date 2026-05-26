# NoGira X.Y.Z

**Release date:** YYYY-MM-DD

## Added

-

## Changed

-

## Fixed

-

## Upgrade notes

- Bump all `nogira/nogira-*` image tags in `docker-compose.yml` to **X.Y.Z** (core, UI, notification-worker must match).
- Run: `docker compose pull && docker compose up -d`
- No manual SQL for NoGira schema migrations (applied on core startup).
- PostgreSQL remains pinned at `postgres:14` — do not change major version without a PostgreSQL migration procedure ([deployment.md](../deployment.md)).
