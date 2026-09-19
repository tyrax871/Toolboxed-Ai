# Toolboxed Review Log

This log records review of executed task results. It is separate from execution: a commit or worklog entry proves that work occurred, while this log records whether the evidence was inspected and what reviewers decided.

## How to use this log

- Create a review entry after the bounded task is executed.
- Identify the task, plan ID, worklog ID, evidence inspected, reviewers, findings, and decision.
- Record approval, requested correction, rejection, blocking issues, owners, and next review point.
- A review may recommend acceptance; it does not itself change the task to accepted unless acceptance is recorded in `ACCEPTANCE_LOG.md`.
- If review finds new scope, update `PLAN_LOG.md` before executing it.

## Review outcomes

`Approved for acceptance` | `Corrections required` | `Blocked` | `Rejected` | `Deferred` | `Insufficient evidence`

## Entry template

```text
RV-0001 — YYYY-MM-DD
Task:
Plan item:
Worklog entry:
Review status:
Reviewers and roles:
Evidence inspected:
Findings:
Required corrections:
Owners and due dates:
Decision:
Next review point:
Related acceptance entry:
```

## Current reviews

No formal review entries have been recorded yet. PL-0003 fixture review remains pending.
