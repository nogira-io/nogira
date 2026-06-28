# Changelog

Release notes are split by version under [`docs/releases/`](docs/releases/). This file is the index only.

## Releases

| Version | Release notes |
|---------|----------------|
| [0.4.0](docs/releases/0.4.0.md) | NG-724 P1/P4/P5-C/P11 (NGF-080/014): Agent Task + MOBA workflow seeds, Blocks propagation, stale JWT → login auth fix, MCP parent/children + typed links tools; companion: MOBA overwrite control + NG-725 MCP delivery toolkit |
| [0.3.7](docs/releases/0.3.7.md) | NG-722 P16–P21 (NGF-067/079): wiki Configure block editor — separator canonicalization, active surface, format toolbar, inter-block boundaries, block-insert split, textarea autosize; NGB-056–059 fixed |
| [0.3.5](docs/releases/0.3.5.md) | NG-722 P13 (NGF-079): ASSIGNABLE_USER assignee scoping, Scrum backlog all-types, /activities expansion + Priority default column; NGB-055 open for rank DnD |
| [0.3.4](docs/releases/0.3.4.md) | NG-722 P11/P12 (NGF-079): date-based dependency warnings and ghost schedule bars for unscheduled Plan rows |
| [0.3.3](docs/releases/0.3.3.md) | NG-722 P8/P10 (NGF-079): Plan Board timeline editing, direct dependency creation, dependency details dropdown, and connector polish |
| [0.3.2](docs/releases/0.3.2.md) | NG-723 (NGF-044/NGF-017): workspace `/plan` excludes archived activities; portfolio plan rollup aligned |
| [0.3.1](docs/releases/0.3.1.md) | NG-722 P4–P7 UI follow-on (NGF-079): nav/wiki shell persistence, create-activity stay-in-context, semantic toasts, wiki tree toast feedback |
| [0.3.0](docs/releases/0.3.0.md) | NGF-079 MCP activity operations foundation (NG-722): safe activity create/update/move/transition/comment/link/archive/restore, workspace context, and idempotent external metadata |
| [0.2.2](docs/releases/0.2.2.md) | NGF-026/067 MCP wiki attachment images (NG-721-P11): upload/list/replace/delete + figure markup sync |
| [0.2.1](docs/releases/0.2.1.md) | NGF-067 wiki layout polish (NG-721-P9): 320px tree, 240px nav, collapsible tree, Escape dismiss, tree menu z-index |
| [0.2.0](docs/releases/0.2.0.md) | NGF-067 Wiki navigation & collaboration (NG-721 P1–P8): sidebar, macros, Change Parent, DnD, MCP reparent |
| [0.1.19](docs/releases/0.1.19.md) | NGF-062 Relationships & traceability (NG-719 P1–P7, NG-720, NGB-054) |
| [0.1.18](docs/releases/0.1.18.md) | NGF-044 Archive elements in workspace (NG-715 P1–P6, NGB-052) |
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
