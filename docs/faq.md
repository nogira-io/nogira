# FAQ

## Is this the full NoGira source code?

No. This repository is the **public installer**: Docker Compose, documentation, and community/legal files. Application source will be published separately as part of the open-core roadmap.

## Why ship an installer before source?

Early adopters need a **simple, reproducible** way to self-host while the platform stabilises. Container images on [Docker Hub — nogira](https://hub.docker.com/u/nogira) plus this compose file prioritise install success over operational flexibility.

## Where are the Docker images?

On [Docker Hub under the `nogira` organization](https://hub.docker.com/u/nogira). The evaluation installer pulls `nogira-core`, `nogira-ui`, and `nogira-notification-worker` at the same semver tag. `nogira-apps` is published for other deployment layouts but is not part of the default compose file.

## Are all NoGira images the same version?

Yes. For each install, `nogira-core`, `nogira-ui`, and `nogira-notification-worker` must use the **identical** semver tag (for example `0.1.5`). Do not mix versions.

## Do I need to run database migrations manually?

No. NoGira applies Prisma migrations automatically when the **core** container starts, as long as `DATABASE_URL` is configured (the default compose file does this).

## Where are release notes?

See [CHANGELOG.md](../CHANGELOG.md) for the version index. Each release has a dedicated page under [docs/releases/](releases/) (for example [0.1.5.md](releases/0.1.5.md)).

## Can I upgrade PostgreSQL by editing the compose file?

Only with care. **Minor** image updates within PostgreSQL 14 may work with backups. **Major** upgrades (14 → 15) require a dedicated PostgreSQL migration procedure. See [deployment.md](deployment.md).

## Community vs Enterprise

| Edition | Summary |
|---------|---------|
| **Community** | Self-hosted core platform from published images |
| **Enterprise** | Additional capabilities, support, and deployment options — contact NoGira |

## Where do I report security issues?

Email **security@nogira.io**. Do not file public GitHub issues for vulnerabilities. See [SECURITY.md](../SECURITY.md).

## Can I use `latest` tags?

The installer pins explicit semver tags (for example `0.1.5`) for reproducibility. Floating `latest` tags are not recommended for self-hosted installs.
