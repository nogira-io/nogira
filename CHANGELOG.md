# Changelog

Release notes are split by version under [`docs/releases/`](docs/releases/). This file is the index only.

## Releases

| Version | Release notes |
|---------|----------------|
| [0.1.17](docs/releases/0.1.17.md) | NGF-052 Workspace Whiteboards (NG-714 P1–P7) |
| [0.1.16](docs/releases/0.1.16.md) | NG-713.4 Manage Users full name column and Edit User full name editing |
| [0.1.15](docs/releases/0.1.15.md) | NGF-051 user lifecycle (self-delete, archive/anonymize, Manage Users source column, wizard gate, email reuse fix) |
| [0.1.14](docs/releases/0.1.14.md) | NGF-048 Event Challenge Engine (presenter/attendee flows, PlatformEvent scoring) |
| [0.1.13](docs/releases/0.1.13.md) | NGF-026 MCP (`nogira-mcp`, PAT/Cursor docs) |
| [0.1.12](docs/releases/0.1.12.md) | NGF-046 complete: plan polish, wiki Mermaid, rich activity description, portfolio ↔ development rollup |
| [0.1.11](docs/releases/0.1.11.md) | NGF-046 polish: global FTS search, My Work deeplinks, Scrum parity, onboarding wizard + catalog v5 |
| [0.1.10](docs/releases/0.1.10.md) | Hosted/self-hosted catalogue seeds on core startup; workspace create fails loud on template clone errors |
| [0.1.9](docs/releases/0.1.9.md) | Portfolio workspace templates (SAFe/Waterfall), PHASE rename, simulator portfolioTemplate |
| [0.1.8](docs/releases/0.1.8.md) | Home workspace create, user Development workspace policy, Manage Users delete & edit password |
| [0.1.7](docs/releases/0.1.7.md) | Development workspace edition (environment, sprint, child table) |
| [0.1.6](docs/releases/0.1.6.md) | Activity detail rail, planning dates, priority scheme & defaults |
| [0.1.5](docs/releases/0.1.5.md) | Wiki (workspace pages, markdown, attachments) |
| [0.1.4](docs/releases/0.1.4.md) | Scrum board (sprints, backlog, metrics) |
| [0.1.3](docs/releases/0.1.3.md) | Plan view (timeline, milestones, releases) |
| [0.1.2](docs/releases/0.1.2.md) | Kanban board |
| [0.1.1](docs/releases/0.1.1.md) | Hosted demo instance |
| [0.1.0](docs/releases/0.1.0.md) | Workspace views and self-serve setup |
| [0.0.3](docs/releases/0.0.3.md) | Elemental workspace and basic settings |
| [0.0.2](docs/releases/0.0.2.md) | Platform configuration (types, fields, flows, screens, schemes) |
| [0.0.1](docs/releases/0.0.1.md) | Notification system foundation |
| [0.0.0](docs/releases/0.0.0.md) | Core API and product UI foundation |

**Upgrade:** see [docs/deployment.md](docs/deployment.md). Application schema migrations run automatically on core startup; edit image tags in `docker-compose.yml` together (same semver on core, UI, notification-worker, and nogira-mcp).
