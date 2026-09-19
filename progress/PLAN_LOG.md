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
| PL-0006 | Expand the evaluation dataset with design problems and alternatives | Active / Documented | High | Execute and review the reference-driven dataset companion |
| PL-0005 | Add incremental execution sequences for large tasks | Active | High | Apply the brainstorm-to-acceptance process to active work |
| PL-0003 | Define technology and architecture decisions | Active / Partial execution | Critical | Resolve the dataset revision, then run measured evaluations |
| PL-0001 | Establish the implementation and data-foundation roadmap | Active | Critical | Execute the Group 1 foundation frame before application implementation |

## Status definitions

- **Proposed** — selected brainstorm idea is being considered for planning.
- **Active** — task is planned, documented, or being executed within scope.
- **Active / Documented** — scope and approach are recorded; execution has not been completed.
- **Active / Partial execution** — useful outputs exist, but review or acceptance remains incomplete.
- **Blocked** — a named dependency prevents the next responsible action.
- **Deferred** — the project intentionally postpones the task.
- **Completed** — the task's acceptance criteria are met and linked evidence exists.

<span style="color:green">

## PL-0006 — Expand the evaluation dataset with design problems and alternatives

**Status:** Active / Documented  
**Priority:** High  
**Owner:** Product and engineering planning group  
**Origin:** Loose idea added to `BRAINSTORM_LOG.md`, informed by the public Architechtures reference application.

### Objective

Extend the architecture evaluation dataset beyond final BIM elements so it represents an AI-assisted design workflow: a site and development brief produce constrained design alternatives, which are compared and optionally selected before being represented as BIM elements.

### Planned scope

- Create a versioned companion dataset linked to `architecture-evaluation-fixture-v1.json`.
- Represent the design problem: site, development brief, program, constraints, objectives, and generation parameters.
- Represent at least two generated alternatives with footprints, floor/unit summaries, metrics, constraint results, provenance, and comparison fields.
- Represent a selected or unselected outcome without claiming professional or regulatory approval.
- Link alternatives to the existing BIM fixture or clearly record when a link is not yet materialised.
- Record the Architechtures website as a product-workflow reference, not as a copied implementation or proprietary data source.
- Preserve the existing v1 dataset; do not silently replace or broaden its acceptance.

### Explicit exclusions

- No authenticated access, scraping, reverse engineering, or copying of proprietary application data.
- No claim that the reference application's internal algorithms or schemas are known.
- No final planning-law, jurisdiction, code-compliance, or professional design decision.
- No runtime generation engine, optimisation algorithm, application code, or measured performance evaluation.
- No modification of the previously reviewed v1 dataset in this task.

### Expected outputs

- `docs/architecture/architecture-evaluation-design-alternatives-v1.json`
- Worklog execution record
- Review record covering structure, traceability, provenance, and limitations
- Acceptance or corrective outcome before measured evaluation

### Acceptance criteria

- Dataset records site/program inputs, constraints, objectives, and generation parameters.
- At least two alternatives are comparable using explicit metrics.
- Constraint results distinguish pass, warning, fail, and unknown.
- Alternative provenance and relationship to the base BIM fixture are explicit.
- Reference use is documented without claiming access to private internals.
- Limitations, checksum state, licensing, and unresolved assumptions are recorded.

### Exit condition

The companion dataset is readable, linked to the base fixture, reviewed against this plan, and accepted or returned for correction. It does not by itself accept the architecture or authorise deep implementation.

</span>

<span style="color:grey">

## PL-0003 — Define technology and architecture decisions

**Status:** Active / Partial execution  
**Priority:** Critical  

The fixture review was accepted with limitations as `AC-0001`. The first dataset execution was recorded as `WL-0018`, reviewed as `RV-0002`, and returned for revision as `AC-0002`. PL-0006 addresses the new reference-driven scope without silently changing the v1 acceptance.

## PL-0005 — Add incremental execution sequences for large tasks

**Status:** Active  
**Priority:** High  

The progress process is Brainstorm, Plan, Execute, Review, Accept or revise, then Next task. The process is defined in `progress/DEVELOPMENT_LIFECYCLE.md`; the separate-log structure is recorded in `WL-0015`.

## PL-0001 — Establish the implementation and data-foundation roadmap

**Status:** Active  
**Priority:** Critical  

The Group 1 roadmap remains dependent on sufficient PL-0003 architecture evidence.

## PL-0004 — Write the repository usage and plan/worklog guide

**Status:** Completed  
**Related execution:** `WL-0009`, `WL-0010`.

## PL-0002 — Establish plan-first repository execution workflow

**Status:** Completed  
**Related execution:** `WL-0007`.

</span>
