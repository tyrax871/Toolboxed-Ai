# Application Development Progress Lifecycle

This guide defines how the `progress/` folder records each Toolboxed task from idea through success. The progress folder is the authoritative development narrative for people and AI.

## The task lifecycle

```text
Brainstorm → Plan → Document → Execute → Review → Accept → Next task
                  ↑         ↓        ↓
                  └── revise, correct, block, defer, or reject
```

Every task moves through separate records. A task may not skip directly from an idea to acceptance. If evidence is insufficient or the result is unsatisfactory, the task returns to planning, correction, or a new bounded increment.

| Stage | Meaning | Primary log | Required evidence |
|---|---|---|---|
| **Brainstorm** | Capture an idea, problem, opportunity, alternative, or possible task without authorising work | `BRAINSTORM_LOG.md` | Problem, desired outcome, options, assumptions, risks, and possible next action |
| **Plan** | Select an idea for development and define its scope, dependencies, risks, outputs, and acceptance criteria | `PLAN_LOG.md` | Plan ID, owner, scope, exclusions, dependencies, evidence needed, exit condition, and acceptance criteria |
| **Document** | Describe how the planned task will be built or evaluated before execution | `PLAN_LOG.md` plus linked design/ADR/contract/fixture documents | Decisions, interfaces, assumptions, alternatives, evaluation method, and review criteria |
| **Execute** | Perform only the approved bounded task | `CODING_WORKLOG.md` | Actual changes, affected paths, validation, limitations, blockers, and commit/PR evidence |
| **Review** | Inspect the executed result against the plan and evidence requirements | `REVIEW_LOG.md` | Reviewers, evidence inspected, findings, corrections, decision, owners, and next review point |
| **Accept** | Record whether the reviewed result is satisfactory and authorise the next task | `ACCEPTANCE_LOG.md` | Acceptance authority, criteria, evidence, limitations, decision, follow-up, and next task |

## What each log does

### `BRAINSTORM_LOG.md` — ideas and possibilities

This is the least committed log. It is a safe place to think about what Toolboxed might do, problems it might solve, technical options, product opportunities, and questions. Entries are not requirements, decisions, authorisation, implementation evidence, or acceptance.

When an idea is worth pursuing, mark it **Selected for planning** and create or link a plan item.

### `PLAN_LOG.md` — selected and documented tasks

This log turns a selected idea into an actionable task. It records what we want to do, why, how it will be done, what it depends on, what evidence is needed, and what success means. The plan is similar to a structured brainstorm, but it is scoped and controlled.

A plan can be proposed, active, blocked, deferred, or completed. A plan entry is not proof that execution occurred. Design documents, ADRs, contracts, and fixture briefs linked from the plan provide the documented method.

### `CODING_WORKLOG.md` — executed tasks

This log records what actually happened in the repository. It covers documentation, code, configuration, tests, data, infrastructure, and other bounded execution. It must distinguish completed actions from unperformed checks and unresolved limitations.

A worklog entry proves that the recorded action occurred; it does not prove that the result is correct or accepted.

### `REVIEW_LOG.md` — inspected results

This log records inspection of executed work. It identifies what was examined, who reviewed it, what was found, what corrections are required, and whether the result is ready for acceptance. Review is evidence inspection, not automatic approval.

### `ACCEPTANCE_LOG.md` — success or next action

This log records the outcome after review. A result may be accepted, accepted with limitations, require correction, be rejected, blocked, or deferred. Only an accepted result is recorded as a success for that task. Acceptance is scoped to the task; it does not accept the entire application.

## Evidence rules

| Claim | Minimum evidence |
|---|---|
| Idea exists | Brainstorm entry |
| Task is planned | Plan entry with scope and criteria |
| Method is documented | Linked design, ADR, contract, fixture, or evaluation document |
| Task was executed | Worklog entry and exact repository evidence |
| Result was reviewed | Review entry naming reviewers and inspected evidence |
| Task succeeded | Acceptance entry linked to plan, worklog, review, and validation evidence |

Do not infer execution from a plan, review from a commit, or acceptance from a detailed document. Missing evidence must be recorded as missing.

## Task rules

1. Capture ideas in the brainstorm log before treating them as candidate work.
2. Select an idea into `PLAN_LOG.md` before authorising execution.
3. Document the method, contracts, assumptions, and acceptance checks before consequential implementation.
4. Execute only the approved scope and record it in `CODING_WORKLOG.md`.
5. Review the result against the plan; record failures and corrections honestly.
6. Record the acceptance decision separately; do not silently treat review as success.
7. After acceptance, select and plan the next task rather than expanding the accepted scope invisibly.
8. If a task fails, is blocked, deferred, or reveals new scope, record the outcome and create the next bounded action.
9. Preserve all historical entries. Never rewrite history to make a task appear more complete.
10. Keep parent plans active until their own acceptance criteria are met, even when one increment succeeds.

## PL-0003 example

- **Brainstorm:** Consider architecture options and evaluation needs.
- **Plan:** PL-0003 defines the architecture task and acceptance criteria.
- **Document:** The decision matrix and `ARCHITECTURE_EVALUATION_FIXTURE.md` describe the method.
- **Execute:** WL-0012 and WL-0013 record the documentation work.
- **Review:** Pending in `REVIEW_LOG.md` until required reviewers inspect the fixture and evidence.
- **Accept:** Pending in `ACCEPTANCE_LOG.md` until review, dataset creation, measured evaluations, and architecture criteria are complete.

The fixture-definition task may be accepted separately from the parent architecture plan. This preserves accurate progress.

## Record relationship

```text
BRAINSTORM_LOG.md
  → candidate idea
PLAN_LOG.md
  → selected, scoped, documented task
CODING_WORKLOG.md
  → executed task
REVIEW_LOG.md
  → inspected result
ACCEPTANCE_LOG.md
  → success, correction, rejection, block, or deferral
```

When records disagree, use the most cautious status and record the missing evidence or correction.
