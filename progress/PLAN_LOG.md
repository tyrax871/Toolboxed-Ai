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
| PL-0005 | Add incremental execution sequences for large tasks | Active | High | Apply the sequence to active product and architecture work |
| PL-0003 | Define technology and architecture decisions | Active / Partial execution | Critical | Review the fixture and run measured evaluations before final architecture acceptance |
| PL-0001 | Establish the implementation and data-foundation roadmap | Active | Critical | Execute the Group 1 foundation frame before application implementation |

## Status definitions

- **Proposed** — identified but not started.
- **Active** — currently planned or being prepared.
- **Active / Partial execution** — useful outputs exist, but acceptance criteria remain incomplete.
- **Blocked** — waiting on a named decision, resource, source, or prerequisite.
- **Deferred** — intentionally postponed.
- **Completed** — acceptance criteria met and linked to execution history.

<span style="color:green">

## PL-0003 — Define technology and architecture decisions

**Status:** Active / Partial execution  
**Priority:** Critical  
**Owner:** Product and engineering planning group  
**Origin:** Approved planning target following the repository audit and implementation/data-foundation roadmap.  

### Objective

Define and document the initial technical architecture for Toolboxed before creating application code, database migrations, public APIs, or deep frontend implementation. The decisions must support the architecture-first BIM model, parameter-driven design, traceable alternatives, versioned revisions, collaboration, and the first Account and access vertical slice.

### Completed foundation

- Added `docs/architecture/TECHNOLOGY_DECISIONS.md` as a provisional architecture baseline.
- Added ADRs for application architecture, data/storage, authentication/access, background jobs/realtime, and testing/observability.
- Selected a modular-monolith starting point with durable background-job seams.
- Selected a PostgreSQL-compatible transactional database direction, object storage for large artifacts, and adapter boundaries for geometry/BIM exchange.
- Selected managed OIDC/OAuth2-capable identity as the provisional authentication direction while keeping domain authorisation in Toolboxed.
- Selected polling or server-sent events for the first vertical slice, with WebSockets deferred pending measured collaboration requirements.
- Defined layered validation and observability as first-class requirements.
- Added `docs/architecture/ARCHITECTURE_DECISION_MATRIX.md` with alternatives, provisional recommendations, acceptance evidence, risks, and review responsibilities.

### Increment 1 — Frame and design the remaining architecture decisions

**Status:** Partial — design documented; stakeholder review and measured evidence pending  
**Evidence:** `WL-0012`, commits [`a502f6d`](https://github.com/tyrax871/Toolboxed-Ai/commit/a502f6d051b711ce937b9d000a0ccf5e79a1ad11) and [`5ab8c6e`](https://github.com/tyrax871/Toolboxed-Ai/commit/5ab8c6ef0add4e88b554da43edaea158f411fdc4).  

The decision matrix defines alternatives, rationale, provisional recommendations, acceptance evidence, and review responsibilities for frontend, rendering, backend, database/spatial, geometry, BIM exchange, model granularity, identity, hosting, jobs, object storage, product fixture, scale, and performance.

### Increment 2 — Discover and define the representative architecture evaluation fixture

**Status:** Completed — fixture definition documented; review and measured evaluation pending  
**Owner:** Product and engineering planning group  
**Evidence:** `WL-0013`, fixture brief [`0e54d56`](https://github.com/tyrax871/Toolboxed-Ai/commit/0e54d56c5a72133c0355a4b1f06e8477d153a284), worklog [`773d9ef`](https://github.com/tyrax871/Toolboxed-Ai/commit/773d9efeabc49c38ca087944a2ade3274445056a).  

#### Purpose

Define a small, representative building and workload fixture that can evaluate the remaining architecture choices without creating application code or declaring provisional decisions final.

#### Completed outputs

- `docs/architecture/ARCHITECTURE_EVALUATION_FIXTURE.md` with the fixture brief, assumptions, minimum model contents, workloads, measurement protocol, traceability matrix, review checklist, exit criteria, and limitations.
- Defined a low-rise residential fixture covering site, orientation, levels, grids, rooms, walls, floors, roof, ceilings, openings, doors, windows, semantic relationships, stable identifiers, revisions, snapshots, audit events, and representative views.
- Defined evaluation dimensions for BIM semantics, spatial data, geometry, application workflows, rendering, storage, background jobs, performance, quality, and security.
- Defined reproducibility requirements for fixture version, provenance, environment, workload, repetitions, results, thresholds, limitations, and affected decisions.

#### Remaining exit work

- Obtain product, technical, BIM/domain, security, and QA review or record explicit amendments.
- Confirm or explicitly bound building typology, jurisdiction, standards, source provenance, and project assumptions.
- Create or select the fixture dataset and record its version, entities, relationships, files, and license.
- Run measured evaluations and record results before finalising architecture decisions.

#### Exit condition and acceptance criteria

This increment is complete as a planning and discovery document. It may advance to measured evaluation when the fixture is reviewed or amended with explicit owners and unblock conditions. PL-0003 remains **Active / Partial execution** until measured evidence and architecture acceptance are complete.

### Remaining PL-0003 acceptance work

- Review and amend the fixture.
- Run representative spatial, geometry, exchange, storage, rendering, and job-recovery evaluations.
- Record stakeholder decisions or named owners and unblock conditions for unresolved choices.
- Update the relevant technology baseline and ADRs with evidence-backed decisions.
- Complete product, technical, BIM/domain, security, and QA acceptance review before authorising deep implementation.

### Related records

- `WL-0008` — provisional architecture baseline and ADRs.
- `WL-0012` — architecture decision matrix and bounded design increment.
- `WL-0013` — representative architecture evaluation fixture.
- [`a502f6d`](https://github.com/tyrax871/Toolboxed-Ai/commit/a502f6d051b711ce937b9d000a0ccf5e79a1ad11) — architecture decision matrix.
- [`0e54d56`](https://github.com/tyrax871/Toolboxed-Ai/commit/0e54d56c5a72133c0355a4b1f06e8477d153a284) — fixture brief.
- [`773d9ef`](https://github.com/tyrax871/Toolboxed-Ai/commit/773d9efeabc49c38ca087944a2ade3274445056a) — worklog entry.

</span>

<span style="color:green">

## PL-0001 — Establish the implementation and data-foundation roadmap

**Status:** Active  
**Priority:** Critical  
**Owner:** Product and engineering planning group  

### Objective

Define the ordered Group 1 implementation and data-foundation sequence so readers and AI understand the first usable Toolboxed vertical slice, its domain boundaries, dependencies, contracts, validation, and acceptance evidence before implementation begins.

### Roadmap sequence

| Increment | Scope | Depends on | Exit condition |
|---|---|---|---|
| 1. Foundation frame | Confirm Group 1 boundaries, first user journey, domain modules, assumptions, and acceptance evidence | PL-0003; product and BIM plans | Group 1 scope and first vertical slice are bounded |
| 2. Account and access | Organisation, membership, invitation, roles, project permissions, tenant isolation, audit | Identity direction and access ADR | Authenticated user receives project-scoped access |
| 3. Project foundation | Project, units, standards, phases, site, orientation, and governance | Account/access and contracts | Authorised user creates a validated project |
| 4. Model foundation | IDs, entities, relationships, coordinates, levels, grids, rooms, and initial elements | Project and BIM boundaries | Connected initial model is stored and retrieved |
| 5. Revision and change | Immutable revisions, snapshots, autosave, undo/redo seams, audit, provenance | Model and storage strategy | State can be saved, recovered, compared, and audited |
| 6. Contracts and shell | Typed API, commands/queries, projections, errors, loading, accessibility, workflows | Domain and technology decisions | First workflows operate through typed contracts |
| 7. Validation and observability | Invariants, permissions, contracts, integration, logs, metrics, traces, job status | Prior increments | Required checks and operational evidence exist |
| 8. Group 1 acceptance | End-to-end project setup and initial modelling, recovery, audit, and review | Increments 1–7 | First usable slice accepted or corrective work recorded |

### First usable vertical slice

An authenticated user can enter or create an organisation context, create a project with units/standards/phase/site/orientation, define levels and grids, create and edit a small connected set of rooms and architectural elements, save working state with revision and audit history, recover a snapshot or transaction, and see permission, validation, loading, error, and recovery states.

### Acceptance criteria

- Group 1 boundary and first usable slice are explicitly approved.
- Each increment has dependencies, outputs, exit conditions, and worklog evidence.
- Domain boundaries and initial data/API contracts are documented before deep implementation.
- The central model remains the source of truth with revision and audit traceability.
- Permission, validation, accessibility, recovery, observability, and performance checks are defined and run.
- Product and engineering review authorises the next roadmap increment.

### Current next action

Execute the Foundation frame increment after reconciling its assumptions with PL-0003 Increment 2.

</span>

<span style="color:grey">

## PL-0005 — Add incremental execution sequences for large tasks

**Status:** Active  
**Priority:** High  
**Owner:** Product and engineering planning group  

The standard sequence is Frame, Discover, Design, Build, Validate, Review, and Accept or continue. Each increment requires scope, owner, dependencies, risks, outputs, exit conditions, evidence, and a worklog record. PL-0005 remains active while the sequence is being applied to current work.

**Related execution:** `WL-0011`.

## PL-0004 — Write the repository usage and plan/worklog guide

**Status:** Completed  
**Related execution:** `WL-0009`, `WL-0010`.

The repository guide explains the plan/worklog relationship, plan-first execution, traceability, history preservation, status interpretation, and incremental execution.

## PL-0002 — Establish plan-first repository execution workflow

**Status:** Completed  
**Related execution:** `WL-0007`.

The plan-first workflow is established. See the linked execution worklog and governance commits.

</span>

<span style="color:grey">

## Historical roadmap records

PL-0001 originally established the implementation and data-foundation roadmap. Its current active scope is maintained in the Group 1 roadmap above; historical execution records remain in `progress/CODING_WORKLOG.md`.

</span>
