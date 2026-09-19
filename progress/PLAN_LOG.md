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
| PL-0005 | Add incremental execution sequences for large tasks | Active | High | Define and apply a repeatable sequence for breaking large plan items into accepted increments |
| PL-0003 | Define technology and architecture decisions | Active / Partial execution | Critical | Frame and design the remaining architecture decisions before implementation commitments |
| PL-0001 | Establish the implementation and data-foundation roadmap | Active | Critical | Approve architecture decisions, domain boundaries, data contracts, and Group 1 scope before implementation |

## Status definitions

- **Proposed** — identified but not started.
- **Active** — currently planned or being prepared.
- **Active / Partial execution** — approved work has produced partial outputs, but acceptance criteria are not yet complete.
- **Blocked** — waiting on a dependency, decision, resource, or source.
- **Deferred** — intentionally postponed.
- **Completed** — acceptance criteria met and linked to execution history.

<span style="color:green">

## PL-0005 — Add incremental execution sequences for large tasks

**Status:** Active  
**Priority:** High  
**Owner:** Product and engineering planning group  
**Origin:** User request to add a plan sequence for large tasks so work can be completed incrementally until the overall objective succeeds.  

### Objective

Define a repeatable plan-log sequence for large or complex work. Each sequence must divide a large objective into ordered increments with explicit entry conditions, outputs, acceptance criteria, dependencies, status, and evidence. The sequence must support honest partial progress without treating intermediate work as final success.

### Scope

- Add a standard large-task sequence to the repository guide.
- Add sequence fields and rules to this plan log.
- Show how a large plan item progresses from discovery through design, implementation, validation, review, and acceptance.
- Require each increment to be independently recorded in the worklog.
- Preserve the parent plan item as the source of overall objective and acceptance criteria.
- Explain how to handle partial, blocked, deferred, failed, and completed increments.
- Apply the sequence to future work, including the remaining PL-0003 architecture review.

### Standard sequence

| Step | Increment | Exit condition |
|---|---|---|
| 1 | Frame | Objective, scope, owner, dependencies, risks, and success criteria are recorded |
| 2 | Discover | Relevant repository files, requirements, constraints, and evidence are inspected |
| 3 | Design | Options, decisions, contracts, and acceptance tests are documented |
| 4 | Build | The approved increment is implemented within its stated scope |
| 5 | Validate | Relevant tests, checks, review, and evidence are performed and recorded |
| 6 | Review | Required stakeholders inspect the result and resolve open decisions |
| 7 | Accept or continue | Increment is accepted, corrected, blocked, deferred, or followed by the next increment |

### Acceptance criteria

- The repository guide explains the large-task sequence.
- The plan log defines parent tasks, increments, dependencies, exit conditions, and evidence.
- The worklog rules require one entry per executed increment or clearly bounded batch.
- Partial progress cannot be mistaken for overall completion.
- A future reader can identify the current increment and the next required action.
- PL-0003 remains Active / Partial execution until its open architecture choices and acceptance review are complete.

### Related plan items

- `PL-0002` — plan-first repository execution workflow.
- `PL-0003` — technology and architecture decisions.
- `PL-0004` — repository usage and plan/worklog guide.

### Related execution records

- Pending: `WL-0011`.

</span>

<span style="color:grey">

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

### Current increment — Frame and design the remaining architecture decisions

**Status:** Active  
**Owner:** Product and engineering planning group  
**Purpose:** Resolve or explicitly bound the remaining provisional architecture choices before production implementation commitments are made.

#### Scope

- Compare frontend framework and rendering-library options against the product, accessibility, BIM-viewer, team, and deployment needs.
- Compare backend language and framework options against typed contracts, domain boundaries, background jobs, validation, observability, and hiring or delivery constraints.
- Define the evaluation path for the spatial extension, geometry kernel, BIM exchange format, and model granularity.
- Compare identity, hosting, queue, and object-storage provider options while preserving adapter boundaries and avoiding premature vendor lock-in.
- Establish the initial building typology, regulatory jurisdiction, expected project and model scale, and measurable performance budgets.
- Define the stakeholder review group, decision owners, evidence required, and acceptance checklist.

#### Dependencies and evidence

- `docs/architecture/TECHNOLOGY_DECISIONS.md`
- `docs/architecture/DECISIONS/`
- `docs/architecture/BIM_ARCHITECTURE_PLAN.md`
- `docs/product/PRODUCT_PLAN.md`
- `docs/product/REFERENCE_DOCUMENT_REQUIREMENTS.md`
- Confirmed product-owner, technical-lead, BIM/domain-architect, security, and QA input where decisions affect their responsibilities.

#### Expected outputs

- Architecture decision matrix with explicit criteria, alternatives, trade-offs, and provisional or confirmed outcomes.
- Updated technology baseline and ADRs where a decision is sufficiently supported by evidence.
- Defined domain, contract, integration, performance, and operational acceptance checks for the first implementation slice.
- Recorded assumptions and unresolved questions that require stakeholder decisions rather than silent defaults.
- Review checklist identifying required reviewers, evidence, approval state, and follow-up actions.

#### Risks and open questions

- Prematurely selecting a framework, geometry kernel, or provider could create avoidable coupling.
- BIM and geometry requirements may exceed the assumptions of a conventional CRUD application.
- Building typology, jurisdiction, scale, and performance targets are not yet confirmed.
- Provider and identity choices may depend on deployment, compliance, budget, and operational ownership constraints.
- Architecture review may reveal additional scope; any new implementation scope must be planned before execution.

#### Exit condition and acceptance criteria

This increment may move to **Review** only when the decision matrix, evidence, assumptions, acceptance checks, and open questions are documented. It may move to **Accept or continue** when the required stakeholders have reviewed the decisions, unresolved items have named owners and unblock conditions, and the resulting architecture baseline is sufficient to authorise the next bounded implementation increment. PL-0003 must remain **Active / Partial execution** until its complete acceptance review is recorded.

#### Next execution record

The discovery and design work for this increment must be recorded as a new worklog entry with its own increment name, affected paths, evidence, validation, limitations, reviewer status, and commit or pull-request reference.

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
**Related execution:** `WL-0009`, `WL-0010`  

The repository guide explains the plan/worklog relationship, plan-first execution, traceability, history preservation, and status interpretation.

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
