# Progress Logs and Repository Guide

This folder contains the planning and execution records for Toolboxed, a collaborative, architecture-first BIM platform whose central building model is the source of truth.

## Where to look first

| Path | Purpose |
|---|---|
| `README.md` | Repository purpose and top-level folders |
| `progress/PLAN_LOG.md` | Intended work: what the project wants to do |
| `progress/CODING_WORKLOG.md` | Actual work: what changed in the repository |
| `docs/product/` | Product goals and workflows |
| `docs/architecture/` | BIM architecture, technology decisions, and ADRs |
| `design/` | Wireframes and design-system resources |
| `app/` | Application entry points |
| `packages/` | Shared packages |
| `services/` | Backend and background services |
| `infrastructure/` | Database and deployment configuration |
| `tests/` | Automated tests |

## Plan log: what we want to do

`progress/PLAN_LOG.md` records intended work before execution. Each plan item defines its objective, reason, dependencies, people, data or evidence needed, outputs, risks, open questions, and acceptance criteria.

A plan item provides scope and authorisation; it is not proof that work happened. Plan items use sequential IDs such as `PL-0001`, `PL-0002`, and `PL-0003`.

## Worklog: what we have done

`progress/CODING_WORKLOG.md` records actual repository changes, including documentation, code, configuration, tests, planning updates, and repository-structure changes.

Each entry records what actually happened: objective, context, decisions, affected paths, implementation details, validation, limitations, blockers, status, next steps, and commit or pull-request evidence. Entries use sequential IDs such as `WL-0001`, `WL-0007`, and `WL-0008`. The newest entry is first; previous entries remain to preserve history.

## Mandatory plan-first workflow

1. Identify the requested repository work.
2. Add or update its scope in `PLAN_LOG.md`.
3. Record dependencies, people, data, outputs, risks, and acceptance criteria.
4. Obtain required approval for consequential work.
5. Execute only the approved scope.
6. Record actual changes in `CODING_WORKLOG.md`.
7. Add the authorising `PL-` ID to the worklog entry.
8. Link the `WL-` ID and commit or pull request to the plan item.
9. Change plan status only when acceptance criteria and evidence justify it.

If work expands beyond the approved scope, update the plan before continuing. Failed, partial, blocked, cancelled, and reverted work must be recorded honestly and cannot be marked Completed.

## Large-task execution sequence

Large tasks should be divided into ordered increments so the team can make useful progress, validate each result, and continue until the parent objective succeeds. The parent plan item remains the source of the overall objective, scope, and final acceptance criteria.

Use this sequence for complex work:

| Step | Increment | Required result before moving on |
|---|---|---|
| 1 | **Frame** | Objective, scope, owner, dependencies, risks, and success criteria are recorded in the plan log |
| 2 | **Discover** | Relevant repository files, requirements, constraints, assumptions, and evidence are inspected |
| 3 | **Design** | Options, decisions, contracts, interfaces, and acceptance checks are documented |
| 4 | **Build** | The approved increment is implemented within its stated scope |
| 5 | **Validate** | Relevant tests, checks, review, and evidence are performed and recorded honestly |
| 6 | **Review** | Required stakeholders inspect the result and resolve open decisions |
| 7 | **Accept or continue** | The increment is accepted, corrected, blocked, deferred, or followed by the next increment |

### Rules for incremental execution

- Give each major increment a clear name, scope, owner, and exit condition.
- Record the increment in the parent plan item before execution begins when it changes scope or risk.
- Use one worklog entry for each executed increment or clearly bounded batch.
- Link each increment to its commit, pull request, tests, and review evidence.
- Do not call an increment successful merely because it produced files; its exit condition must be met.
- Keep the parent plan Active or Active / Partial until its final acceptance criteria are met.
- If an increment fails, record the failure and decide whether to correct, retry, split, block, defer, or re-plan it.
- If an increment reveals new scope, update the plan before executing that new scope.
- At any point, a reader should be able to identify the current increment and the next required action.

### Increment status pattern

```text
Parent plan: PL-0003 — Define technology and architecture decisions
    ↓
Increment: Review framework and runtime options
    ↓
Worklog: WL-xxxx — actual research and decision record
    ↓
Evidence: commits, ADR updates, tests, and stakeholder review
    ↓
Outcome: accepted / correction required / blocked / deferred
```

This sequence supports partial progress without confusing intermediate results with final success.

## How records connect

```text
PL-0003 — approved intended scope
    ↓
WL-0008 — actual repository work
    ↓
Commit(s) — exact GitHub evidence
```

- The plan log answers: **What did we intend to do, and why?**
- The worklog answers: **What did we actually change?**
- The commit or pull request answers: **Where is the exact evidence?**
- The status answers: **Is the work fully accepted?**

A plan item cannot be marked Completed merely because files were created.

## How to interpret plan status

A status describes the relationship between intended scope, actual execution, dependencies, and acceptance evidence. It is not a general opinion about whether the work is valuable or promising.

| Status | Meaning | What may have happened | What the reader should conclude | What happens next |
|---|---|---|---|---|
| **Proposed** | Work identified but execution has not started | Need, idea, milestone, or dependency recorded | Do not expect repository outputs yet | Clarify scope and obtain approval |
| **Active** | Plan is being prepared or executed | Research, design, implementation, or review underway | Work is current, but completion is not implied | Continue within scope and record actual results |
| **Active / Partial execution** | Useful outputs exist, but acceptance is incomplete | Some files, decisions, tests, or implementation exist; criteria or reviews remain open | Outputs are real but incomplete or provisional | Identify remaining criteria and continue or request review |
| **Blocked** | A specific dependency prevents the next responsible action | Missing decision, access, source, person, environment, approval, or prerequisite | Work may be partly complete, but the blocker must be resolved | Record blocker, owner, impact, unblock condition, and next review |
| **Deferred** | Project intentionally postpones the work | Priority, timing, resources, or sequencing changed | Do not continue until reactivated | Record rationale and reactivation condition |
| **Completed** | Acceptance criteria met and evidence linked | Outputs exist, validation/review performed, limitations resolved or accepted | Complete for this plan scope | Preserve evidence and create follow-up plans as needed |

### Partial execution

Partial is not failed, abandoned, or almost complete. It means a meaningful result exists with a known gap between execution and acceptance. Record what is complete, what remains, open criteria, provisional limits, required reviewers, dependent-work constraints, and the next decision point.

### Blocked

Use Blocked only when a named obstacle prevents the next responsible action. Open questions alone do not make work blocked. Record the dependency, responsible owner, affected work, safe work that can continue, unblock condition, and review point.

### Deferred

Use Deferred when the project chooses not to pursue the work now. Use Blocked when the project wants to proceed but cannot. Preserve the original scope, rationale, dependencies, and acceptance criteria so the item can be resumed.

### Completed

Mark Completed only when scope is executed or formally changed, expected outputs exist, required validation or review occurred, failures and limitations are resolved or accepted, worklog and evidence are linked, and no known blocker prevents the stated outcome. Completed means complete for that plan item—not for the entire product.

## Authorising plan items

Every worklog entry must identify the exact plan item that authorised it:

```text
**Plan item:** `PL-0003 — Define technology and architecture decisions`
```

Use the exact ID and one primary authorising plan item. If work crosses scope boundaries, update the plan or create a new plan item first.

## Current PL-0003 state

`PL-0003 — Define technology and architecture decisions` is **Active / Partial execution**. The provisional architecture baseline and ADRs exist and are recorded in `WL-0008`, but framework choices, spatial and BIM strategy, providers, scale and performance targets, and stakeholder review remain unresolved.

The documents may guide review and further planning, but they are not final production architecture. Do not mark PL-0003 Completed until the open choices are resolved and acceptance evidence is recorded.

## How to review a change

1. Read the relevant plan item.
2. Read its authorising worklog entry.
3. Open the linked commit or pull request.
4. Inspect changed files and validation evidence.
5. Check current status, risks, and remaining work.

## History rules

- Do not present intended work as completed work.
- Do not claim tests, reviews, deployments, or approvals that did not happen.
- Do not delete older worklog entries.
- Do not mark partial work Completed.
- Preserve the original authorising plan item.
- Record failed checks and unperformed validation.
- Link plan items, worklog entries, commits, and pull requests whenever available.

## Templates

### Plan item

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

### Worklog entry

```text
WL-0001 — YYYY-MM-DD
Plan item: PL-0001 — Plan item title
Increment:
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

- **Green** — newest current worklog entry.
- **Grey** — previous retained entries.
- **Yellow** — blocked or awaiting a decision.
- **Red** — failed validation or known issue.
