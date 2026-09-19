# Application Development Progress Lifecycle

This guide defines the process for developing Toolboxed one task at a time. The `progress/` folder is the authoritative record of what we might do, what we selected, what we did, what we found, and whether the result worked.

## Development process

```text
Brainstorm → Plan → Execute → Review → Accept or revise → Next task
```

The process is deliberately simple:

1. **Brainstorm** loosely about something we might want.
2. **Plan** the idea in enough detail to know what we are trying to do and how we will judge it.
3. **Execute** the documented plan within its agreed scope.
4. **Review** the result against the plan and inspect the evidence.
5. **Accept or revise** the result: record success if it worked, or record corrections, rejection, blockage, or deferral.
6. **Move to the next task** only after the current outcome is recorded.

Documentation happens while the idea is expanded into a plan. It is not a separate execution stage that a task must pretend to complete independently.

## What each log does

| Log | What it records | What it does not record |
|---|---|---|
| `BRAINSTORM_LOG.md` | Loose ideas, questions, possibilities, problems, and conversation-style notes | Requirements, approved scope, decisions, or completed work |
| `PLAN_LOG.md` | Ideas selected for exploration, expanded into objectives, scope, approach, dependencies, risks, evidence, and acceptance criteria | Actual execution, review findings, or success |
| `CODING_WORKLOG.md` | What was actually done, including changed files, implementation, validation, limitations, and commits | Whether the result was satisfactory or accepted |
| `REVIEW_LOG.md` | Inspection of the executed result, evidence, findings, corrections, and review decision | Final acceptance unless acceptance is recorded separately |
| `ACCEPTANCE_LOG.md` | Whether the plan worked: accepted, accepted with limitations, revise, rejected, blocked, or deferred; plus the next task | Unrecorded assumptions or a claim that the whole application is complete |
| `DEVELOPMENT_LIFECYCLE.md` | The process and evidence rules connecting the logs | A substitute for task-specific records |

## Stage rules

### 1. Brainstorm

Use `BRAINSTORM_LOG.md` as a loose scratchpad. A thought can be a sentence, question, bullet, or short conversation. Do not force it into a formal template. Brainstorming is intentionally incomplete and non-authorising.

When an idea is worth exploring, copy or reference it in `PLAN_LOG.md` and expand it there.

### 2. Plan

Use `PLAN_LOG.md` to turn the selected idea into a task. Define:

- Objective and reason.
- Scope and exclusions.
- Owner and dependencies.
- Approach or design documents needed.
- Evidence and validation needed.
- Risks, assumptions, and open questions.
- Exit condition and acceptance criteria.
- The next responsible action.

The plan is where the idea becomes understandable and executable. A plan may include linked ADRs, designs, contracts, fixtures, or datasets when needed.

### 3. Execute

Execute only the documented plan scope. Record actual work in `CODING_WORKLOG.md`, including:

- Plan ID and task name.
- Files, code, data, configuration, or infrastructure changed.
- Commands, checks, tests, or measurements actually run.
- Failed or unperformed checks.
- Limitations, blockers, and deviations.
- Exact commit, pull request, or other evidence.

A worklog proves that the work happened. It does not prove that the plan worked.

### 4. Review

Use `REVIEW_LOG.md` to inspect the executed result against the plan. Record:

- Plan and worklog references.
- Reviewers or review responsibility.
- Evidence inspected.
- Findings and failures.
- Required corrections or follow-up.
- Whether the result is ready for acceptance.

Review is not automatically success.

### 5. Accept or revise

Use `ACCEPTANCE_LOG.md` to answer: **Did the plan work?** Record one of:

- `Accepted` — the result satisfies the acceptance criteria.
- `Accepted with limitations` — the result works within explicitly recorded limits.
- `Revise` — the result does not yet satisfy the plan; create the next corrective task.
- `Rejected` — the approach or result should not continue.
- `Blocked` — a named dependency prevents a decision or next action.
- `Deferred` — the project chooses to postpone the task.

Only an accepted result is a success for that task. An unsuccessful result is still useful progress when its findings and next action are recorded.

## Evidence chain

```text
BRAINSTORM_LOG.md
  → loose idea
PLAN_LOG.md
  → selected and documented task
CODING_WORKLOG.md
  → executed result
REVIEW_LOG.md
  → inspected result
ACCEPTANCE_LOG.md
  → did the plan work?
  → next task or corrective task
```

## Task rules

1. Keep brainstorming loose and easy to add to.
2. Expand an idea in `PLAN_LOG.md` before executing it.
3. Do not execute undocumented consequential work.
4. Record execution separately from review and acceptance.
5. Review the result against the actual plan, not against a silently changed goal.
6. Record success only in `ACCEPTANCE_LOG.md` after review.
7. If the plan did not work, record `Revise`, `Rejected`, `Blocked`, or `Deferred` and create the next action.
8. Do not silently expand an accepted task; plan the next task explicitly.
9. Preserve historical records and link each task across the logs.
10. Keep parent plans active until their own acceptance criteria are met.

## PL-0003 example

- **Brainstorm:** “We should review the architecture evaluation fixture.”
- **Plan:** PL-0003 expands that idea into review scope, evidence, and exit criteria.
- **Execute:** The fixture is inspected and the result is recorded in the worklog.
- **Review:** RV-0001 records findings and follow-up requirements.
- **Accept or revise:** AC-0001 records that the fixture review was accepted with limitations and that dataset creation is next.

The same process now applies to every application task.

## Status principle

When records disagree, use the most cautious status and record the missing evidence or correction. Never infer success from a plan, a document, or a commit alone.
