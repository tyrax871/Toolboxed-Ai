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

Statuses:

- **Proposed** — identified but not started.
- **Active** — currently planned or being prepared.
- **Active / Partial execution** — approved work produced partial outputs, but acceptance is incomplete.
- **Blocked** — waiting for a dependency, decision, resource, or source.
- **Deferred** — intentionally postponed.
- **Completed** — acceptance criteria are met and execution evidence is linked.

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
