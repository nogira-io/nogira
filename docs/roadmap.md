# Roadmap

This roadmap is **directional** and may evolve based on customer feedback, enterprise requirements, and community adoption. It describes **outcomes**, not internal implementation details.

For version history of what shipped in each installer release, see [CHANGELOG.md](../CHANGELOG.md).

---

## Current Capabilities

### Core platform

- Activities and workflow management (create, edit, transitions, parent/child links)
- Visual **workflow builder** with versioning, publish flow, and reusable statuses
- **Status categories** and usage validation across flows
- **Kanban** boards with column mapping, drag-and-drop, and assignee filters
- **Scrum** boards — backlog, sprints (plan/active/complete), ceremonies, metrics, and velocity trends
- **Workspace hierarchy** — portfolio, program, development, and custom workspace types
- **Portfolio workspaces** — cross-workspace activity and plan rollup, child-workspace discovery
- **Role-based access control** — global roles plus workspace Guest / Member / Manager / Owner
- **Self-enrollment** and access-request flows; first-run **setup wizard** for new instances
- **Plan view** — timeline, milestones, releases, and workspace planning markers (MVP)
- **Workspace insights** — operational signals for workspace health
- **Development workspace edition** — environment, sprint, and child-activity surfaces for delivery teams
- **Onboarding desk** — guided first-session tasks and catalog-driven provisioning
- **Event challenges** — live presenter-led sessions, join tokens, missions, and scoring (**NGF-048**)

### Knowledge management

- **Workspace wiki** — hierarchical pages, Markdown editing, attachments, and workspace search
- **Wiki Mermaid** diagrams in pages
- **Rich activity descriptions** (Markdown) on detail and browse surfaces
- **File attachments** on activities and wiki
- **Full-text search** (Postgres FTS + trigram) across activities and wiki
- **Global search** with filters, column configuration, and CSV export
- **Comments** on activities

### Operations

- **Saved searches and views** — private and shared filter configurations
- **My Work** — personal quadrants and quick-filter deep links into search
- **Favorites** — workspaces, boards, and saved views
- **SMTP integration** and outbound email delivery
- **Notification engine** — domain events, job queue, and dedicated notification worker
- **Global notification policies** (system settings)
- **Workspace notification schemes** — matrix-driven rules and collaboration mail
- **Global and workspace permission matrices** — configurable RBAC with audit-friendly changes
- **Workspace lifecycle** — archive, restore, and governed permanent purge for workspaces
- **Board archive** (soft) on the boards hub
- **Account center** — profile, password, avatar, and workspace memberships
- **Personal Access Tokens** for API, CLI, and MCP clients

### AI and integration

- **MCP Server** — Streamable HTTP for Cursor, Claude Desktop, and other MCP clients (**NGF-026**)
- **MCP tools (MVP1)** — search, wiki read/update, activity read/update with PAT passthrough
- **Live event challenge** onboarding for workshops and conferences

### Installer (this repository)

- Single-node **Docker Compose** evaluation stack with pinned Hub images
- Automatic application schema migrations on core startup
- Public docs for install, upgrade, MCP, and challenge administration

---

## Planned

The sections below describe what we intend to build next. Ordering across themes is reflected in [Near-term priorities](#near-term-priorities).

### Collaboration and knowledge

- Archive and restore **activities** (**NGF-044**)
- Archive and restore **wiki pages** with consistent “Archive” terminology (**NGF-044**)
- Activity ↔ wiki linking
- Wiki **page version history**
- Rich wiki macros (engineering-focused, not a Confluence clone)
- **Mentions** and cross-references (**NGF-018**)
- **Tags** on activities and related entities
- **Activity history / audit log** UI maturity (**NGF-003**)
- Co-editing and live wiki collaboration (explicitly out of scope for current wiki MVP)

---

### Planning and dependencies

Portfolio and plan foundations exist today (milestones, releases, portfolio rollup). The next evolution focuses on **planning depth** for portfolio managers:

- **Activity dependencies** (finish-to-start and related links) (**NGF-049**)
- **Cross-workspace** planning on portfolio timelines (**NGF-049**)
- Interactive **timeline scheduling** — bar resize, schedule-from-row, marker alignment (**NGF-049**)
- **Roadmap view** enhancements beyond the current MVP plan board (**NGF-017** follow-on)
- **Prioritization** workspace (Jira Product Discovery–style ideas → delivery) (**NGF-047**)
- **Capacity planning** (basic) (**NGF-020**)
- **Time tracking** (**NGF-019**)

---

### Enterprise and governance

Outcomes below are packaged commercially via **Enterprise Edition** where noted.

- **Custom roles** beyond fixed workspace roles (**NGF-039**)
- **LDAP** directory integration
- **SAML / OIDC** authentication and external identity providers
- **Enterprise Edition** — advanced governance, commercial support, and licensing (not a public “license generator”)
- **Audit capabilities** and stronger activity history (**NGF-003**)
- **Email template management** with global defaults and workspace overrides (**NGF-015** follow-on)
- **Advanced permissions model** — finer-grained policy (**NGF-039**)

*Already in Community Edition:* workspace archive/restore/purge, permission matrices, notification policies, and admin user lifecycle (create, invite, disable).

---

### Migration and adoption

- **Jira** importer / migration tool (**NGF-032**, **NGF-033**)
- **Confluence**-oriented content migration (paired with wiki evolution)
- **Excel** and **Word** importers for bulk adoption scenarios
- Expanded **onboarding** catalog parity and enterprise rollout playbooks (**NGF-011** extensions)

---

### Ecosystem and extensibility

- **Marketplace** for apps and extensions (**NGF-029**)
- **Plugin SDK** and app ecosystem growth (**NGF-040**)
- **Public APIs** and partner integrations (beyond PAT + MCP MVP1)
- **Webhooks** and event subscriptions
- **MCP integrations** enrichment — additional tools and surfaces (**NGF-034**)
- **Release manifest** for deterministic hosted deployments (**NGF-042**)
- Multi-architecture image adoption on Docker Hub (AMD64 + ARM64 installer parity)

---

### AI and agent collaboration

- **AI chat** inside NoGira (**NGF-030**)
- **AI-assisted planning** and documentation
- **Self-hosted LLM** support (customer-controlled models)
- **AI agent orchestration** (**NGF-031**)
- **AI-driven development workflows** and advanced boards (**NGF-036** MOBA concept)
- **Advanced search** — natural language and AI-assisted discovery (**NGF-035**)

*Already available:* MCP Server, PAT auth, and tool-based read/update for AI clients on your infrastructure.

---

### Infrastructure

- **High availability** deployments (**NGF-038**)
- **Kubernetes** deployment guides and reference topologies
- **Multi-node** and advanced enterprise deployments
- Dedicated **documentation site** (beyond this installer repo)
- Application **source publication** under the open-core model (separate repositories)

*Supported today for evaluation:* single-node Compose on Linux AMD64/ARM64 and macOS Apple Silicon (see [deployment.md](deployment.md)).

---

## Near-term priorities

Relative **value** and **effort** are qualitative guides for sequencing — not engineering estimates.

| Priority | Capability | Value | Effort |
|----------|------------|-------|--------|
| 1 | Entity archive system (activities, wiki, boards) | Very High | Low |
| 2 | Activity ↔ Wiki links | Very High | Low |
| 3 | Wiki version history | Very High | Low |
| 4 | Rich wiki macros | Very High | Low |
| 5 | Planning dependencies & advanced timeline | Very High | Medium |
| 6 | Jira importer | Very High | Medium |
| 7 | Custom roles | Very High | Medium |
| 8 | LDAP / OIDC / SAML | Very High | Medium |
| 9 | Enterprise Edition | Very High | Medium |
| 10 | Public APIs | High | Low |
| 11 | Marketplace | Very High | High |
| 12 | AI Chat | High | Medium |
| 13 | MCP enrichment | High | Medium |
| 14 | AI Agent Orchestration | High | High |
| 15 | AI Development Board (MOBA) | High | High |

---

## What we do not publish here

Internal-only topics stay out of this public roadmap, for example: license-key generators, internal worker orchestration design, proprietary MCP adapter internals, and unreleased enterprise implementation checklists. Those appear as **outcomes** above when relevant to buyers and operators.

---

Questions or enterprise interest: [www.nogira.io](https://www.nogira.io).
