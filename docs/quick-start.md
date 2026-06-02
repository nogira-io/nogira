# Quick start

For product overview and positioning, see the [repository README](../README.md).

## What you get

A **single-node evaluation** stack:

- PostgreSQL 14 (bundled, internal network only)
- NoGira Core (API, port **4000**)
- NoGira UI (port **3000**)
- Notification worker (background jobs; same data volume as core)
- NoGira MCP (AI clients, port **3100**)

## Docker images

NoGira runtime images are on [Docker Hub — nogira](https://hub.docker.com/u/nogira):

| Image | Used by this installer |
|-------|-------------------------|
| [nogira/nogira-core](https://hub.docker.com/r/nogira/nogira-core) | Yes |
| [nogira/nogira-ui](https://hub.docker.com/r/nogira/nogira-ui) | Yes |
| [nogira/nogira-notification-worker](https://hub.docker.com/r/nogira/nogira-notification-worker) | Yes |
| [nogira/nogira-mcp](https://hub.docker.com/r/nogira/nogira-mcp) | Yes |
| [nogira/nogira-apps](https://hub.docker.com/r/nogira/nogira-apps) | No (other topologies) |

`docker compose pull` downloads the pinned tags from `docker-compose.yml`.

## Install

1. Install Docker and Docker Compose v2.
2. Clone this repository and enter the directory.
3. Copy `.env.example` to `.env`.
4. Set `POSTGRES_PASSWORD` and `JWT_SECRET` in `.env`.
5. Run:

   ```bash
   docker compose up -d
   ```

6. Open **http://localhost:3000**.
7. Complete the setup wizard to create the first administrator account.

First startup may take one to two minutes while the database initializes and migrations apply.

## Ports

| Service | URL |
|---------|-----|
| UI | http://localhost:3000 |
| API | http://localhost:4000 |
| MCP | http://localhost:3100/mcp |

## Reset (wipe all local data)

```bash
docker compose down -v
docker compose up -d
```

You will need to run the setup wizard again.

## Next steps

- [deployment.md](deployment.md) — upgrades, volumes, PostgreSQL notes
- [mcp.md](mcp.md) — connect Cursor/AI clients via MCP
- [faq.md](faq.md) — editions and open core
