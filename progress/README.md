# Progress Logs

This folder contains the Toolboxed planning log and execution worklog.

## Files in this folder

| File | Purpose |
|---|---|
| `PLAN_LOG.md` | Records what the project wants to do: priorities, milestones, dependencies, decisions, required people, data needs, deliverables, risks, and acceptance criteria. |
| `CODING_WORKLOG.md` | Records what the project has done: completed changes, files affected, implementation details, validation, limitations, blockers, status, next steps, and commits or pull requests. |
| `README.md` | Defines the governance rules for both logs. |

## Mandatory plan-first execution gate

<!-- GATE RULE: No repository change may begin until the intended work is recorded or updated in PLAN_LOG.md. -->
<!-- GATE RULE: The plan item must define scope, objective, dependencies, outputs, risks, and acceptance criteria before execution. -->
<!-- GATE RULE: User approval is required where the change is consequential, state-changing, or otherwise requires confirmation. -->
<!-- GATE RULE: Execution must stay within the approved plan scope; scope changes require a plan update before continuing. -->
<!-- GATE RULE: Every execution entry must identify the authorising PL- identifier. -->
<!-- GATE RULE: Every completed plan item must link to its WL- entry and resulting commit or pull request. -->
<!-- GATE RULE: Failed, partial, blocked, cancelled, and reverted work must be recorded honestly and cannot be marked Completed. -->
<!-- GATE RULE: Emergency work may use an exception path only when the worklog records the reason and the plan is updated retrospectively as soon as practical. -->

## Plan log rules

<!-- PLAN RULE: Update PLAN_LOG.md when intended work, priorities, dependencies, decisions, or scope changes. -->
<!-- PLAN RULE: Give every plan item a unique sequential ID in the format PL-0001, PL-0002, PL-0003, and so on. -->
<!-- PLAN RULE: Keep the current plan and active items near the top. -->
<!-- PLAN RULE: Use the statuses Proposed, Active, Blocked, Deferred, and Completed. -->
<!-- PLAN RULE: Record objective, reason, priority, dependencies, required people, data needs, deliverables, acceptance criteria, risks, and open questions. -->
<!-- PLAN RULE: Distinguish confirmed decisions from assumptions and unresolved questions. -->
<!-- PLAN RULE: Link completed plan items to the relevant CODING_WORKLOG.md entry and commit or pull request. -->
<!-- PLAN RULE: Update plan status and scope without rewriting execution history in CODING_WORKLOG.md. -->

## Execution worklog rules

<!-- WORKLOG RULE: Add an entry to CODING_WORKLOG.md whenever code, configuration, tests, documentation, planning, or repository structure changes. -->
<!-- WORKLOG RULE: Give every entry a unique sequential ID in the format WL-0001, WL-0002, WL-0003, and so on. -->
<!-- WORKLOG RULE: Include the change date in ISO format: YYYY-MM-DD. -->
<!-- WORKLOG RULE: Put the newest entry first and mark it green. -->
<!-- WORKLOG RULE: Do not delete or rewrite previous entries. Mark older entries grey so the project history remains visible. -->
<!-- WORKLOG RULE: Record what actually changed, not only what was intended. -->
<!-- WORKLOG RULE: Include the authorising Plan item: PL- identifier. -->
<!-- WORKLOG RULE: Record objective, context, detailed work completed, decisions, files and folders affected, implementation details, validation, limitations, blockers, status, next steps, and commit or pull request. -->
<!-- WORKLOG RULE: Use repository-relative paths and identify created, updated, deleted, or unchanged files where relevant. -->
<!-- WORKLOG RULE: Record failed checks, partial results, assumptions, and unperformed validation honestly. -->
<!-- WORKLOG RULE: Do not claim a test, review, validation, deployment, or approval that was not actually performed. -->

## How the logs work together

1. Identify the requested repository work.
2. Add or update the intended work in `PLAN_LOG.md`.
3. Review scope, dependencies, people, data, outputs, risks, and acceptance criteria.
4. Obtain required approval before executing consequential work.
5. Execute only the approved plan item.
6. Record actual repository or product changes in `CODING_WORKLOG.md`.
7. Add the `PL-` identifier to the worklog entry and add the `WL-` identifier to the plan item.
8. Link the resulting commit or pull request in both records.
9. Update the plan status only when the acceptance criteria and evidence justify the transition.
10. Keep plan changes and execution history separate: the plan may change as priorities evolve, while the worklog remains an immutable chronological record.

## Required plan-item format

```text
PL-0001 — Plan item title

Status:
Priority:
Owner:
Objective:
Reason:
Dependencies:
People needed:
Data or evidence needed:
Expected outputs:
Acceptance criteria:
Risks and open questions:
Related execution records:
```

## Required worklog-entry format

```text
WL-0001 — YYYY-MM-DD

Plan item: PL-0001
Change type:
Objective:
Context:
Detailed work completed:
Decisions and rationale:
Files and folders affected:
Implementation details:
Validation performed:
Limitations or blockers:
Status:
Next steps:
Commit or pull request:
```

## Colour convention

- **Green** — newest, current execution entry in `CODING_WORKLOG.md`.
- **Grey** — previous execution entries retained for history.
- **Yellow** — blocked or awaiting a decision.
- **Red** — failed validation or a known issue requiring attention.

Colour formatting is implemented in `CODING_WORKLOG.md` with HTML spans where supported by the Markdown renderer. Plan status is represented by explicit status text in `PLAN_LOG.md`.
