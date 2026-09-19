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
| PL-0003 | Define technology and architecture decisions | Active / Partial execution | Critical | Define and evaluate the representative architecture fixture before final architecture acceptance |
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

**Status:** Active  
**Owner:** Product and engineering planning group  
**Purpose:** Define a small, representative building and workload fixture that can be used to evaluate the remaining architecture choices without creating application code or declaring provisional decisions final.

#### Fixture scope

Use a small low-rise residential building model based on the existing product and BIM context. The fixture must define, at minimum:

- Site boundary, orientation, survey/reference coordinates, setbacks, and constraints.
- Levels, grids, reference geometry, and project units.
- Rooms/spaces with names, areas, zones, occupancy, and relationships.
- Walls, floors, slabs, roofs, ceilings, openings, doors, and windows.
- Materials or assemblies sufficient to test semantic relationships and derived properties.
- Existing, new, proposed, relocated, and superseded states where relevant.
- Stable identifiers, relationships, provenance, revision, snapshot, and audit examples.
- Representative views: site plan, floor plan, section, elevation, and a simple 3D/model view.

#### Evaluation dimensions

| Dimension | Evidence to define |
|---|---|
| BIM and semantics | Entity inventory, relationships, stable IDs, revision rules, IFC provenance, unsupported-property reporting |
| Spatial data | Coordinates, levels, room/element containment, site queries, spatial indexes, migration and recovery cases |
| Geometry | Wall, opening, room, section, view, validity, and derived-property operations; kernel boundary and licensing review |
| Application | Account access, project setup, model setup, save, revision, audit, snapshot, undo/redo seam, and recovery states |
| Rendering | 2D workspace readiness, selection/linking, optional isolated WebGL evaluation, memory and frame-time observations |
| Storage | Upload/download authorization, metadata, checksums, retention, signed access, orphan repair, and provenance |
| Jobs | Import/export or validation job payload, retry, restart recovery, idempotency, cancellation, progress, and failure states |
| Performance | API latency, workspace readiness, autosave acknowledgement, memory, representative query plans, and worker throughput |
| Quality and security | Permission negatives, tenant isolation, accessibility, error recovery, redaction, auditability, and review evidence |

#### Required fixture documentation

The fixture brief must record:

- Building typology and project assumptions.
- Jurisdiction, standards, units, and regulatory assumptions, or explicit unresolved status.
- Source/reference files or generated fixture provenance.
- Entity counts, relationship counts, model size, file size, and expected workload profile.
- Test environment, hardware/network profile, tools, versions, and licensing constraints.
- Pass/fail thresholds or observations for each evaluation dimension.
- Named decision owners, reviewers, unresolved questions, and unblock conditions.

#### Expected outputs

- `docs/architecture/ARCHITECTURE_EVALUATION_FIXTURE.md` describing the fixture, assumptions, dataset, workloads, evidence, and acceptance checks.
- A fixture-to-decision traceability matrix linking each workload to the architecture decision it informs.
- Evaluation checklist for product, technical, BIM/domain, security, and QA review.
- Follow-up worklog entry documenting discovery, evidence, limitations, and next decisions.
- Updates to the technology baseline and ADRs only where measured evidence justifies a change.

#### Dependencies

- `docs/architecture/TECHNOLOGY_DECISIONS.md`
- `docs/architecture/ARCHITECTURE_DECISION_MATRIX.md`
- `docs/architecture/BIM_ARCHITECTURE_PLAN.md`
- `docs/architecture/DECISIONS/`
- `docs/product/PRODUCT_PLAN.md`
- `docs/product/REFERENCE_DOCUMENT_REQUIREMENTS.md`
- PL-0001 Group 1 roadmap and first usable vertical slice.

#### Risks and open questions

- The building type, jurisdiction, and professional assumptions may require product-owner confirmation.
- A small fixture may not predict enterprise-scale model behaviour; scale-up fixtures must be planned separately.
- Geometry and IFC requirements may expose scope beyond the first implementation slice.
- Licensing, provider, hosting, and team constraints may change technology recommendations.
- Benchmark results without a recorded environment or workload are not sufficient acceptance evidence.

#### Exit condition and acceptance criteria

This increment is ready for review when the fixture brief, workload definitions, assumptions, evaluation dimensions, environment requirements, pass/fail or observation criteria, owners, and unresolved questions are documented. It is ready to continue to measured evaluation when the required reviewers accept the fixture scope or record explicit amendments. PL-0003 remains **Active / Partial execution** until the resulting evidence and architecture review are complete.

#### Next action

Create the fixture brief and record it in a new worklog entry before building evaluators, application code, migrations, or provider-specific infrastructure.

### Remaining PL-0003 acceptance work

- Confirm or explicitly bound the initial building typology, jurisdiction, professional assumptions, and project fixture.
- Run representative spatial, geometry, exchange, storage, rendering, and job-recovery evaluations.
- Record stakeholder decisions or named owners and unblock conditions for unresolved choices.
- Update the relevant technology baseline and ADRs with evidence-backed decisions.
- Complete product, technical, BIM/domain, security, and QA acceptance review before authorising deep implementation.

### Related records

- `WL-0008` — provisional architecture baseline and ADRs.
- `WL-0012` — architecture decision matrix and bounded design increment.
- [`a502f6d`](https://github.com/tyrax871/Toolboxed-Ai/commit/a502f6d051b711ce937b9d000a0ccf5e79a1ad11) — architecture decision matrix.
- [`5ab8c6e`](https://github.com/tyrax871/Toolboxed-Ai/commit/5ab8c6ef0add4e88b554da43edaea158f411fdc4) — worklog entry.

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
