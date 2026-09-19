# Progress Logs and Repository Guide

This folder is the authoritative development narrative for Toolboxed. It tells people and AI what we might do, what we have selected to do, how the task will be done, what was actually done, how it was reviewed, and whether it succeeded.

## Progress logs

| File | Role | Lifecycle stage |
|---|---|---|
| `BRAINSTORM_LOG.md` | Ideas, problems, opportunities, alternatives, and possible tasks; no work is authorised here | Brainstorm |
| `PLAN_LOG.md` | Selected ideas turned into scoped, documented tasks with dependencies and acceptance criteria | Plan and Document |
| `CODING_WORKLOG.md` | Actual execution: files, code, configuration, tests, data, validation, limitations, and commits | Execute |
| `REVIEW_LOG.md` | Inspection of executed results against the plan and evidence requirements | Review |
| `ACCEPTANCE_LOG.md` | Final task outcome: accepted success, correction, rejection, block, or deferral; identifies the next task | Accept |
| `DEVELOPMENT_LIFECYCLE.md` | Rules connecting the logs and defining evidence for each stage | Governance |

## Task lifecycle

```text
Brainstorm → Plan → Document → Execute → Review → Accept → Next task
                  ↑         ↓        ↓
                  └── revise, correct, block, defer, or reject
```

Each task should pass through this process. A task may return to planning or correction when review finds defects, evidence is insufficient, acceptance criteria fail, new scope is discovered, or a dependency blocks progress.

### Evidence progression

- A brainstorm entry records an idea; it is not a requirement.
- A plan records selected scope and authorisation; it is not proof of execution.
- Documentation records how the task will be built or evaluated; it is not proof that it works.
- A worklog records what was executed; it is not proof that the result is satisfactory.
- A review records inspection and findings; it is not automatically acceptance.
- An acceptance entry records the final task outcome and authorises the next task.

## Plan-first task workflow

1. Capture ideas in `BRAINSTORM_LOG.md`.
2. Select an idea for development and create or update its `PL-` entry in `PLAN_LOG.md`.
3. Document the design, contracts, assumptions, evaluation method, and acceptance checks.
4. Execute only the approved bounded scope.
5. Record execution in `CODING_WORKLOG.md`.
6. Review the result in `REVIEW_LOG.md`.
7. Record success or the required next action in `ACCEPTANCE_LOG.md`.
8. Move to the next authorised task only after the current task outcome is recorded.

## What each log does

### Brainstorm log

Use it for free exploration. Record the problem, desired outcome, ideas, alternatives, assumptions, risks, and possible next actions. Entries may be selected, parked, rejected, or converted to plans. Brainstorm entries never authorise implementation.

### Plan log

Use it for selected work. A plan is a structured and documented version of an idea: it defines objective, scope, exclusions, owner, dependencies, evidence, outputs, risks, open questions, exit conditions, and acceptance criteria. Linked ADRs, design documents, contracts, and fixture briefs describe the method.

### Coding worklog

Use it for actual work. Record the exact increment, changes, validation actually performed, unperformed checks, failures, limitations, blockers, and repository evidence. The worklog must not claim that review or acceptance occurred unless those records exist separately.

### Review log

Use it after execution. Record reviewers, evidence inspected, findings, required corrections, owners, decision, and next review point. Review determines whether the result is ready for acceptance or requires further work.

### Acceptance log

Use it after review. Record the acceptance authority, criteria, evidence, limitations, outcome, follow-up plan, and next task. Only an accepted result is a success for that task. Acceptance is always scoped and does not accept the entire application.

## Current PL-0003 state

`PL-0003 — Define technology and architecture decisions` remains **Active / Partial execution**. Its baseline, matrix, and fixture definition are documented and executed as repository changes. The dataset, measured evaluations, formal review, evidence-backed ADR decisions, and architecture acceptance remain pending.

## Status and history rules

- Do not infer execution from a plan or implementation from a design document.
- Do not infer review from a commit or acceptance from a review recommendation.
- Record failed, partial, blocked, deferred, rejected, and corrected work honestly.
- Preserve all historical entries; do not rewrite history to make work appear complete.
- Link each task across brainstorm, plan, worklog, review, acceptance, and exact repository evidence.
- Keep parent plans active until their own acceptance criteria are met.
- Use the most cautious status when records disagree.

For detailed lifecycle rules and templates, see `progress/DEVELOPMENT_LIFECYCLE.md`.
