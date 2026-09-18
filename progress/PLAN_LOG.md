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
| PL-0003 | Define technology and architecture decisions | Active | Critical | Document and approve the initial application, data, storage, security, and delivery architecture |
| PL-0001 | Establish the implementation and data-foundation roadmap | Active | Critical | Approve architecture decisions, domain boundaries, data contracts, and Group 1 scope before implementation |

## Status definitions

- **Proposed** — identified but not started.
- **Active** — currently planned or being prepared.
- **Blocked** — waiting on a dependency, decision, resource, or source.
- **Deferred** — intentionally postponed.
- **Completed** — acceptance criteria met and linked to execution history.

<span style="color:green">

## PL-0003 — Define technology and architecture decisions

**Status:** Active  
**Priority:** Critical  
**Owner:** Product and engineering planning group  
**Origin:** Next approved planning target following the repository audit and the implementation/data-foundation roadmap.  

### Objective

Define and document the initial technical architecture for Toolboxed before creating application code, database migrations, public APIs, or deep frontend implementation. The decisions must support the architecture-first BIM model, parameter-driven design, traceable alternatives, versioned revisions, collaboration, and the first Account and access vertical slice.

### Reason

The repository has product and UX direction but no selected runtime, database, storage, authentication, geometry, job, deployment, or testing strategy. Making these decisions first will prevent unstable domain assumptions and duplicated frontend/backend behaviour.

### Scope of decisions

| Area | Decision required |
|---|---|
| Application shape | Confirm modular monolith boundaries and seams for later service extraction |
| Frontend | Framework, routing, state management, UI component approach, accessibility, and 2D/3D rendering boundary |
| Backend | Language, API framework, module structure, validation, error handling, and API versioning |
| Database | Relational database, migration system, transactions, indexing, and local development setup |
| Spatial and BIM data | Coordinate systems, geometry storage, spatial queries, model identity, snapshots, and exchange formats |
| File and object storage | Models, drawings, documents, exports, previews, retention, checksums, and access control |
| Identity and access | Authentication provider, sessions, invitations, account recovery, organisations, memberships, and audit integration |
| Background computation | Queue, workers, generation runs, retries, cancellation, progress, recovery, and idempotency |
| Realtime updates | Initial polling, server-sent events, or WebSocket strategy and migration path |
| Deployment | Local, test, staging, and production environments; hosting; configuration; backups; and migrations |
| Observability | Structured logs, metrics, traces, error reporting, job health, and user-visible failures |
| Testing | Unit, integration, contract, end-to-end, accessibility, performance, geometry, and generation-fixture strategy |
| Security and operations | Secrets, encryption, tenancy, retention, access reviews, disaster recovery, and export controls |

### Dependencies

- Product and UX requirements already recorded in the repository and UX artifact.
- `PL-0001` implementation/data-foundation roadmap.
- Repository audit findings.
- Expected first building typology and regulatory context.
- Expected users, organisations, model sizes, document sizes, and generation workloads.

### People needed

- Product owner or decision-maker.
- Technical lead or software architect.
- Frontend engineer.
- Backend engineer.
- BIM/domain architect.
- Geometry or computational-design specialist.
- Platform/DevOps engineer.
- Security/privacy specialist.
- QA/test engineer.
- Professional domain reviewers as available.

### Data or evidence needed

- Initial user and organisation scenarios.
- First supported project and building typology.
- Geographic and regulatory jurisdiction.
- Expected project/model scale and performance targets.
- Required 2D and 3D interactions.
- Parameter-generation workloads and reproducibility needs.
- Document, model, and export requirements.
- Security, retention, backup, and deployment constraints.
- Team skills, budget, and operating constraints.

### Expected outputs

| Path | Required output |
|---|---|
| `docs/architecture/TECHNOLOGY_DECISIONS.md` | Selected stack, alternatives considered, rationale, risks, assumptions, and open questions |
| `docs/architecture/DECISIONS/ADR-0001-initial-application-architecture.md` | Modular-monolith boundaries, modules, seams, and service-extraction criteria |
| `docs/architecture/DECISIONS/ADR-0002-data-and-storage-strategy.md` | Transactional database, spatial/BIM data, object storage, snapshots, and retention strategy |
| `docs/architecture/DECISIONS/ADR-0003-authentication-and-access.md` | Identity provider, sessions, organisations, memberships, invitations, and audit approach |
| `docs/architecture/DECISIONS/ADR-0004-background-jobs-and-realtime.md` | Generation jobs, worker lifecycle, status updates, retries, and cancellation |
| `docs/architecture/DECISIONS/ADR-0005-testing-and-observability.md` | Validation layers, test strategy, logs, metrics, traces, and operational checks |

### Acceptance criteria

PL-0003 is complete when:

1. Each critical technology area has a documented decision or an explicitly recorded unresolved decision.
2. Reasonable alternatives are considered for frontend, backend, database, storage, authentication, jobs, realtime, and deployment.
3. Decisions include rationale, consequences, risks, migration implications, and ownership.
4. The architecture supports Group 1 and the first tested vertical slice.
5. The approach protects the central BIM model, revision history, provenance, permissions, audit, and future parameter-driven generation.
6. Local development, testing, deployment, backups, and observability are described sufficiently for implementation planning.
7. The decision package is reviewed and accepted before implementation begins.

### Risks and open questions

- The first building typology and regulatory jurisdiction are not fixed.
- Geometry kernel, BIM exchange format, and spatial database strategy remain undecided.
- Authentication provider and account-recovery requirements remain undecided.
- Required 2D/3D performance targets have not been measured.
- AI generation quality, reproducibility, explainability, and compute cost require validation.
- The initial team, budget, and professional reviewers are not confirmed.
- Premature technology choices may need revision when domain and performance evidence improves.

### Related execution records

- Pending. This planning update must be recorded in the execution worklog before the plan item is considered complete.

</span>

<span style="color:grey">

## PL-0002 — Establish plan-first repository execution workflow

**Status:** Completed  
**Priority:** Critical  
**Owner:** Product and engineering planning group  
**Origin:** User-approved repository governance decision on 2026-09-18.  

### Objective

Make planning a required step before any repository work. Intended work must be recorded or updated in `progress/PLAN_LOG.md` before execution begins. Actual repository changes must then be recorded in `progress/CODING_WORKLOG.md`, with both records linked through plan and worklog IDs, affected paths, acceptance criteria, and the resulting commit or pull request.

### Completed outputs

- `progress/PLAN_LOG.md` updated with `PL-0002` and the plan/worklog relationship contract.
- `progress/README.md` updated with the mandatory plan-first execution gate and linked-record rules.
- `progress/CODING_WORKLOG.md` updated with `WL-0007` documenting the actual execution.

### Acceptance evidence

- Plan item: `PL-0002`.
- Execution record: `WL-0007`.
- Governance commit: [`cf1da35`](https://github.com/tyrax871/Toolboxed-Ai/commit/cf1da35923e56db50584cae5381cff2208e59ada).
- Supporting plan/governance commits: [`3fe3f54`](https://github.com/tyrax871/Toolboxed-Ai/commit/3fe3f54b635b1259d029a59c740e6dfc981bf9b3), [`72af443`](https://github.com/tyrax871/Toolboxed-Ai/commit/72af44396d140e17bc8a57e70564a77b77d8a1b0).

### Resulting workflow

1. Identify requested repository work.
2. Create or update a plan item.
3. Review scope, dependencies, people, data, outputs, risks, and acceptance criteria.
4. Obtain required approval.
5. Execute only the approved scope.
6. Record actual changes in the worklog.
7. Link `PL-`, `WL-`, and commit or pull request references.
8. Update plan status when evidence supports the transition.

### Limitations and follow-up

- The relationship is enforced by documented process, not automated CI validation.
- Emergency-work exception handling is documented but not automated.
- Future work may add checks for IDs, links, required fields, and unplanned changes.

</span>

<span style="color:grey">

## PL-0001 — Implementation and data-foundation roadmap

**Status:** Active  
**Priority:** Critical  
**Owner:** Product and engineering planning group  
**Origin:** Repository audit on 2026-09-18, informed by the product, BIM architecture, workflow, and UX planning documents.  

### Objective

Move Toolboxed from high-level product and UX planning toward an implementation-ready foundation. Define what the product must do, the people and roles required, the data to collect, data ownership and versioning, backend/frontend relationships, and the first tested vertical slice.

### Confirmed decisions

- Toolboxed is an architecture-first collaborative BIM platform.
- The central building model is the source of truth.
- Generated alternatives and metrics remain provisional until explicitly accepted.
- Accepted alternatives become model revisions rather than destructive replacements.
- UX groups are completed sequentially.
- Group 1, Account and access, is the first implementation milestone.
- Intended work belongs in this plan log; completed work belongs in the coding worklog.
- A modular-monolith approach with clear domain boundaries and background-job seams is the initial architecture direction, pending formal review.

### Assumptions requiring review

- A relational database will support transactional project, access, governance, and design data.
- Spatial data may require a spatial extension or dedicated geometry strategy.
- Long-running design generation requires durable background jobs.
- Models, drawings, documents, and exports require object storage.
- Polling or server-sent events may be an initial realtime strategy.

### Plan items

#### 1. Technology and architecture decisions

**Status:** Proposed · **Priority:** Critical  
**Dependencies:** Product scope and domain boundaries  
**People:** Product owner, technical lead, frontend/backend engineers, platform/DevOps, security  
**Data needed:** Runtime constraints, model sizes, user roles, deployment needs, generation workloads, security requirements  
**Expected outputs:** `docs/architecture/TECHNOLOGY_DECISIONS.md` and initial ADRs  
**Acceptance:** Frontend, backend, database, spatial data, storage, authentication, jobs, realtime, hosting, observability, and testing choices are documented with rationale, risks, and open questions.

#### 2. Core domain model

**Status:** Proposed · **Priority:** Critical  
**Dependencies:** Technology direction; product and BIM documents  
**People:** BIM/domain architect, product owner, architect, engineer, planner, builder, backend engineer, data architect  
**Data needed:** Identity, organisation, project, site, brief, parameters, constraints, model, revisions, views, documents, systems, approvals, issues, construction, and audit requirements  
**Expected outputs:** `docs/architecture/DOMAIN_MODEL.md`, relationship diagrams, lifecycle rules, invariants, ownership, and parameter-model documentation  
**Acceptance:** Each initial entity has purpose, ownership, relationships, fields, lifecycle, invariants, permissions, versioning, provenance, and archive/delete behaviour.

#### 3. Backend/frontend data contracts

**Status:** Proposed · **Priority:** Critical  
**Dependencies:** Core domain model  
**People:** Backend/frontend engineers, product owner, UX designer, QA engineer  
**Data needed:** Group 1 states, commands, queries, events, validation, permissions, errors, and frontend projections  
**Expected outputs:** `docs/architecture/DATA_CONTRACTS.md`, schemas, commands/events, errors, projections, and versioning rules  
**Acceptance:** Group 1 can be implemented from typed contracts without exposing raw database tables; validation, permissions, stale data, pagination, and job states are defined.

#### 4. Security, tenancy, permissions, and audit

**Status:** Proposed · **Priority:** Critical  
**Dependencies:** Identity, domain model, and technology direction  
**People:** Security/privacy, backend, product, QA, platform  
**Data needed:** Organisation boundaries, memberships, roles, sensitive records, approval rules, retention, and publishing permissions  
**Expected outputs:** `docs/architecture/SECURITY_AND_ACCESS.md`, tenancy, RBAC/ABAC, session, invitation, audit, retention, encryption, and export policies  
**Acceptance:** Every Group 1 action has an explicit permission rule; tenant isolation and audited security transitions are testable.

#### 5. Group 1 — Account and access

**Status:** Proposed · **Priority:** Critical  
**Dependencies:** Items 1–4, or explicitly documented provisional decisions  
**People:** UX, frontend, backend, security, QA, product  
**Data needed:** Sign-in, invitation, organisation, role, project access, rejected/expired/suspended/read-only access, sign-out, session, notification, and audit flows  
**Expected outputs:** `docs/product/UX_GROUP_01_ACCOUNT_ACCESS.md`, screen/state matrix, routes, API contract, schemas, permission matrix, and test plan  
**Acceptance:** Normal, empty, loading, error, blocked, expired, suspended, saved, read-only, and sign-out states are specified and accepted for implementation.

#### 6. First tested vertical slice

**Status:** Proposed · **Priority:** High  
**Dependencies:** Group 1 specification and initial technology direction  
**People:** Frontend, backend, QA, platform  
**Data needed:** Seed organisation, users, memberships, roles, projects, access decisions, and audit records  
**Expected outputs:** Authentication/development login, organisation selection, project list, access states, migration, API, routes, tests, and local setup  
**Acceptance:** A user can authenticate, select an organisation, view accessible projects, open a project, and receive correct denied/read-only responses with passing unit, integration, and end-to-end checks.

#### 7. Parameter-driven design data contract

**Status:** Proposed · **Priority:** High  
**Dependencies:** Core domain model, data contracts, and Group 1 project context  
**People:** BIM/domain architect, architect, data/AI engineer, backend/frontend, quantity surveyor, planner, sustainability specialist  
**Data needed:** Site, programme, room requirements, massing, circulation, performance, cost, compliance, presets, objectives, constraints, runs, alternatives, metrics, diffs, and provenance  
**Expected outputs:** Parameter/unit definitions, constraint/objective model, generation-run contract, alternative/metric schema, model-diff and impact contract, explainability rules  
**Acceptance:** A brief can be saved, validated, versioned, submitted, monitored, compared, and accepted as a new revision without overwriting approved information.

#### 8. Project setup and BIM model foundations

**Status:** Deferred until Items 1–7 are accepted · **Priority:** High  
**Dependencies:** Domain model, data contracts, vertical slice, parameter contract, and geometry strategy  
**People:** BIM/domain architect, geometry engineer, frontend/backend, QA, architect, engineer  
**Data needed:** Site, levels, grids, rooms, walls, floors, roofs, doors, windows, components, views, revisions, geometry, relationships, and exchange requirements  
**Expected outputs:** Project setup, central model schema, geometry/coordinate strategy, model workspace, generated-view foundation, validation, and snapshots  
**Acceptance:** A permitted user can create a project, define site and levels, create a basic model, save revisions, inspect views, and recover prior states with tested model integrity.

### Cross-cutting data requirements

Core records should identify, where applicable: stable ID and entity type; organisation and project scope; actor, owner, timestamps, and source; status and version; units and coordinate system; validation and confidence; provenance; permissions; dependencies; audit events; and retention/archive/delete behaviour.

### Risks and open questions

- Geometry kernel, BIM exchange format, and spatial database strategy are undecided.
- First building typology and geographic/regulatory jurisdiction are not fixed.
- Authentication provider and account recovery are not fixed.
- Required 2D/3D interaction fidelity and performance are not measured.
- AI quality, reproducibility, explainability, and professional validation need domain testing.
- Cost, energy, planning, and code results must be labelled as estimates or validated results.
- Implementation team and professional reviewers are not yet confirmed.

### Overall completion gate

Move from planning into implementation only when technology decisions, core entities and invariants, data contracts, security rules, Group 1 specification, vertical-slice validation plan, and parameter-driven data contracts are accepted.

### Related execution records

- `progress/CODING_WORKLOG.md` — `WL-0006` records the data-infrastructure planning direction.
- The repository audit was completed on 2026-09-18; no implementation commit is associated with this plan item yet.

</span>
