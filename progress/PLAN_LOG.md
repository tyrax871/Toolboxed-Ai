# Toolboxed Project Plan Log

<!-- PLAN RULE: This file records ideas selected from BRAINSTORM_LOG.md and expanded into documented tasks. -->
<!-- PLAN RULE: Every task has a unique sequential ID in the format PL-0001, PL-0002, PL-0003, and so on. -->
<!-- PLAN RULE: Record scope, exclusions, owner, dependencies, evidence, outputs, risks, exit conditions, and acceptance criteria. -->
<!-- PLAN RULE: A plan is not proof of execution, review, validation, or success. -->

## Role of this log

`PLAN_LOG.md` is where a loose brainstorm idea becomes a task we can understand, execute, review, and accept. It records what we want to do, why, how, and what success means. Loose ideas remain in `BRAINSTORM_LOG.md`.

## Task lifecycle

```text
BRAINSTORM_LOG.md → PLAN_LOG.md → CODING_WORKLOG.md → REVIEW_LOG.md → ACCEPTANCE_LOG.md → next task
```

## Current plan

| ID | Plan item | Status | Priority | Next outcome |
|---|---|---|---|---|
| PL-0005 | Add incremental execution sequences for large tasks | Active | High | Apply the brainstorm-to-acceptance process to active work |
| PL-0003 | Define technology and architecture decisions | Active / Partial execution | Critical | Create and review the versioned evaluation dataset before measured evaluations |
| PL-0001 | Establish the implementation and data-foundation roadmap | Active | Critical | Execute the Group 1 foundation frame before application implementation |

## Status definitions

- **Proposed** — selected brainstorm idea is being considered for planning.
- **Active** — task is planned, documented, or being executed within scope.
- **Active / Partial execution** — useful outputs exist, but review or acceptance remains incomplete.
- **Blocked** — a named dependency prevents the next responsible action.
- **Deferred** — the project intentionally postpones the task.
- **Completed** — the task's acceptance criteria are met and linked evidence exists.

<span style="color:green">

## PL-0003 — Define technology and architecture decisions

**Status:** Active / Partial execution  
**Priority:** Critical  
**Owner:** Product and engineering planning group  

### Objective

Define and document the initial technical architecture for Toolboxed before creating application code, database migrations, public APIs, or deep frontend implementation.

### Lifecycle state

- **Brainstorm:** Architecture and evaluation ideas were explored before selection.
- **Plan:** PL-0003 defines the architecture task and acceptance criteria.
- **Execute:** WL-0012, WL-0013, and WL-0016 record executed documentation and fixture-review work.
- **Review:** RV-0001 records the fixture review.
- **Accept:** AC-0001 accepts the fixture review with limitations.
- **Next task:** Create and review the versioned evaluation dataset.

### Current task — create the versioned evaluation dataset

**Status:** Active / Documented; execution not yet recorded  
**Purpose:** Create a small, inspectable dataset that satisfies the reviewed fixture and can support later measured architecture evaluation.

#### Planned scope

- Choose and document a concrete serialisation format.
- Define minimum entity and relationship counts.
- Confirm or explicitly label building type, jurisdiction, standards, units, coordinates, and professional assumptions.
- Create or select the smallest dataset satisfying the fixture.
- Record source/generator provenance, version, license, checksums, file sizes, counts, and known limitations.
- Verify that the dataset can support semantic, spatial, geometry, exchange, storage, and job evaluation tasks.
- Record execution in `CODING_WORKLOG.md`, review in `REVIEW_LOG.md`, and outcome in `ACCEPTANCE_LOG.md`.

#### Explicit exclusions

- No production application code.
- No database migrations or provider-specific infrastructure.
- No final framework, geometry kernel, BIM exchange, identity, queue, or hosting decision.
- No measured architecture acceptance from the dataset alone.

#### Exit condition

A versioned, inspectable dataset exists with provenance, integrity, counts, and limitations recorded; its result has been reviewed; and acceptance or corrective action has been recorded before measured evaluations begin.

</span>

<span style="color:green">

## PL-0001 — Establish the implementation and data-foundation roadmap

**Status:** Active  
**Priority:** Critical  
**Owner:** Product and engineering planning group  

The Group 1 roadmap defines the first usable vertical slice: account and access, project foundation, model foundation, revision/change, contracts/application shell, validation/observability, and Group 1 acceptance. Its implementation remains dependent on sufficient PL-0003 architecture evidence.

</span>

<span style="color:grey">

## PL-0005 — Add incremental execution sequences for large tasks

**Status:** Active  
**Priority:** High  

The progress process is Brainstorm, Plan, Execute, Review, Accept or revise, then Next task. The process is defined in `progress/DEVELOPMENT_LIFECYCLE.md`; the separate-log structure is recorded in `WL-0015`.

## PL-0004 — Write the repository usage and plan/worklog guide

**Status:** Completed  
**Related execution:** `WL-0009`, `WL-0010`.

## PL-0002 — Establish plan-first repository execution workflow

**Status:** Completed  
**Related execution:** `WL-0007`.

</span>
