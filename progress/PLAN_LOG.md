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
| PL-0007 | Map the preferred design alternative into the BIM graph | Active / Documented | High | Execute and review the mapped design-revision dataset |
| PL-0006 | Expand the evaluation dataset with design problems and alternatives | Accepted with limitations | High | Continue with BIM mapping or checksum/provenance correction |
| PL-0005 | Add incremental execution sequences for large tasks | Active | High | Apply the brainstorm-to-acceptance process to active work |
| PL-0003 | Define technology and architecture decisions | Active / Partial execution | Critical | Resolve dataset revisions, then run measured evaluations |
| PL-0001 | Establish the implementation and data-foundation roadmap | Active | Critical | Execute the Group 1 foundation frame before application implementation |

## Status definitions

- **Proposed** — selected brainstorm idea is being considered for planning.
- **Active** — task is planned, documented, or being executed within scope.
- **Active / Documented** — scope and approach are recorded; execution has not been completed.
- **Active / Partial execution** — useful outputs exist, but review or acceptance remains incomplete.
- **Blocked** — a named dependency prevents the next responsible action.
- **Deferred** — the project intentionally postpones the task.
- **Accepted with limitations** — the task met its scoped criteria while known limitations remain explicitly recorded.
- **Completed** — the task's acceptance criteria are met and linked evidence exists.

<span style="color:green">

## PL-0007 — Map the preferred design alternative into the BIM graph

**Status:** Active / Documented  
**Priority:** High  
**Owner:** Product and engineering planning group  
**Origin:** `AC-0003` follow-up from the accepted-with-limitations design-alternatives dataset.

### Objective

Convert the preferred synthetic design alternative into an explicit, traceable BIM-style element graph linked to the base fixture, while preserving the distinction between candidate design output and professional or regulatory approval.

### Planned scope

- Use `alternative-a` from `docs/architecture/architecture-evaluation-design-alternatives-v1.json` as the preferred candidate.
- Create a versioned companion dataset at `docs/architecture/architecture-evaluation-selected-design-v1.json`.
- Map the alternative to explicit levels, spaces/units, walls, floors, roof, ceilings, doors, windows, materials, views, and relationships.
- Preserve links to the design problem, alternative, comparison, and selection decision.
- Record mapping decisions where the summary does not provide enough geometry or semantics.
- Add revision, provenance, and audit records for the mapping operation.
- Clearly mark inferred or synthetic values and do not present them as source-application output.

### Explicit exclusions

- No production application code, database migrations, or runtime generation engine.
- No claim that the Architechtures application produced the mapped graph.
- No IFC export, solid geometry kernel evaluation, daylight simulation, parking analysis, accessibility certification, or regulatory review.
- No silent modification of the base v1 fixture or the accepted design-alternatives companion dataset.

### Expected outputs

- `docs/architecture/architecture-evaluation-selected-design-v1.json`
- `WL-0020` execution record
- `RV-0004` review record
- `AC-0004` acceptance or revision record

### Acceptance criteria

- The preferred alternative is linked to explicit BIM-style entities and relationships.
- Every mapped entity identifies its source alternative or an explicit inference.
- Levels, spaces/units, elements, openings, materials, views, revision, and audit records exist.
- The mapping is internally traceable and does not claim regulatory or professional approval.
- Limitations and unresolved geometry/standards assumptions are explicit.

### Exit condition

The mapped dataset is readable, traceable, reviewed against PL-0007, and accepted or returned for correction. It remains evaluation data and does not authorise production implementation.

</span>

<span style="color:grey">

## PL-0006 — Expand the evaluation dataset with design problems and alternatives

**Status:** Accepted with limitations  
**Priority:** High  

The design-problem and alternative-comparison companion dataset was executed as `WL-0019`, reviewed as `RV-0003`, and accepted as `AC-0003`. Its remaining limitations are addressed by PL-0007 and later checksum/provenance work.

## PL-0003 — Define technology and architecture decisions

**Status:** Active / Partial execution  
**Priority:** Critical  

The fixture review was accepted with limitations as `AC-0001`. The first dataset execution was recorded as `WL-0018`, reviewed as `RV-0002`, and returned for revision as `AC-0002`. PL-0006 and PL-0007 address follow-up dataset scope without silently changing earlier acceptance.

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
