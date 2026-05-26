# NoGira

**Modern self-hosted project management platform.**  
Built for teams that want control, speed, and simplicity.

**Single-node evaluation deployment** — install in minutes with Docker Compose.

---

## Quick start

**Prerequisites:** [Docker](https://docs.docker.com/get-docker/) and Docker Compose v2.

**Container images** are published on [Docker Hub — nogira](https://hub.docker.com/u/nogira) (`nogira/nogira-core`, `nogira/nogira-ui`, `nogira/nogira-notification-worker`). This installer pins a single semver on all three (see `docker-compose.yml`).

```bash
git clone https://github.com/nogira-io/nogira.git
cd nogira
cp .env.example .env
```

Edit `.env` and set:

- `POSTGRES_PASSWORD` — database password (choose a strong value)
- `JWT_SECRET` — long random string (session signing)

Then start NoGira:

```bash
docker compose up -d
```

Open **http://localhost:3000** and complete the **setup wizard** (create your first administrator).

**Done.** API is on **http://localhost:4000**.

See [docs/quick-start.md](docs/quick-start.md) for more detail.

---

## Editions (open core)

| Edition | Description |
|---------|-------------|
| **Community** | Core self-hosted platform — workspaces, workflows, boards, and collaboration features shipped in the Community image set |
| **Enterprise** | Advanced features, SSO, HA, governance, and commercial support — [contact NoGira](https://www.nogira.io) |

NoGira follows an **open-core** model. This repository is the **installer**; application source publication will evolve on a separate roadmap.

---

## Source code

The public installer repository is available first while the platform stabilises.  
Application source publication will follow separately as part of the NoGira open-core roadmap.

---

## Hosted demo

Request access to a hosted demo: **https://www.nogira.io** (early access / demo).

---

## Upgrade

Application database migrations run **automatically** when the core container starts.

To upgrade NoGira: edit the image tags in `docker-compose.yml` (all `nogira/*` services must use the **same version**), then:

```bash
docker compose pull
docker compose up -d
```

See [docs/deployment.md](docs/deployment.md) for volumes, rollback, and PostgreSQL lifecycle.

---

## Documentation

| Doc | Topic |
|-----|--------|
| [docs/quick-start.md](docs/quick-start.md) | First install |
| [docs/deployment.md](docs/deployment.md) | Upgrade, volumes, platform support |
| [CHANGELOG.md](CHANGELOG.md) | Release index → [docs/releases/](docs/releases/) |
| [docs/faq.md](docs/faq.md) | Editions, installer vs source |
| [docs/roadmap.md](docs/roadmap.md) | Product direction (high level) |

---

## Support matrix (evaluation)

| Environment | Support |
|-------------|---------|
| Linux **AMD64** | Supported (Docker Hub multi-arch) |
| Linux **ARM64** | Supported |
| macOS Apple Silicon | Supported for evaluation |
| Windows | **WSL2** + Docker only |

---

## Legal

- [LICENSE](LICENSE) — Apache-2.0 (installer repository)
- [SECURITY.md](SECURITY.md) — responsible disclosure
- [TRADEMARKS.md](TRADEMARKS.md) — brand use
- [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md)
- [CONTRIBUTING.md](CONTRIBUTING.md)
