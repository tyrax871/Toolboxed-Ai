# Progress Worklog

This folder contains the Toolboxed coding worklog.

## Rules for this folder

<!-- RULE: Add one dated entry to CODING_WORKLOG.md whenever code, configuration, tests, documentation, planning, or repository structure changes. -->
<!-- RULE: Give every entry a unique sequential ID in the format WL-0001, WL-0002, WL-0003, and so on. -->
<!-- RULE: Include the change date in ISO format: YYYY-MM-DD. -->
<!-- RULE: Put the newest entry first and mark it green. -->
<!-- RULE: Do not delete or rewrite previous entries. Mark older entries grey so the project history remains visible. -->
<!-- RULE: Every entry must describe everything completed in that work item, not only the headline result. -->
<!-- RULE: Record the objective, context, decisions, actions taken, files and folders affected, important implementation details, validation performed, limitations, blockers, status, and next steps. -->
<!-- RULE: Use clear repository-relative paths and identify created, updated, deleted, or unchanged files where relevant. -->
<!-- RULE: Record failed checks, partial results, assumptions, and follow-up work honestly. -->
<!-- RULE: Do not claim a test, review, validation, deployment, or approval that was not actually performed. -->
<!-- RULE: Keep entries descriptive and chronological while avoiding irrelevant commentary. -->
<!-- RULE: Link the relevant commit or pull request when available. -->

## Required entry format

```text
WL-0001 — YYYY-MM-DD

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

IDs must increase by one for each new worklog entry. Dates must identify when the change was made or recorded. Every entry must be sufficiently detailed for a user or developer to understand what happened without relying on the conversation history.

## Colour convention

- **Green** — newest, current progress entry.
- **Grey** — previous progress entries retained for history.
- **Yellow** — blocked or awaiting a decision.
- **Red** — failed validation or a known issue requiring attention.

The colour formatting is implemented in `CODING_WORKLOG.md` with HTML spans so the visual status remains readable in GitHub-rendered Markdown where supported.
