# Deployment guide

## Single-node evaluation

This installer targets a **single-machine evaluation** deployment: one Docker host, bundled PostgreSQL, no HA, no Kubernetes. It is the fastest way to try NoGira; production topologies are a separate Enterprise conversation.

## Volumes

| Volume | Purpose |
|--------|---------|
| `nogira-postgres-data` | PostgreSQL database files |
| `nogira-core-data` | NoGira instance config, uploads, and runtime state (`/data` in the core container) |

### What persists

- All workspaces, activities, and settings in PostgreSQL
- Files and instance configuration under `nogira-core-data`

### Safe reset

To destroy **all** evaluation data and start fresh:

```bash
docker compose down -v
docker compose up -d
```

Do not run `down -v` on a system you intend to keep.

## Docker Hub

Published images: [hub.docker.com/u/nogira](https://hub.docker.com/u/nogira)

| Repository | Role in evaluation compose |
|------------|----------------------------|
| `nogira/nogira-core` | API + migrations on startup |
| `nogira/nogira-ui` | Web UI |
| `nogira/nogira-notification-worker` | Background notifications |
| `nogira/nogira-mcp` | MCP server for AI clients (port **3100**) |
| `nogira/nogira-apps` | Not used by this installer |

## Upgrading NoGira (application)

All `nogira/*` images in `docker-compose.yml` must use the **same version tag** (for example `0.1.13`). Mixed versions are unsupported.

Read [CHANGELOG.md](../CHANGELOG.md) and the matching file under [docs/releases/](releases/) for what changed in each version.

1. Edit all runtime image tags in `docker-compose.yml` (`nogira-core`, `nogira-ui`, `nogira-notification-worker`, `nogira-mcp`) and `REACT_APP_VERSION` on the UI service to the target release.
2. Pull and restart:

   ```bash
   docker compose pull
   docker compose up -d
   ```

**Database schema migrations** for NoGira run **automatically** when the core container starts (`prisma migrate deploy`). You do not run SQL migrations manually for normal upgrades.

### Rollback

Set image tags back to the previous semver, `docker compose pull`, and `docker compose up -d`. Use caution: if a newer migration already ran against the database, rolling back images without restoring a database backup may fail. Back up volumes before major upgrades.

## PostgreSQL major-version upgrades (manual)

The compose file pins:

```yaml
image: postgres:14
```

**NoGira does not automatically perform PostgreSQL major-version upgrades.**

Do **not** change:

```yaml
image: postgres:14
```

to:

```yaml
image: postgres:15
```

against an existing `nogira-postgres-data` volume without following a proper [PostgreSQL major-version upgrade](https://www.postgresql.org/docs/current/upgrading.html) procedure (dump/restore or `pg_upgrade`). Changing only the image tag will typically prevent PostgreSQL from starting.

Minor updates within PostgreSQL 14 are generally safer; still back up first.

## Environment variables

Only two values are required in `.env`:

| Variable | Purpose |
|----------|---------|
| `POSTGRES_PASSWORD` | PostgreSQL password |
| `JWT_SECRET` | Signing secret for sessions |

Do not commit `.env` to version control.

## Platform support

| Environment | Evaluation support |
|-------------|-------------------|
| Linux AMD64 | Yes |
| Linux ARM64 | Yes |
| macOS (Apple Silicon) | Yes (Docker Desktop) |
| Windows | WSL2 + Docker only |

## Not included in this installer

- pgAdmin, external PostgreSQL, reverse proxy, SMTP in compose
- High availability or Kubernetes manifests

## MCP (AI clients)

The evaluation stack includes **`nogira-mcp`**. AI clients connect over HTTP:

- Local: `http://localhost:3100/mcp`
- Hosted: `https://<env>.mcp.nogira.io/mcp`

See [mcp.md](mcp.md) for client setup and available tools.

For Enterprise deployment options, contact NoGira via [www.nogira.io](https://www.nogira.io).
