# Toolboxed Project Plan Log

<!-- PLAN RULE: This file records intended work, priorities, dependencies, decisions, and acceptance criteria. -->
<!-- PLAN RULE: Keep current and active items near the top. -->
<!-- PLAN RULE: Give every plan item a unique sequential ID: PL-0001, PL-0002, PL-0003, and so on. -->
<!-- PLAN RULE: Update status as Proposed, Active, Blocked, Deferred, or Completed. -->
<!-- PLAN RULE: Do not use this file as a record of completed implementation; link completed items to CODING_WORKLOG.md. -->
<!-- PLAN RULE: Distinguish confirmed decisions, assumptions, open questions, and blockers. -->

## Current plan

| ID | Plan item | Status | Priority | Next outcome |
|---|---|---|---|---|
| PL-0003 | Define technology and architecture decisions | Active / Partial execution | Critical | Review provisional architecture baseline and resolve open technology choices |
| PL-0001 | Establish the implementation and data-foundation roadmap | Active | Critical | Approve architecture decisions, domain boundaries, data contracts, and Group 1 scope before implementation |

## Status definitions

- **Proposed** — identified but not started.
- **Active** — currently planned or being prepared.
- **Active / Partial execution** — approved work has produced partial outputs, but acceptance criteria are not yet complete.
- **Blocked** — waiting on a dependency, decision, resource, or source.
- **Deferred** — intentionally postponed.
- **Completed** — acceptance criteria met and linked to execution history.

<span style="color:green">

## PL-0003 — Define technology and architecture decisions

**Status:** Active / Partial execution  
**Priority:** Critical  
**Owner:** Product and engineering planning group  
**Origin:** Next approved planning target following the repository audit and the implementation/data-foundation roadmap.  

### Objective

Define and document the initial technical architecture for Toolboxed before creating application code, database migrations, public APIs, or deep frontend implementation. The decisions must support the architecture-first BIM model, parameter-driven design, traceable alternatives, versioned revisions, collaboration, and the first Account and access vertical slice.

### Execution completed so far

- Added `docs/architecture/TECHNOLOGY_DECISIONS.md` as a provisional architecture baseline.
- Added ADRs for application architecture, data/storage, authentication/access, background jobs/realtime, and testing/observability.
- Selected a modular-monolith starting point with durable background-job seams.
- Selected a PostgreSQL-compatible transactional database direction, object storage for large artifacts, and adapter boundaries for geometry/BIM exchange.
- Selected managed OIDC/OAuth2-capable identity as the provisional authentication direction while keeping domain authorisation in Toolboxed.
- Selected polling or server-sent events for the first vertical slice, with WebSockets deferred pending measured collaboration requirements.
- Defined layered validation and observability as first-class requirements.

### Current provisional decisions

- Modular monolith with explicit domain modules.
- Typed HTTP API with command/query separation.
- PostgreSQL-compatible database; spatial extension remains open.
- Stable model identifiers, immutable revisions, explicit coordinate systems, and geometry adapters.
- S3-compatible object storage with database metadata, checksums, ownership, and retention.
- Managed OIDC/OAuth2 authentication with application-owned organisations, memberships, roles, and project permissions.
- Durable workers for generation, metrics, imports, exports, and heavy validation.
- Polling or server-sent events initially; WebSockets deferred.
- Structured logs, metrics, traces, error reporting, and user-visible job status.
- Domain, contract, integration, end-to-end, accessibility, visual-state, performance, and recovery testing.

### Expected outputs

| Path | Result |
|---|---|
| `docs/architecture/TECHNOLOGY_DECISIONS.md` | Created as the provisional baseline |
| `docs/architecture/DECISIONS/ADR-0001-initial-application-architecture.md` | Created |
| `docs/architecture/DECISIONS/ADR-0002-data-and-storage-strategy.md` | Created |
| `docs/architecture/DECISIONS/ADR-0003-authentication-and-access.md` | Created |
| `docs/architecture/DECISIONS/ADR-0004-background-jobs-and-realtime.md` | Created |
| `docs/architecture/DECISIONS/ADR-0005-testing-and-observability.md` | Created |

### Acceptance review still required

PL-0003 remains Active / Partial execution because the following remain open:

- Frontend framework and rendering libraries.
- Backend language and framework.
- Exact spatial extension, geometry kernel, BIM exchange format, and model granularity.
- Identity, hosting, queue, and object-storage providers.
- Initial building typology, regulatory jurisdiction, scale targets, and performance budgets.
- Review by the product owner, technical lead, BIM/domain architect, security, and QA representatives.

### Related execution records

- `WL-0008` — provisional architecture baseline and ADRs.
- Technology decision commits: [`413a7ba`](https://github.com/tyrax871/Toolboxed-Ai/commit/413a7ba749aec3a376eeb4027991536595bac10d), [`f3016dd`](https://github.com/tyrax871/Toolboxed-Ai/commit/f3016dde24e48d14f2211b3e80466f1d36ae399a), [`63b734f`](https://github.com/tyrax871/Toolboxed-Ai/commit/63b734f95c61d9d2b5997459c67fb059fa57b7b7), [`4101224`](https://github.com/tyrax871/Toolboxed-Ai/commit/4101224f0f144688bfaeafc0dc4042005970de23), [`6f20c7d`](https://github.com/tyrax871/Toolboxed-Ai/commit/6f20c7dcc7d17d764e7995508909638aa17029d1), [`5ecbf86`](https://github.com/tyrax871/Toolboxed-Ai/commit/5ecbf863c5830a984eb880bb7b40110c6324f535).

</span>

<span style="color:grey">

## PL-0004 — Write the repository usage and plan/worklog guide

**Status:** Completed  
**Priority:** High  
**Owner:** Product and engineering planning group  
**Origin:** User request to make repository usage and the distinction between intended work and completed work understandable to readers.  

### Objective

Create a clear guide explaining how to use the Toolboxed GitHub repository, how to read and update the plan log, how to read and update the execution worklog, and how plan items, worklog entries, commits, and acceptance status relate.

### Completed outputs

- Added the reader-friendly repository guide to `progress/README.md`.
- Explained the plan log as the record of intended work and the worklog as the record of actual repository changes.
- Documented the plan-first workflow, authorising plan items, traceability, history preservation, and review order.
- Added detailed guidance for interpreting Proposed, Active, Active / Partial execution, Blocked, Deferred, and Completed statuses.
- Added decision rules distinguishing Partial from Blocked, Deferred, and Completed.
- Documented the acceptance gate for marking work Completed.
- Preserved `PL-0003` as Active / Partial execution.

### Acceptance evidence

- `WL-0009` — initial repository usage guide.
- `WL-0010` — detailed plan-status interpretation guidance.
- Guide commit: [`c1547f5`](https://github.com/tyrax871/Toolboxed-Ai/commit/c1547f55c6388a99a20d4c3e0f79e8ba0e35e6e2).
- Earlier plan and guide commits: [`9489ab8`](https://github.com/tyrax871/Toolboxed-Ai/commit/9489ab8c53cc1fb8f647501937bb4e2404d5ace3), [`aff27c6`](https://github.com/tyrax871/Toolboxed-Ai/commit/aff27c61d1c1e1df88514343c5ee45be11a15a52).

</span>

<span style="color:grey">

## PL-0002 — Establish plan-first repository execution workflow

**Status:** Completed  
**Priority:** Critical  
**Owner:** Product and engineering planning group  
**Related execution:** `WL-0007`  

The plan-first workflow is established. See the linked execution worklog and governance commits for the full record.

</span>

<span style="color:grey">

## PL-0001 — Implementation and data-foundation roadmap

**Status:** Active  
**Priority:** Critical  
**Owner:** Product and engineering planning group  

The roadmap remains active. Its eight workstreams are tracked in the repository history and this plan log.

</span>
