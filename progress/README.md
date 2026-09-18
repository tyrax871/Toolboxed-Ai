# Progress Worklog

This folder contains the Toolboxed coding worklog.

## Rules for this folder

<!-- RULE: Add one dated entry to CODING_WORKLOG.md whenever code, configuration, tests, or project documentation changes. -->
<!-- RULE: Give every entry a unique sequential ID in the format WL-0001, WL-0002, WL-0003, and so on. -->
<!-- RULE: Include the change date in ISO format: YYYY-MM-DD. -->
<!-- RULE: Put the newest entry first and mark it green. -->
<!-- RULE: Do not delete or rewrite previous entries. Mark older entries grey so the project history remains visible. -->
<!-- RULE: Each entry must identify its ID, date, change type, affected paths, reason, validation, and next step or status. -->
<!-- RULE: Use clear repository-relative paths. -->
<!-- RULE: Record failed checks, blockers, and follow-up work honestly. -->
<!-- RULE: Keep implementation details concise and link to the relevant commit or pull request when available. -->

## Entry format

```text
WL-0001 — YYYY-MM-DD
```

IDs must increase by one for each new worklog entry. Dates must identify when the change was made or recorded.

## Colour convention

- **Green** — newest, current progress entry.
- **Grey** — previous progress entries retained for history.
- **Yellow** — blocked or awaiting a decision.
- **Red** — failed validation or a known issue requiring attention.

The colour formatting is implemented in `CODING_WORKLOG.md` with HTML spans so the visual status remains readable in GitHub-rendered Markdown where supported.
