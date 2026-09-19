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
| **Proposed** | The work has been identified but execution has not started | A need, idea, milestone, or dependency was recorded | Do not expect repository outputs yet | Clarify scope, dependencies, owners, evidence, outputs, risks, and acceptance criteria; obtain approval where required |
| **Active** | The plan is currently being prepared or executed | Research, design, implementation, or review is underway | The work is authorised and current, but completion is not implied | Continue within scope and record actual results in the worklog |
| **Active / Partial execution** | Approved work produced useful outputs, but acceptance is incomplete | Some files, decisions, tests, or implementation exist; important criteria or reviews remain open | The outputs are real but incomplete, provisional, or not fully approved; do not treat them as final | Identify remaining criteria, decisions, reviewers, evidence, and dependencies; continue or request acceptance review |
| **Blocked** | Progress cannot responsibly continue because a required dependency is unavailable | Missing decision, access, source data, person, environment, approval, or technical prerequisite | Work may be planned or partly complete, but the blocker must be resolved before the next dependent step | Record the blocker, owner, impact, unblock condition, and next review point; do not silently work around it |
| **Deferred** | The work is intentionally postponed, not necessarily prevented | Priority, timing, resources, or sequencing changed | Do not spend effort on it unless the plan is reactivated | Record why it was deferred, what remains preserved, and the condition or decision that would reactivate it |
| **Completed** | Acceptance criteria are met and evidence is linked | Planned outputs exist, validation or review was performed, and remaining limitations are accepted or closed | The plan item is complete within its stated scope; this does not mean the whole product is complete | Preserve the evidence and create a new plan item for follow-up work or changed scope |

### Partial execution: how to read it carefully

**Partial** is not the same as failed, abandoned, or almost complete. It means the repository contains a meaningful result, but the result has a known gap between execution and acceptance.

A partial item should state:

- What was completed.
- What was not completed.
- Which acceptance criteria remain open.
- Whether the output is provisional, experimental, draft, or usable within a limited scope.
- Who or what is needed for acceptance.
- Whether dependent implementation may proceed or must wait.
- The next decision or review point.

For example, `PL-0003` is **Active / Partial execution** because its technology baseline and ADRs exist, but framework selection, BIM and geometry strategy, provider choices, performance targets, and stakeholder review remain unresolved. The documents can guide review, but they are not final production architecture.

A partial status should not be used to hide failed validation. Failed checks belong in the worklog and may require **Blocked** or a separate corrective plan item if they prevent progress.

### Blocked: how to read and manage it

Use **Blocked** only when a specific obstacle prevents the next responsible action. Name the blocker rather than using vague language such as “waiting” or “not ready.”

A useful blocked record includes:

- The exact dependency or decision that is missing.
- The person, team, system, or source responsible for resolving it.
- The work affected by the blocker.
- What can continue safely, if anything.
- The condition that will remove the blocker.
- A review date or next action.

Do not mark work Blocked merely because it is difficult, has open questions, or has partial output. Open questions may be compatible with **Active** or **Active / Partial execution**. Use Blocked when the unresolved matter prevents the planned next step.

### Deferred: how to distinguish it from blocked

Use **Deferred** when the project chooses not to pursue the work now. Use **Blocked** when the project wants to proceed but cannot.

| Question | If yes, use |
|---|---|
| Are we intentionally postponing this because of priority or sequencing? | **Deferred** |
| Would we continue now if the missing dependency or decision were available? | **Blocked** |
| Has some output been delivered but acceptance is not complete? | **Active / Partial execution** |

A deferred item should retain its scope, rationale, dependencies, and acceptance criteria so it can be resumed without reconstructing the original intent.

### Completed: the acceptance gate

Mark an item **Completed** only when the plan’s acceptance criteria are satisfied or explicitly closed through an approved decision. Check all of the following:

- The planned scope was executed, or an approved scope change explains the difference.
- Expected outputs exist at the required quality and locations.
- Required validation, testing, review, or approval was actually performed.
- Failed checks and limitations are resolved, accepted, or linked to follow-up work.
- The worklog records the actual outcome.
- The worklog ID and commit or pull-request evidence are linked from the plan item.
- No known blocker prevents the stated outcome.

Completed means **complete for this plan item and scope**. It does not mean the repository, product, or future work is finished.

## Authorising plan items

Every worklog entry must identify the exact plan item that authorised it:

```text
**Plan item:** `PL-0003 — Define technology and architecture decisions`
```

Use the exact ID and one primary authorising plan item. Do not invent IDs or use informal names. If work crosses scope boundaries, update the plan or create a new plan item first. Account and access implementation should use its own Group 1 plan item rather than only `PL-0003`.

## Current PL-0003 state

`PL-0003 — Define technology and architecture decisions` is **Active / Partial execution**. The provisional architecture baseline and ADRs exist and are recorded in `WL-0008`, but frontend/backend framework choices, spatial and BIM strategy, providers, scale and performance targets, and stakeholder review remain unresolved.

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
