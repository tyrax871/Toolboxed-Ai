# Toolboxed Project Plan Log

<!-- PLAN RULE: This file records selected and documented tasks. Brainstorm ideas belong in BRAINSTORM_LOG.md. -->
<!-- PLAN RULE: Every task has a unique sequential ID in the format PL-0001, PL-0002, PL-0003, and so on. -->
<!-- PLAN RULE: Record scope, exclusions, owner, dependencies, evidence, outputs, risks, exit conditions, and acceptance criteria. -->
<!-- PLAN RULE: Distinguish planned, documented, executed, reviewed, and accepted work. -->
<!-- PLAN RULE: A plan or design document is not proof of execution, review, validation, or acceptance. -->

## Role of this log

`PLAN_LOG.md` contains ideas selected from `BRAINSTORM_LOG.md` and turned into scoped, documented tasks. It records what we want to do, why we want to do it, how we intend to do it, what evidence is needed, and what success means. It does not record unapproved brainstorming or claim that execution occurred.

## Task lifecycle

```text
BRAINSTORM_LOG.md → PLAN_LOG.md → CODING_WORKLOG.md → REVIEW_LOG.md → ACCEPTANCE_LOG.md → next task
```

## Current plan

| ID | Plan item | Status | Priority | Next outcome |
|---|---|---|---|---|
| PL-0005 | Add incremental execution sequences for large tasks | Active | High | Apply the separate-log lifecycle to active product and architecture work |
| PL-0003 | Define technology and architecture decisions | Active / Partial execution | Critical | Review the fixture, create the dataset, and run measured evaluations before architecture acceptance |
| PL-0001 | Establish the implementation and data-foundation roadmap | Active | Critical | Execute the Group 1 foundation frame before application implementation |

## Status definitions

- **Proposed** — selected idea is being considered; execution is not authorised.
- **Active** — task is planned, documented, or being executed within scope.
- **Active / Partial execution** — useful outputs exist, but review or acceptance criteria remain incomplete.
- **Blocked** — a named dependency prevents the next responsible action.
- **Deferred** — the project intentionally postpones the task.
- **Completed** — the task's scope-specific acceptance criteria are met and linked evidence exists.

<span style="color:green">

## PL-0003 — Define technology and architecture decisions

**Status:** Active / Partial execution  
**Priority:** Critical  
**Owner:** Product and engineering planning group  

### Objective

Define and document the initial technical architecture for Toolboxed before creating application code, database migrations, public APIs, or deep frontend implementation.

### Lifecycle state

- **Planned:** PL-0003 authorises architecture definition and acceptance work.
- **Documented:** The provisional baseline, ADRs, decision matrix, and evaluation fixture exist.
- **Executed:** WL-0012 and WL-0013 record the documentation increments.
- **Reviewed:** No formal review entry exists yet.
- **Accepted:** Not reached; dataset creation, measured evaluations, review, and architecture acceptance remain pending.

### Current task — review fixture and create evaluation dataset

**Status:** Active / Documented; execution not yet recorded  
**Purpose:** Review the fixture definition, resolve or assign open assumptions, and create a versioned, inspectable dataset that can be used for measured architecture evaluations.

#### Planned scope

- Inspect `docs/architecture/ARCHITECTURE_EVALUATION_FIXTURE.md`.
- Record product, technical, BIM/domain, security, and QA review decisions in `REVIEW_LOG.md`.
- Confirm or explicitly label building typology, jurisdiction, standards, units, coordinate assumptions, source provenance, and licensing.
- Create or select the smallest inspectable dataset satisfying the fixture brief.
- Record dataset version, entity and relationship counts, files, provenance, license, integrity checks, and known limitations.
- Record the executed work in `CODING_WORKLOG.md`.
- Record acceptance or corrective action in `ACCEPTANCE_LOG.md` before proceeding to measured evaluations.

#### Explicit exclusions

- No production application code.
- No database migrations or provider-specific infrastructure.
- No final framework, geometry kernel, BIM exchange, identity, queue, or hosting decision.
- No architecture acceptance based only on the fixture document.

#### Exit condition

The fixture has a recorded review outcome, and a versioned dataset exists or a documented blocker explains why creation cannot proceed. The next task is measured evaluation only after the dataset task is accepted or explicitly continued with limitations.

### Completed increments

- **Increment 1:** Architecture decision matrix and bounded design work — `WL-0012`.
- **Increment 2:** Representative architecture evaluation fixture definition — `WL-0013`, fixture commit [`0e54d56`](https://github.com/tyrax871/Toolboxed-Ai/commit/0e54d56c5a72133c0355a4b1f06e8477d153a284).
- **Progress lifecycle governance:** Separate progress logs and task lifecycle — `WL-0015`.

### Remaining acceptance work

- Review the fixture and record `RV-0001` or a corrective review entry.
- Create and inspect the versioned evaluation dataset.
- Record `WL-0016` for the dataset task.
- Record `AC-0001` or a corrective/deferred outcome before measured evaluation.
- Run spatial, geometry, exchange, storage, rendering, job-recovery, performance, quality, and security evaluations.
- Update ADRs and architecture decisions from evidence.
- Complete final product, technical, BIM/domain, security, and QA acceptance review.

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

The separate progress logs now apply the sequence Brainstorm, Plan, Document, Execute, Review, Accept, and Next task. The task lifecycle is defined in `progress/DEVELOPMENT_LIFECYCLE.md`; the governance update is recorded in `WL-0015`.

## PL-0004 — Write the repository usage and plan/worklog guide

**Status:** Completed  
**Related execution:** `WL-0009`, `WL-0010`.

## PL-0002 — Establish plan-first repository execution workflow

**Status:** Completed  
**Related execution:** `WL-0007`.

</span>
