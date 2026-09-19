# Progress Logs and Repository Guide

This folder is the authoritative development narrative for Toolboxed. It tells people and AI what we might want to do, what we selected, how we plan to do it, what we actually did, what we found, and whether the result worked.

## Progress logs

| File | Role | Process stage |
|---|---|---|
| `BRAINSTORM_LOG.md` | Loose ideas, questions, possibilities, and conversation-style notes | Brainstorm |
| `PLAN_LOG.md` | Selected ideas expanded into documented tasks | Plan |
| `CODING_WORKLOG.md` | Actual execution and repository evidence | Execute |
| `REVIEW_LOG.md` | Inspection of executed results and findings | Review |
| `ACCEPTANCE_LOG.md` | Whether the plan worked and what happens next | Accept or revise |
| `DEVELOPMENT_LIFECYCLE.md` | Process rules connecting the logs | Governance |

## Development process

```text
Brainstorm → Plan → Execute → Review → Accept or revise → Next task
```

Every task should follow this sequence. Brainstorming is loose. Planning makes the idea understandable and executable. Execution performs the documented plan. Review checks the result. Acceptance records whether the plan worked. If it did not work, the acceptance record creates the corrective or next task rather than pretending the task succeeded.

## What each log does

### `BRAINSTORM_LOG.md` — loose ideas

Use this like a simple chat, scratchpad, or list. Add anything we might want, a problem we notice, a question, a possible feature, or a technical possibility. Do not force ideas into full plans here. Nothing in this log authorises work.

### `PLAN_LOG.md` — explored and documented ideas

Move an idea here when we want to explore it seriously. Expand it into an objective, scope, exclusions, approach, dependencies, evidence, risks, exit condition, and acceptance criteria. This is where the idea becomes a task that can be executed.

### `CODING_WORKLOG.md` — executed work

Record what actually happened while carrying out the plan. Include changed files, implementation details, validation performed, unperformed checks, limitations, blockers, and exact repository evidence. This log does not decide whether the plan worked.

### `REVIEW_LOG.md` — reviewed results

Record what was inspected, by whom or by which review responsibility, what the evidence showed, what failed, and what corrections are required. Review prepares the result for acceptance; it is not acceptance by itself.

### `ACCEPTANCE_LOG.md` — outcome and next task

Record whether the plan worked: accepted, accepted with limitations, revise, rejected, blocked, or deferred. If the plan did not work, create or identify the next corrective task. If it worked, identify the next planned task. Only an accepted result is a task success.

## Workflow

1. Add a loose idea to `BRAINSTORM_LOG.md`.
2. Select an idea and expand it into a documented task in `PLAN_LOG.md`.
3. Execute only the documented task.
4. Record actual work in `CODING_WORKLOG.md`.
5. Review the result in `REVIEW_LOG.md`.
6. Record whether the plan worked in `ACCEPTANCE_LOG.md`.
7. Plan the next task or corrective task before continuing.

## Evidence chain

```text
BRAINSTORM_LOG.md
  → idea
PLAN_LOG.md
  → documented task
CODING_WORKLOG.md
  → execution
REVIEW_LOG.md
  → review
ACCEPTANCE_LOG.md
  → success or correction
  → next task
```

## Current PL-0003 state

`PL-0003 — Define technology and architecture decisions` remains **Active / Partial execution**. The fixture review was accepted with limitations. The next task is to create and review the versioned evaluation dataset. Dataset creation, measured evaluations, evidence-backed ADR decisions, and architecture acceptance remain pending.

## Rules

- Keep brainstorm ideas loose; do not require a plan template there.
- Do not infer execution from a plan or documentation.
- Do not infer success from execution or review alone.
- Record failed, partial, blocked, deferred, rejected, and corrective outcomes honestly.
- Preserve historical entries and link each task across the logs.
- Keep parent plans active until their own acceptance criteria are met.
- Use the most cautious status when records disagree.

For the full process rules, see `progress/DEVELOPMENT_LIFECYCLE.md`.
