# Progress Record Structure

Lifecycle records are stored as one file per task and stage to reduce merge conflicts and preserve append-only history.

```text
progress/
├── brainstorm/
│   └── BR-####.md
├── plan/
│   └── PL-####.md
├── execute/
│   └── WL-####.md
├── review/
│   └── RV-####.md
└── acceptance/
    └── AC-####.md
```

## Record chain

```text
BR-#### → PL-#### → WL-#### → RV-#### → AC-####
```

The existing root Markdown logs remain historical indexes and consolidated summaries during migration. New task records should use the stage directories. A task may begin from an existing follow-up without creating a new brainstorm record; in that case, link to the originating acceptance or plan record.

## Current migrated task

- Plan: `plan/PL-0007.md`
- Execute: `execute/WL-0020.md`
- Review: pending `review/RV-0004.md`
- Acceptance: pending `acceptance/AC-0004.md`

The authoritative lifecycle rules remain in `DEVELOPMENT_LIFECYCLE.md`.
